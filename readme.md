### 1、新建一个仓库，并上传到github
```
	echo "# JXGF_CNG_V4.0" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/ycxzfforever/JXGF_CNG_V4.0.git
	git push -u origin master
```
### 2、git删除文件夹/文件（不删除本地文件）
	先声明一点，如果要同时删除本地的和github上的文件，直接删除本地的再push就行了，比较简单。这里的要求是不能删除本地的文件，而要删除github里，就是网页上的文件。
	其实质就是删除缓冲区里的文件，再提交给服务器端。<br>
	1.首先进入要删除的文件夹或文件的根目录下，如```F:\myprojects\supermarketmanager1115```<br>
	2.执行下面的语句”some-directory”是相对于本地根目录下的文件夹/文件路径<br>
	
		1、git rm -r --cached some-directory
		2、git commit -m 'Remove the now ignored directory "some-directory"'
		3、git push origin master
	
	另外git pull --rebase origin master这句挺有用的，记录一下。这句的意思是：把github上最新的文件下载下来。
	
	
### 3、增加另外一个仓库地址
	git remote set-url --add origin 仓库地址

### 4、配置图形化diff工具和merge工具
	#difftool 配置
	[diff]
		tool = bc4
	[difftool]
		prompt = false
	[difftool "bc4"]
		cmd = "\"D:/Program Files (x86)/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\""
		
	#mergeftool 配置
	[merge]
		tool = bc4
	[mergetool]
		prompt = false
	[mergetool]	
		keepBackup = false #让git mergetool不再生成备份文件（*.orig）
	[mergetool "bc4"]
		cmd = "\"D:/Program Files (x86)/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\""
