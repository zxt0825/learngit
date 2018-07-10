pwd							address now
mkdir							mkdir learngit
cd
ls -a		

git add							add sth to working dir
git commit -m  "...."					to commit the changes
	   -am "...."					add and commit
git reset HEAD readme.txt     				to unstage   (HEAD mean the version now)
git checkout -- readme.txt				to discard changes

*git status						to look the status of git
git init						to init the dir to be a git repository
git diff readme.txt					to see which part is different
*git log (--pretty=oneline)				the log is the version of now and before
	git log --graph --pretty=oneline --abbrev-commit
git reflog						the log of changing the version
	
git reset --hard HEAD^					(HEAD means the version now ,and ^ means last version.
git reset --hard 3b1295(commit id)				can back to the version you choose

git branch (-vv)					see:"master (151b81e version 1.1)"

*git remote add origin git@github.com....
							add remote repository
*git remote remove origin				remove remote rep

*git push -u origin master				first time to push

*git checkout -b dev					create a branch and checkout to dev
	git branch dev
	+git checkout dev
	
git merge						merge to update
git merge --no-ff -m "merge with no-ff"
git merge --no-ff -m "merged bug fix 101" issue-101

*git branch						checkout the branch
git branch -d dev					delete a branch

git stash 
git stash pop						back to the status when you leave and delete the log in stash
	git stash apply
	+git stash drop

http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html


更新远程跟踪分支
$ git fetch origin
Shell
上述命令从远程refs/heads/命名空间复制所有分支，并将它们存储到本地的refs/remotes/ origin/命名空间中，除非使用分支.<name>.fetch选项来指定非默认的refspec。

在远程分支上窥视，无需在本地存储库中配置远程
$ git fetch git://git.kernel.org/pub/scm/git/git.git maint
$ git log FETCH_HEAD
Shell
第一个命令从 git://git.kernel.org/pub/scm/git/git.git 从存储库中获取maint分支，第二个命令使用FETCH_HEAD来检查具有git-log的分支。

git branch -r
origin/master
$ git branch -a
* master
  remotes/origin/master
上面命令表示，本地主机的当前分支是master，远程分支是origin/master。
取回远程主机的更新以后，可以在它的基础上，使用git checkout命令创建一个新的分支。
$ git checkout -b newBrach origin/master
上面命令表示，在origin/master的基础上，创建一个新分支:newBrach。

$ git pull <远程主机名> <远程分支名>:<本地分支名>
比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样 -
$ git pull origin next:master
如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：
$ git pull origin next
上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再执行git merge。
$ git fetch origin
$ git merge origin/next

