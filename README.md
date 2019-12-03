
## 如何优雅的提交代码 
软件开发的小伙伴们，对git 是非常熟不过的，每天应该都会提交代码到自己的 Repositories或者公司私有的 gitlub ，当然也有些小伙伴会使用svn或者其它的提交工具,该文章分享一下如何使用git commit优雅的提交，能够让团队的小伙伴更能够 git review，我会按照以下的目录继续分享配置。

平时提交代码的commit message
使用 commitizen 插件提交后的commit message
使用 commitizen + cz-customizable 插件后的提交 commit message
使用gitmoji-cli 插件后的提交 commit messag
如何配置commitizen
如何配置commitizen + cz-customizable
如何配置itmoji-cli


大家先别着急安装这些插件，要把文章看完看看那个适合自己，从中选择一个适合自己的或者团队的，会在文章的后面添加暗转使用

1 git提交代码的commit message
git commit应该是我们大多数提交时使用的提交命令，一般在命令行的操作如下

git add .|| git add -A
git commit -m'提交说明'
git push 
那么我们在远程git  repository会看到是这样的信息 或者在git log中看到的 

图的提交信息看上去还可以吧。一般般但是没有什么两店只能知道这些是日常提交的记录



2 使用 commitizen 的 commit message
git add -A
git  cz
cz-cli@4.0.3, cz-conventional-changelog@3.0.1

? Select the type of change that you're committing: fix:         A bug fix

? What is the scope of this change (e.g. component or file name): (press enter to skip) root/app.tsx root/app.less root/index.tsx

? Write a short, imperative tense description of the change (max 52 chars):
 (10) 这里是简短更改的说明

? Provide a longer description of the change: (press enter to skip)
 这里是详细更改的说明

? Are there any breaking changes? Yes

? Describe the breaking changes:
 说明更改原因
? Does this change affect any open issues? Yes

? Add issue references (e.g. "fix #123", "re #123".):
 "fix #123 https://github.com/zhangfaliang/react-hooks/commits/master"
[master 6c90b87] fix(root/app.tsx root/app.less root/index.tsx): 这里是简短更改的说明
 1 file changed, 1 insertion(+), 1 deletion(-)

git push
来看看这次的提交，在git上面的显示



看上去是不是比上次的提交要炫酷一些 ，可以直接看到改变的 文件 以及详细的说明 ，还有issue的地址和连接 



3 commitizen + cz-customizable 插件后的提交 commit message
这个是在commitizen上的基础上添加一个可以插拔的插件，实现自定的commit模板

git add -A
git cz
cz-cli@4.0.3, cz-customizable@6.2.0



Line 1 will be cropped at 100 characters. All other lines will be wrapped after 100 characters.

? 选择一种你的提交类型: 💪  WIP:      Work in progress
? Denote the SCOPE of this change（表示此更改的范围）: root/app.tsx root/app.less root/index.tsx
? 短说明:
 这里是简短的说明
? 长说明，使用"|"换行(可选)：
 这里是详细更改的说明

###--------------------------------------------------------###
WIP(root/app.tsx root/app.less root/index.tsx): 这里是简短的说明

这里是详细更改的说明
###--------------------------------------------------------###

? 确定提交说明? Yes
[master 86be287] WIP(root/app.tsx root/app.less root/index.tsx): 这里是简短的说明
 1 file changed, 1 deletion(-)


看图，其实和上个版本的提交类似，只是实现了自定义或者是说适合自己的提交模板





我们先不看第一步、四步，咱们看一下二、三步他们的模板都是类似的

type
type用于说明 commit 的提交性质。经常使用的

feat 新增一个功能 
fix 修复一个Bug docs 文档变更
style 代码格式（不影响功能，例如空格、分号等格式修正） 
 refactor 代码重构 
 perf 改善性能
 test 测试 
 build 变更项目构建或外部依赖（例如scopes: webpack、gulp、npm等） 
 ci 更改持续集成软件的配置文件和package中的scripts命令，例如scopes: Travis, Circle等 
 chore 变更构建流程或辅助工具 revert 代码回退

scope
scope说明commit影响的范围。根据实际业务划分，或者组件库开发划分，可以省略。

Body
commit的详细描述，说明代码提交的详细说明。

Footer
如果代码的提交是不兼容变更或关闭缺陷，则Footer必需，否则可以省略。



4 使用gitmoji-cli 插件后的提交 commit messag 这个非常给力，类型非常丰富
 gitmoji -i
✔ Gitmoji commit hook created successfully
➜  my-app git:(master) git add -A
➜  my-app git:(master) ✗ git commit
? Choose a gitmoji: (Use arrow keys or type to search)
  🎨  - Improving structure / format of the code.
  ⚡️  - Improving performance.
  🔥  - Removing code or files.
  🐛  - Fixing a bug.
  🚑  - Critical hotfix.
  ✨  - Introducing new features.
  📝  - Writing docs.
 ✨  - Introducing new features.
  📝  - Writing docs.
  ✅  - Updating tests.
  🏁  - Fixing something on Windows.
  🚨  - Removing linter warnings.
  🚧  - Work in progress.
  ⬇️  - Downgrading dependencies.
  🤖  - Fixing something on Android.
  ⏪  - Reverting changes.
❯ 🍻  - Writing code drunkenly.
  🚸  - Improving user experience / usability.
? Choose a gitmoji: 🍻  - Writing code drunkenly.
? Enter the commit title [13/48]: 修改root下的App文件
? Enter the commit message: 去掉冗余代码
[master 235adf3] :beers: 修改root下的App文件
 1 file changed, 1 insertion(+), 1 deletion(-)


哈哈咱么来了  Writing code drunkenly （喝酒撸代码 😁 ）看Git repository的记录





哈哈 在commit前面多了一个的小图标是不是很有意思。好了废话不说了咱们看看这些花里胡哨的commit的配置吧

如何配置commitizen
安装命令行工具
全局安装
npm install -g commitizen cz-conventional-changelog


在您的主目录中创建一个.czrc文件，其路径指向首选的，全局安装的commitizen适配器

echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
你们都准备好了！现在任何git仓库，并使用git cz代替git commit，您会发现commitizen提示。

全局安装搞定  😃（我之前选择的全局安装）。咱们接下啦看看项目中安装

