# GIT的菜鸟教程笔记和使用指南
本项目为个人笔记，篇幅大概五分钟

# git笔记
基本概念
* 工作区:能在电脑看到的目录
* 暂存区：存放在.git下的index，也叫索引 add
* 版本库：就是.git（包含暂存区） commit
* （git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。 
* git reset HEAD 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响
* git rm --cached <file> 命令时，会直接从暂存区删除文件，工作区则不做出改变
* git checkout .或者git checkout --<file>会用index区全部或指定文件替换工作区的文件。很危险
* git checkout HEAD .或者git checkout HEAD <file>,HEAD指向的master分支中的全部或者部分文件替换index区和工作区中的文件，也危险

### 先 创建仓库
* 基本操作
  
        git init //初始化和使用当前目录作为git仓库
        //生成.git
        git init 目录名  //指定目录作为Git仓库,相应的也会在目录下生成.git
        //如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交
        git add *.c   //目录下以 .c 结尾的文件提交到仓库中
        git add README
        git commit -m '提交说明'
* git clone 可以从现有git仓库中拷贝项目
        
        git clone <repo>  //repo：git仓库
        git clone <repo> <directory> //directory:本地目录

        //比如要克隆Git 代码仓库 Grit
        git clone git://github.com/..../grit.git +（指定新项目名字，可省略）
        //执行完后会在当前目录下创建一个grit的目录，包 含一个保存版本目录的.git
### 配置 
        git config
        git config -e    # 针对当前仓库
        git config -e --global   # 针对系统上所有仓库
        如git config --global user.name "runoob"
### 基本操作
常用6个命令：clone，push，add，commit，checkout，pull 

        git add .//添加文件到index区 
        git clone // 	拷贝一份远程仓库，也就是下载一个项目

        //提交与修改
        git diff --cached filename //有显示本地区与仓库对应文件的不同，不写cached则是index区
        git commit 	提交暂存区到本地仓库。
        git reset 	回退版本。
        git rm 	删除工作区文件。
        git mv 	移动或重命名工作区文件。

        //远程操作
        git remote 	远程仓库操作
        git fetch 	从远程获取代码库
        git pull 	下载远程代码并合并
        git push 	上传远程代码并合并
        git rm -r --cached test/a.txt  删除本地仓库某个文件 不写a.txt则删除全部，--cached表示不删本地工作区

        //分支操作
        git branch 分支名 //不填分支名则是列出分支列表
        git branch -d (branchname) /删除分支
        git checkout 分支名 //切换到分支名
        git merge 分支名//合并分支，但合并后要删除分支名

        //合并冲突
        两个分支合并后，同名文件会存在内容叠加，需要自己vim修改
        //修改完后要用git add告诉 Git 文件冲突已经解决
        $ git status -s
        UU runoob.php
        $ git add runoob.php
        $ git status -s
        M  runoob.php
        $ git commit
        [master 88afe0e] Merge branch 'change_site'
## 查看提交历史
        git log 看历史提交记录 叫--online以简洁看，加--graph看分支
        git blame <file>  列表形式看文件的历史修改记录
        git log --author=用户名 //看用户的提交记录
        git blame <file> //看指定文件的修改
## 标签
在里程碑那种时候可以标个标签，比如用 `git tag -a v1.0`命令给最新一次提交打上（HEAD）"v1.0"的标签,Git 会打开你的编辑器，让你写一句标签注解

                

