# git 基本操作
2019-06-04

[git官网地址](https://git-scm.com/)

## 常用命令
### git 配置
```
// 设置用户名
$ git config [--global] user.name 'name'   
// 设置用户邮箱   
$ git config [--global] user.email 'email' 
```
### 操作命令
```
$ git -help -g                              // 展示帮助信息
$ git init                                  // 初始化
$ git clone <url>                           // 拉取远程仓库代码
$ git pull                                  // 获取远程最新代码
$ git add <. -A -u>                         // 将本地修改提交到暂存区
$ git commit -m 'commit msg'                // 将暂存区修改提交到本地版本库
$ git checkout <filepat filename>           // 撤销工作区文件修改，
$ git reset --hard <commitid>               // 将代码会退到指定commitid版本，删除修改
$ git reset --soft <commitid>               // 将代码会退到指定commitid，保留修改
$ git log [--name-only]                     // 查看commit信息
$ git show <commitid>
$ git status                                // 查看git状态
$ git tag <tagname> [commitid]              // 执行commitid添加标题
$ git push [-u] [origin]                    // 将本地版本库的修改提交到远程版本库
$ git checkout -b 'branch name'             // 新建本地分支
$ git branch -D 'branch name'               // 删除本地分支
$ git push origin --delete 'branch'         // 删除远程分支

```
## 文件状态
```
A: 你本地新增的文件（服务器上没有）.
C: 文件的一个新拷贝.
D: 你本地删除的文件（服务器上还在）.
M: 文件的内容或者mode被修改了.
R: 文件名被修改了。
T: 文件的类型被修改了。
U: 文件没有被合并(你需要完成合并才能进行提交)。
X: 未知状态(很可能是遇到git的bug了，你可以向git提交bug report)。
在man git diff-files中可以查到这些标志的说明。
这些状态标志在git的源代码的diff.h文件中被定义。
```
## 修改处理
```
$ git fetch --all && git reset --hard origin/master     // 抛弃本地所有的修改，回到远程仓库的状态 master 分支。
$ git update-ref --d HEAD                               // 重设第一个 commit
$ git diff <commit-if><commit-id>/[--cached]/ [HEAD]    // 展示工作区和暂存区的不同
$ git reset --soft <commit-id>/ HEAD                    // 代码回退到指定commit或远程，不删除本地修改
$ git reset <file-name>                                 // 将暂存区的文件放到工作区
$ git stash [save msg]                                  // 将本地修改放到暂存区[添加说明]
$ git stash -u(untracked)                               // 保存包括新建的文件，不用将文件添加的暂存区
$ git stash list                                        // 展示所有stashes
$ git stash list --date=local                           // 展示stash 列表时间
$ git stash apply <stash@{n}>                           // 回到指定的stash状态
$ git stash drop <stash@{n}>                            // 删除指定的stash状态
$ git stash pop                                         // 回到最新的stash状态，并删除这个stash
$ git stash clear                                       // 清除所有stash
$ git checkout <stash@{n}> -- <file-path>               // 从stash中获取某个文件的修改
$ git checkout .                                        // 放弃所有修改
```
## 仓库修改
```
$ git branch -b <branch name>                           // 新建本地分支
$ git branch                                            // 展示当前分支名
$ git branch -r                                         // 列出远程仓库分支
$ git branch -a                                         // 所有分支
$ git branch -vv                                        // 展示本地分支关联远程仓库情况
$ git branch -delete <branch name>                      // 删除本地分支
$ git branch -m <new branh name>                        // 当前分支重新命名
$ git push --delete origin <branch name>                // 删除远程分支
$ git checkout <branch name>                            // 切分支，如果这个分支是远程分支，本地没有，将会在本地新建分支，并关联远程分支
$ git checkout -                                        // 快速切到上一分支
$ git branch -u origin/branchname                       // 关联远程分支
$ git remote -v                                         // 查看远程仓库地址和权限
$ git remote add origin <remote-url>                    // 添加仓库地址
$ git remote set-url origin <new-url>                   // 修改远程仓库地址
$ git whatchanged --since='2 week ago'                  // 查看两周内的修改
$ git pull                                              // 拉取最新代码
$ git push                                              // 提交
$ git push -u origin <branch name>                      // 关联远程分支并提交
```
## git commit 提交
```
$ git commit -m <msg>                                   // 将暂存区代码提交到本地仓库
$ git log                                               // 查看commit信息
$ git log --pretty=oneline --graph --decorate --all     // 展示简化的commit信息
$ git bundle create <file> <branch name>                // 将分支导出成一个文件
$ git log --all --grep='<given-text>'                   // 通过grep查找commit信息
```

**如有总结不当之处，请指正， 谢谢！**