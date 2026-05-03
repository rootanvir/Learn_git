# Git Cheat Sheet

---

## Setup & Config

| Command | Description |
|---------|-------------|
| `git config --global user.name "Name"` | Set global username |
| `git config --global user.email "e@x.com"` | Set global email |
| `git config --global core.editor vim` | Set default editor |
| `git config --global init.defaultBranch main` | Set default branch name |
| `git config --list` | Show all config values |
| `git config --global alias.st status` | Create alias: `git st` → `git status` |

---

## Init & Clone

| Command | Description |
|---------|-------------|
| `git init` | Initialize repo in current directory |
| `git init <dir>` | Initialize repo in new directory |
| `git clone <url>` | Clone a remote repo |
| `git clone <url> <dir>` | Clone into specific folder |
| `git clone --depth 1 <url>` | Shallow clone (latest snapshot only) |
| `git clone -b <branch> <url>` | Clone a specific branch |

---

## Stage & Commit

| Command | Description |
|---------|-------------|
| `git status` | Show working tree status |
| `git status -s` | Compact status output |
| `git add <file>` | Stage a specific file |
| `git add .` | Stage all changes |
| `git add -p` | Interactively stage hunks (patch mode) |
| `git add -u` | Stage modifications + deletions (not new files) |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes vs last commit |
| `git diff <b1>..<b2>` | Diff between two branches |
| `git commit -m "msg"` | Commit with inline message |
| `git commit -am "msg"` | Stage tracked files and commit |
| `git commit --amend` | Amend last commit (message or content) |
| `git commit --amend --no-edit` | Amend without changing message |
| `git rm <file>` | Remove file from repo and disk |
| `git rm --cached <file>` | Remove from index only (keep on disk) |
| `git mv <old> <new>` | Rename or move a file |

---

## Undo

| Command | Description |
|---------|-------------|
| `git restore <file>` | Discard unstaged changes in file |
| `git restore --staged <file>` | Unstage a file (keep changes) |
| `git restore --source=HEAD~1 <file>` | Restore file from a specific commit |
| `git revert <commit>` | New commit that undoes a commit (safe) |
| `git revert HEAD` | Revert last commit |
| `git reset --soft HEAD~1` | Undo commit; keep changes staged |
| `git reset --mixed HEAD~1` | Undo commit; keep changes unstaged |
| `git reset --hard HEAD~1` | Undo commit; discard all changes ⚠️ |
| `git reset --hard origin/main` | Reset to match remote ⚠️ |
| `git clean -fd` | Remove untracked files + dirs ⚠️ |
| `git clean -n` | Dry run: preview what would be removed |

---

## Branching

| Command | Description |
|---------|-------------|
| `git branch` | List local branches |
| `git branch -a` | List all branches (local + remote) |
| `git branch -v` | List with last commit info |
| `git branch <name>` | Create new branch |
| `git branch -d <name>` | Delete branch (safe, merged only) |
| `git branch -D <name>` | Force delete branch ⚠️ |
| `git branch -m <old> <new>` | Rename a branch |
| `git switch <branch>` | Switch to branch |
| `git switch -c <branch>` | Create and switch to new branch |
| `git switch -c <b> <remote/b>` | Create local branch tracking a remote |

---

## Merging

| Command | Description |
|---------|-------------|
| `git merge <branch>` | Merge branch into current branch |
| `git merge --no-ff <branch>` | Merge with a merge commit (no fast-forward) |
| `git merge --squash <branch>` | Squash branch commits into one staged change |
| `git merge --abort` | Abort an in-progress merge |

---

## Rebasing

| Command | Description |
|---------|-------------|
| `git rebase <branch>` | Rebase current branch onto `<branch>` |
| `git rebase -i HEAD~3` | Interactive rebase: last 3 commits |
| `git rebase --onto <new> <old> <b>` | Rebase onto a different base |
| `git rebase --abort` | Abort rebase |
| `git rebase --continue` | Continue after resolving conflict |
| `git rebase --skip` | Skip current conflicting commit |

### Interactive Rebase Commands

| Command | Description |
|---------|-------------|
| `pick` | Keep commit as-is |
| `reword` | Keep commit, edit message |
| `edit` | Pause to amend commit |
| `squash` | Meld into previous commit |
| `fixup` | Like squash, discard this message |
| `drop` | Remove commit entirely |

---

## Remotes

| Command | Description |
|---------|-------------|
| `git remote -v` | List remotes |
| `git remote add <name> <url>` | Add a remote |
| `git remote remove <name>` | Remove a remote |
| `git remote rename <old> <new>` | Rename a remote |
| `git remote set-url <name> <url>` | Change remote URL |
| `git fetch` | Fetch all remotes |
| `git fetch --prune` | Fetch + remove stale remote refs |
| `git pull` | Fetch + merge current branch |
| `git pull --rebase` | Fetch + rebase instead of merge |
| `git pull origin <branch>` | Pull a specific branch |
| `git push <remote> <branch>` | Push branch to remote |
| `git push -u origin <branch>` | Push + set upstream tracking |
| `git push --force-with-lease` | Safe force push (checks remote state) |
| `git push --force` | Force push ⚠️ (overwrites remote) |
| `git push origin --delete <b>` | Delete a remote branch |
| `git push --tags` | Push all tags |

---

## Stashing

| Command | Description |
|---------|-------------|
| `git stash` | Stash current changes |
| `git stash push -m "msg"` | Stash with a description |
| `git stash -u` | Stash including untracked files |
| `git stash list` | List all stashes |
| `git stash show stash@{0}` | Show contents of a stash |
| `git stash pop` | Apply latest stash + remove it |
| `git stash apply stash@{1}` | Apply specific stash (keep in list) |
| `git stash drop stash@{0}` | Delete a stash |
| `git stash clear` | Delete all stashes ⚠️ |
| `git stash branch <branch>` | Create branch from stash |

---

## Tagging

| Command | Description |
|---------|-------------|
| `git tag` | List all tags |
| `git tag <name>` | Create lightweight tag at HEAD |
| `git tag -a <name> -m "msg"` | Create annotated tag |
| `git tag -a <name> <commit>` | Tag a specific commit |
| `git tag -d <name>` | Delete local tag |
| `git push origin <tag>` | Push a specific tag |
| `git push origin --tags` | Push all tags |
| `git push origin --delete <tag>` | Delete remote tag |
| `git show <tag>` | Show tag metadata + commit |

---

## Log & History

| Command | Description |
|---------|-------------|
| `git log` | Full commit log |
| `git log --oneline` | One line per commit |
| `git log --oneline --graph --all` | Visual branch graph |
| `git log -n 5` | Last 5 commits |
| `git log --author="Name"` | Filter by author |
| `git log --since="2 weeks ago"` | Filter by date |
| `git log --grep="fix"` | Filter by commit message |
| `git log -- <file>` | Log for a specific file |
| `git log <b1>..<b2>` | Commits in b2 not in b1 |
| `git log -p` | Show patches (diffs) per commit |
| `git show <commit>` | Show commit details + diff |
| `git show HEAD:src/main.cpp` | Show file as it was at HEAD |
| `git blame <file>` | Show who changed each line |
| `git blame -L 10,20 <file>` | Blame specific line range |
| `git shortlog -sn` | Commit count per author |

---

## Searching

| Command | Description |
|---------|-------------|
| `git grep "pattern"` | Search working tree for pattern |
| `git grep -n "pattern"` | Search with line numbers |
| `git grep "pattern" <commit>` | Search a specific commit |
| `git log -S "string"` | Find commits that added/removed a string |
| `git log -G "regex"` | Find commits where diff matches regex |
| `git bisect start` | Begin binary search for a bug |
| `git bisect bad` | Mark current commit as bad |
| `git bisect good <commit>` | Mark known-good commit |
| `git bisect reset` | End bisect session |

---

## Patch & Cherry-pick

| Command | Description |
|---------|-------------|
| `git diff > changes.patch` | Export diff as patch file |
| `git apply changes.patch` | Apply a patch file |
| `git apply --check changes.patch` | Dry run: check if patch applies cleanly |
| `git format-patch HEAD~3` | Create .patch files for last 3 commits |
| `git am *.patch` | Apply a series of patch files |
| `git cherry-pick <commit>` | Apply a single commit to current branch |
| `git cherry-pick <c1>..<c2>` | Apply a range of commits |
| `git cherry-pick --no-commit <c>` | Apply changes without committing |
| `git cherry-pick --abort` | Abort cherry-pick |

---

## Reflog

| Command | Description |
|---------|-------------|
| `git reflog` | Show all HEAD movements (safety net) |
| `git reflog show <branch>` | Show movements for a branch |
| `git checkout HEAD@{2}` | Go to a previous HEAD position |
| `git reset --hard HEAD@{3}` | Restore to a reflog entry ⚠️ |

---

## Submodules & Worktrees

| Command | Description |
|---------|-------------|
| `git submodule add <url> <path>` | Add a submodule |
| `git submodule init` | Initialize submodules |
| `git submodule update` | Fetch submodule contents |
| `git submodule update --init --recursive` | Init + update all nested submodules |
| `git clone --recurse-submodules <url>` | Clone with all submodules |
| `git worktree add <path> <branch>` | Check out branch in new directory |
| `git worktree list` | List all worktrees |
| `git worktree remove <path>` | Remove a worktree |

---

## Plumbing (Advanced)

| Command | Description |
|---------|-------------|
| `git cat-file -p <hash>` | Pretty-print object contents |
| `git cat-file -t <hash>` | Show object type (blob/tree/commit/tag) |
| `git ls-tree HEAD` | List tree contents of current commit |
| `git hash-object <file>` | Compute SHA-1 hash of a file |
| `git rev-parse HEAD` | Resolve reference to a SHA |
| `git rev-parse --short HEAD` | Short SHA of HEAD |
| `git rev-list --count HEAD` | Total commit count |

---

## Key Symbols Reference

| Symbol | Meaning |
|--------|---------|
| `HEAD` | Current commit pointer |
| `HEAD~1` | One commit before HEAD |
| `HEAD^` | First parent of HEAD (same as `HEAD~1`) |
| `HEAD~n` | n commits before HEAD |
| `@{upstream}` | Upstream tracking branch |
| `ORIG_HEAD` | Previous HEAD (before merge/rebase/reset) |
| `FETCH_HEAD` | Last fetched ref |
| `MERGE_HEAD` | Commit being merged |
| `..` | Commits reachable from right, not left |
| `...` | Commits reachable from either, not both |

---

