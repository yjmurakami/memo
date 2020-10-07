## 初期設定

### 基本設定

```bash
git config --global user.name "First-name Family-name"
git config --global user.email "username@example.com"
git config --global core.editor "vi"
```

### diff / merge ツール

~/.gitconfig ファイルに下記を追記

```
[diff]
    tool = WinMerge

[difftool]
    prompt = false

[difftool "WinMerge"]
    path = C:/Program Files/WinMerge/WinMergeU.exe
    cmd = \"C:/Program Files/WinMerge/WinMergeU.exe\" -e -x -u -wl -wr \"$LOCAL\" \"$REMOTE\"

[merge]
    tool = WinMerge

[mergetool]
    prompt = false
    keepBackup = false

[mergetool "WinMerge"]
    path = C:/Program Files/WinMerge/WinMergeU.exe
    cmd = \"C:/Program Files/WinMerge/WinMergeU.exe\" \"$MERGED\"

[alias]
    windiff = difftool -d -t WinMerge
    winmerge = mergetool -t WinMerge
```

## コマンド

### 設定の確認
```bash
git config --global --list
```

### リポジトリ作成
```bash
git init [repository]
git init
```

### クローン
```bash
git clone [URL]
```

### 状態確認
```bash
git status
```

### Working Directory → Staging Area
```bash
git add [file]
git add .
```

### Staging Area → Repository
```bash
git commit -m "[comment]"
```

### Repository → Remote
```bash
git push [remote] [branch]
```

### Remote → Local
```bash
git pull [remote] [branch]
```

### ファイル名変更
```bash
git mv [current-name] [new-name]
```

### ファイル削除
```bash
git rm [file]
```

### ログ
```bash
git log --oneline --graph
git log [file]
```

### コミットの詳細
```bash
git show [commit-id]
```

### Working Directory vs Staging Area
```bash
git difftool
```

### Working Directory vs HEAD
```bash
git difftool HEAD
```

### Staging Area vs HEAD
```bash
git difftool --staged HEAD
```

### 指定のファイルを比較
```bash
git difftool -- [file]
```

### コミットの比較
```bash
# コミットIDは、HEAD、HEAD^ などでも可能
git difftool [commit-id1] [commit-id2]
```

### ブランチの確認
```bash
git branch -a
```

### ブランチの作成
```bash
git branch [branch]
```

### ブランチの変更
```bash
git checkout [branch]
```

### ブランチ名の変更
```bash
git branch -m [current-name] [new-name]
```

### ブランチの削除
```bash
git branch -d [branch]
```

### ブランチの差分確認
```bash
git difftool [branch1] [branch2]
```

### マージ Fast-forward
```bash
git merge [branch]
```

### マージ
```bash
git merge [branch] --no-ff
```

### コンフリクトの解消
```bash
git mergetool
```

### スタッシュ
```bash
git stash
git stash apply
git stash list
git stash drop

# Untracked file もスタッシュする場合
git stash -u

# apply drop を同時にする場合
git stash pop

# 複数スタッシュする場合
git stash save "[comment]"

# 複数スタッシュがある場合
git stash show stash@{0}
git stash apply stash@{0}
git stash drop stash@{0}

git stash branch [branch]
```

### トラック中のファイルを確認
```bash
git ls-files
```

## .gitignore

```
# 特定のファイル
MyFile.txt

# ファイルパターン
*.txt

# フォルダ
my-folder/
```