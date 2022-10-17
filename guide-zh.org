#+TITLE: 一年成为Emacs高手 (像神一样使用编辑器)
#+AUTHOR: 陈斌 (redguardtoo)
#+LANGUAGE: zh
#+TEXINFO_DIR_CATEGORY: Emacs
#+OPTIONS: ^:{} toc:nil H:5 num:0
* 简介
成为高手很容易. 我初学Emacs时常忘记"退出"的快捷键, 一年后我完全掌握了Emacs.

一些文章强调Emacs有多牛, 但关于"如何做"则语焉不详. 即使涉及到"如何做", 谈细节多而方法论少.

很多人花了大量时间"学习"Emacs却最终放弃,就是因为过于拘泥细节,而方法论上出了问题.

例如,初学者背少用的快捷键会有很大的挫折感.一个月记住50个快捷键后算很厉害了.但是Emacs可以配置快捷键的命令近7000个.如果记住所有快捷键等同于掌握Emacs的话,一个人需要花至少十年.99%的快捷键很少用,少用的按键很快就忘了.花了十年做了99%都是无用功的事情当然非常打击积极性.

除本文之外的任何一本Emacs教程都会列出至少100个"常用"的快捷键.我不会刻意教你某个快捷键,但是会告诉你:
- 一个人记住的快捷键数量和他的Emacs水平没有必然联系
- 20个甚至更少的快捷键够用了
- 常用的是哪些快捷键
- 其他按键在使用过程中会自然记住

我在快捷键这个问题上指明大方向,避免了记住7000个快捷键这个恐怖的任务,学习过程变轻松很多.

这个例子说明了本文独特之处在于集中火力在"方法论".

方法论基于实践和经验总结,有事实证据支持.例如常用快捷键列表是用 [[https://github.com/dacap/keyfreq][keyfreq]] 的插件积累至6个月数据统计出来的.

全文结构如下:
- 为什么 Emacs 值得学习, 对开源文化熟悉可跳过这一章
- 实事求是,戒骄戒躁
- 充分利用高手成果, 不要重复发明轮子
- 尽快掌握 Emacs 的步骤
- 如何提高 (社区, 阅读, 知识管理)
- 跳出具体技巧, 重要的是人
- 答疑和小结
* 广告                                                                          :noexport:
我开发了一套教授文本文件操作术的课程, 此操作术可用于所有主流编辑器和IDE(Visual Studio Code, Vim, Emacs, Sublime Text 3, IntelliJ IDEA...).

中国大陆用户的课程链接: [[https://edu.51cto.com/sd/de7e7]]

海外华人的课程链接: [[https://www.udemy.com/course/how-to-code-faster-zh/]]
* 目录                                                                          :noexport:TOC:
- [[#简介][简介]]
- [[#为什么用-emacs-可选][为什么用 Emacs (可选)]]
  - [[#学会了emacs就同时学会了其他编辑器][学会了Emacs就同时学会了其他编辑器]]
  - [[#优秀的社区][优秀的社区]]
  - [[#编程速度更快][编程速度更快]]
  - [[#emacs-会永存][Emacs 会永存]]
  - [[#可以立刻开始工作][可以立刻开始工作]]
  - [[#一年指的是一年中的空闲时间][一年指的是一年中的空闲时间]]
- [[#实事求是戒骄戒躁][实事求是,戒骄戒躁]]
  - [[#理解软件自由][理解软件自由]]
  - [[#避免门户之见][避免门户之见]]
  - [[#以科学理性做指导][以科学理性做指导]]
- [[#具体步骤][具体步骤]]
  - [[#无-linuxunix-经验新手的快速指南-可选][无 Linux/Unix 经验新手的快速指南 (可选)]]
  - [[#读官方教程][读官方教程]]
  - [[#以实际问题作为切入点][以实际问题作为切入点]]
  - [[#待解决的问题设定优先度][待解决的问题设定优先度]]
  - [[#站在巨人的肩膀上][站在巨人的肩膀上]]
  - [[#报-bug][报 bug]]
  - [[#持续改进][持续改进]]
  - [[#加入社区更上一层楼][加入社区更上一层楼]]
- [[#读书最有效][读书最有效]]
  - [[#emacswiki][EmacsWiki]]
  - [[#emacs-lisp-书籍推荐-可选][Emacs Lisp 书籍推荐 (可选)]]
- [[#知识管理][知识管理]]
  - [[#配置纳入-github-的版本控制][配置纳入 GitHub 的版本控制]]
  - [[#将相关资料备份][将相关资料备份]]
- [[#第三方插件推荐][第三方插件推荐]]
- [[#emacs-是一种生活方式][Emacs 是一种生活方式]]
- [[#付之于行动][付之于行动]]
- [[#使用-evil][使用 Evil]]
  - [[#text-object][Text Object]]
  - [[#leader-键][Leader 键]]
  - [[#evil-兼容-emacs-原生插件][Evil 兼容 Emacs 原生插件]]
  - [[#evil-专用的插件介绍][Evil 专用的插件介绍]]
  - [[#在-shell-和-interactive-interpreter-中使用-evil][在 Shell 和 Interactive Interpreter 中使用 Evil]]
  - [[#evil-的小结][Evil 的小结]]
- [[#答疑][答疑]]
  - [[#新手怎么开始][新手怎么开始]]
  - [[#如和理解他人配置][如和理解他人配置]]
  - [[#他人配置是否太重量级][他人配置是否太重量级?]]
  - [[#其他第三方配置][其他第三方配置]]
  - [[#该使用-emacs-的哪个版本][该使用 Emacs 的哪个版本]]
  - [[#vi-用户要转阵营吗][Vi 用户要转阵营吗?]]
  - [[#为什么很多-vi-用户不接受-evil][为什么很多 Vi 用户不接受 Evil?]]
  - [[#不习惯默认快捷键-怎么办][不习惯默认快捷键, 怎么办？]]
  - [[#使用第三方配置后有些奇怪的-bug-怎么改][使用第三方配置后有些奇怪的 bug, 怎么改?]]
  - [[#已更新软件包-但是没有任何作用-也没有任何错误信息][已更新软件包, 但是没有任何作用, 也没有任何错误信息]]
  - [[#有配置问题][有配置问题]]
  - [[#启动报错][启动报错]]
  - [[#自己的简单配置好控制][自己的简单配置好控制]]
  - [[#自己加的插件无效][自己加的插件无效]]
  - [[#我想用-windows-版本的-emacs-而不是-cygwin-版本-怎么做][我想用 Windows 版本的 Emacs 而不是 Cygwin 版本, 怎么做?]]
  - [[#emacs-在代码跳转和自动完成上和商业-ide-有差距-怎么办][Emacs 在代码跳转和自动完成上和商业 IDE 有差距, 怎么办?]]
  - [[#邮件][邮件]]
  - [[#为什么-emacs-启动时从服务器-elpa-安装第三方软件包-package-会失败][为什么 Emacs 启动时从服务器 (elpa) 安装第三方软件包 (package) 会失败?]]
  - [[#有些网站-emacs-访问不了][有些网站 Emacs 访问不了]]
  - [[#是否应尽早学习-emacs-lisp][是否应尽早学习 Emacs Lisp]]
  - [[#掌握-emacs-lisp-是否是成为高手的必要条件][掌握 Emacs Lisp 是否是成为高手的必要条件?]]
  - [[#有必要学习键盘宏-keyboard-macros-吗][有必要学习键盘宏 (Keyboard Macros) 吗?]]
  - [[#基本操作我会了-下一步学什么迷茫中][基本操作我会了, 下一步学什么迷茫中]]
  - [[#如何学习-org-mode][如何学习 org-mode?]]
  - [[#对于-一切都用-emacs-来完成-的观点你怎么看][对于 "一切都用 Emacs 来完成" 的观点你怎么看?]]
- [[#联系我][联系我]]
- [[#结语][结语]]
  - [[#如何报-bug][如何报 bug]]
  - [[#不要复制粘帖本文][不要复制粘帖本文]]
- [[#版权][版权]]

* 为什么用 Emacs (可选)
虽然本文的重点是"怎么做", 而不是"为什么".但先解释一下Emacs的优秀之处很有必要.

** 学会了Emacs就同时学会了其他编辑器
Emacs的自由度高且历史悠久,所以即使常用的功能也比其他软件类似功能强大的多.

切换到其他编辑器后,可以根据Emacs的独特经验优化自己的工作流.
** 优秀的社区
Emacs Lisp 不同寻常的语法决定了其开发者都是资深开发者, 掌握了多门语言.

** 编程速度更快
IDE 针对特定语言或框架优化, Emacs 完成通用任务更有效.

例如, 我碰到难题需上 IRC 请教国外高手 (工作流是, 粘贴代码到 [[http://gist.github.com]], 在 irc 提问, 看网页, 将解决方案粘贴回来), Emacs 集成了 IRC 工具和浏览器操作就很方便.

口说无凭, 请看高手视频, [[https://www.youtube.com/watch?v=AgRsYOJi6ao][abo-abo演示的查找替换技术]]

顺便说一下, Emacs的"代码自动完成"和"代码导航"两个功能对主流编程语言支持都不错.

"不错"的意思是达到90%的功能,是否能达到100%取决于安装了哪些插件. 达不到100%,适当妥协一下,90%也不错.

不要斤斤计较在"代码自动完成"和"代码导航"要完全复制IDE的体验.而忽视了Emacs的在这两个功能上的特色.

高级程序员对API早已熟悉,在大项目中的新代码和老代码相似.所以他们对"智能"不在意,对写代码速度更重视.

例如web程序员需求在javascript文件写css和html代码. Emacs结合 [[https://en.wikipedia.org/wiki/Ctags][Ctags]] 在同一代码文件自动完成javasscript&html&css,这显然很方便.

** Emacs 会永存
[[https://forum.sublimetext.com/t/project-alive/16005][个人开发者会丧失兴趣]], 公司会倒闭. 但自由软件基金会将一直存在下去.

Emacs 作为其招牌软件也会维护下去, 投资永不会贬值.
** 可以立刻开始工作
软件开源, 配置是纯文本, 且资源消耗小, 安装包很小 (命令行版本 30M 左右), 任何环境下都可用.

这在大项目中特别有益, 例如, 某项目需同时编辑 Perl, Java, C, Bash, SQL, 要编辑远程服务器上的代码, 网速不快. Emacs 的优势就体现出来了.

** 一年指的是一年中的空闲时间
我利用一年中通勤时间就取得了很大进步.

* 实事求是,戒骄戒躁
** 理解软件自由
何为软件自由没有比自由软件基金会更权威了. 建议把 [[https://www.gnu.org/philosophy/free-sw.zh-cn.html]] 反复读, 理解何为四大自由.

一旦真正理解了软件自由, Emacs 就变得非常简单了.

例如, 很多用户习惯让 Emacs 启动时自动从其官方插件仓库 [[https://elpa.gnu.org]] 下载安装插件. 当该网站偶尔下线或者公司的防火墙拦截了对外网站访问时, Emacs 就会启动失败.

这也就是一分钟可以解决的小事, 如果你理解软件自由, *有勇气* 到 =~/.emacs.d/elpa/= 目录下看一看的话。

一个插件仓库 (repository) 本质上就是一个文件夹, 它有一个含有插件列表名为 =archive-contents= 的文本文件, 以及一系列插件包. 你完全可以把这些文件下载下来, 在本地硬盘里建立 ELPA 的镜像.

对个人来说, 安装 [[https://github.com/redguardtoo/elpa-mirror][elpa-mirror]] 每年备份一下所有插件就足够了.
** 避免门户之见
比如用了 Emacs 就排斥 Vim 的快捷键, 或者反之.

避免门户之见的关键就是实事求是.

以 Emacs 和 Vim 的快捷键为例, 两种快捷键完全可以无缝接合.

** 以科学理性做指导
有读者反映我的方法类似于大学里写论文做研究, 事实上这正是我的灵感来源.

Emacs 只是一种技术, 其学习方法和其它技术是通用的.

打好基础, 让自己的知识有 *足够的* 广度和 *适当的* 深度, 对新手是最重要的. 否则会在一些琐碎问题上浪费时间.

新手的错误是花大量时间记快捷键, 事实上网上教程列出的初学者"必知"快捷键不是必需的. 很少用到的快捷键直接输入对应命令就行了. 用 [[http://www.emacswiki.org/emacs/Smex][smex]] 或同类插件输入命令很高效.

* 具体步骤
后文用到的命名惯例,
- =C= 表示按下 Ctrl 键, =M= 表示按下 Alt 键
- =M-x my-command= 表示同时按下 Alt 和 X, 输入 "my-command", 然后回车

** 无 Linux/Unix 经验新手的快速指南 (可选)
建议,
- 不安装任何第三方插件
- 掌握shell基本知识, 什么是环境变量, 什么是 stdin, stdout, pipe. 这些知识可以帮助用户理解 Emacs 如何和其他软件交互
- 读Emacs官方教程(快捷键 =M-x help-with-tutorial-spec-language=), 学会基本的文本操作 (大概十几个快捷键)
- 使用 Emacs 自带的 [[http://www.orgmode.org][org-mode]], org-mode 关键是用起来, 只要记住按 TAB 键是展开内容就可以了, 其他都不用学

Org-mode 是Emacs内置的插件.用来写文档,记笔记,管理个人工作事务等等. 有很多第三方插件拓展. 不是三言两语可以概况其功能的. 它最受欢迎的的特性是支持名为 [[https://en.wikipedia.org/wiki/Getting_Things_Done][GTD (Getting Things Done)]] 的工作流. 很多人认为 org-mode 是最好的GTD软件. 新手以此入门上手很快, 可以立刻提高自己的生产力.

** 读官方教程
按以下步骤阅读教程:
- 不安装任何插件打开 Emacs, 比如在 Shell 中运行命令 =emacs -nw -Q=
- =M-x help-with-tutorial= 打开教程

完成该教程仅需半小时.

即使不用 Emacs 默认快捷键, 这步也是必须的, 不要跳过!

最起码要知道以下命令,
- =M-x describe-variable=, 快捷键 =C-h v=, 查看变量的文档
- =M-x describe-function=, 快捷键 =C-h f=, 查看命令的文档
- =M-x describe-key=, 快捷键 =C-h k=, 查看快捷键的文档
** 以实际问题作为切入点
努力能很快得到回报, 会越学越有乐趣, 进入正反馈.

例如, 我急需 GTD 的工具, 而 Emacs 的 [[http://orgmode.org/][Org-mode]] 是同类软件中最好的. 用 Org-mode 节省了时间后, 我对 Emacs 兴趣高涨.

反面例子是啃Lisp教程开始Emacs之旅, 坚持下来的人寥寥无几.
** 待解决的问题设定优先度
关键在于理性地考虑你最迫切需要解决的一个问题.

*以这个问题作为出发点*, 除此之外都可以妥协.

虽然 Emacs 无所不能, 但是饭也要一口一口吃. 有时退一步等于进两步.

例如, 我一直以为 Emacs 的中文显示很完美, 搞不懂为什么有人在字体配置上花那么多时间.

在读者反馈后, 才明白原来我一直在终端下使用Emacs, 终端软件可以完美显示中文字体, 所以就没 Emacs 什么事了. 需要配置字体的人用的是图形界面 Emacs.

当初只在终端下使用 Emacs 是因为需连接到远程服务器. 我认为这是重点. 甚至为此放弃了漂亮的配色主题 (后来发觉此牺牲毫无必要). 塞翁失马, 由此也避免了图形界面版本的所有问题.
** 站在巨人的肩膀上
刚开始我也是抱着玩的心态, 到处拷贝别人代码到我的配置中去. 浪费了很多时间.

后来我停止折腾, 安心用 [[http://www.sanityinc.com/][Steve Purcell]] 的 [[https://github.com/purcell/emacs.d][Emacs 配置]] , 从此走上正轨.

初学者开始阶段应以模仿为主. 这点是本文核心思想.

之前提过, 我选择不背快捷键,而用smex优化输入命令的效率.这也是因为我使用他人成熟配置后学会的.

考虑一下:
- 我就是这么做的, [[https://github.com/purcell/emacs.d/issues?direction=asc&page=1&sort=created&state=closed][看看一年内我给他报了多少 bug]]
- 要超越高手就必须了解其高度, 你需要一年时间去模仿去学习
- 基于 Purcell 的配置给他报 bug (甚至是提交patch), 你就是考虑到了他未考虑到的问题, 至少在这点就超过他了, 日积月累就很可观了

** 报 bug
像武侠小说那样拜高手为师是白日做梦. 唯一能让高手指点的办法是先付出. 最可靠的付出就是报 bug.

我就是这样 [[https://github.com/capitaomorte/yasnippet/issues/256][学到一些高级 Lisp 技巧的]].

** 持续改进
要在高手已有工作上改善. 即使是微小的改善, 如果坚持一段时间, 就是巨大的进步了, 你就可以在这一点上笑傲江湖.

再找出另一高手需要改善的地方, 使用同样的方法.

例如, 默认在 Emacs 中移动子窗口焦点不是很方便. 需按 =C-x o= 多次. 我找到了 emacs 插件 [[https://github.com/dimitri/switch-window][switch-window]], 只要按 =C-x o= 一次, 会有提示子窗口编号, 接下来输入编号就可以了. 但还有改善空间, 我又找到了 [[https://github.com/nschum/window-numbering.el][window-number.el]], 只要按 =M-NUM= 一次. 这个方法已几乎完美, 但 Alt 键还是有点慢, 我结合 [[https://github.com/emacs-evil/evil][evil]] 和 [[https://github.com/cofi/evil-leader][evil-leader]], 可以按逗号和数字飞速切换子窗口了. 我的这个点子后来被[[https://github.com/syl20bnr/spacemacs/commit/0931e4abece1307def3a024f4f2717359fb8d6e8][spacemacs采用]].现在已是大多数Emacs用户的标准配置了.
** 加入社区更上一层楼
最重要的是专一. 不去定阅和 Emacs 无关的话题.

*** Reddit
[[http://www.reddit.com/r/emacs/][Reddit]] 是最好的.
*** GitHub 是高手云集的地方
GitHub 的版本控制服务很好. 现在它的社区化倾向越来越强了, 我喜欢.

例如, 可以看一下 [[https://github.com/search?p=1&q=stars%3A%3E20+extension%3Ael+language%3Aelisp&ref=searchresults&type=Repositories]] 上最酷的 Emacs 插件.

*** 博客
最好的是 [[https://planet.emacslife.com/][Planet EmacsLife]], 多个 Emacs 博客的集合.

*** 在 Stack Overflow 上搜索相关讨论
google "emacs-related-keywords site:stackoverflow.com"

我会定期搜索, 同一帖子反复精读. 因为讨论质量很高.

[[http://emacs.stackexchange.com]] 是 Stack Overflow 旗下专门的 Emacs 问答社区.
*** 到 Youtube 上看 emacs 相关的视频
我就是看了 [[http://www.youtube.com/watch?feature=player_embedded&v=oJTwQvgfgMM][Google Tech Talks 上这个 Org-mode 作者的介绍]] 而爱上 org-mode.

不过 Youtube 搜索结果是最佳匹配的. 由于相关视频并不多, 如按照默认算法, 每次总是那几个. 所以如果关注最新进展, 搜索应以时间排序.

* 读书最有效
** EmacsWiki
[[http://www.emacswiki.org/][EmacsWiki]] 是社区维护的文档.

有人抱怨文档太乱, 质量参差不齐. 前者我有同感. 后者不赞同. EmacsWiki 文档质量相当高, 因其是 *唯一的* 半官方文档. 忍受其乱中有序的现状吧.

最佳阅读方法是, 选定一特定主题, 从头读到尾. 这样对最新进展都了解了. 是否要采用其建议另当别论.

** Emacs Lisp 书籍推荐 (可选)
Bob Glickstein 的 [[http://www.amazon.com/Writing-GNU-Emacs-Extensions-Glickstein/dp/1565922611][Writing GNU Emacs Extensions]] 是最好的.

生动, 例子丰富. 作者用心安排了书的结构. 例如, 很早就介绍了 defadvice 的用法. defadvice 是 Emacs Lisp 的精华.

Xah Lee 提供 [[http://xahlee.info/emacs/emacs/buy_xah_emacs_tutorial.html][付费 Lisp 教程]] 也相当不错.

* 知识管理
不要低估长时间的累积效应.

例如 Steve Purcell 的配置. 2000 年开始维护,其质量不用我多费口舌.

知识积累的越多, 这些知识之间的联系就会越多. 联系增长的速度是以指数的方式增长的. 如从头来过, 意味着积累知识的书面记录丢失了. 损失是很大的. 基数已归零, 增长的量又能有多少.

这也是后文谈到为什么要用工具保存配置和知识的原因.
** 配置纳入 GitHub 的版本控制
我的配置见 [[https://github.com/redguardtoo/emacs.d]].

版本控制可以认为是一个集中式的知识管理, 任何时刻任何地点对配置的修改都要及时上传合并 (merge). 这是积累能力的关键.

共享实际也是一种利己行为, 很多人用我的配置等于帮我测试.
** 将相关资料备份
我还写了许多博客文章. 这些文章都存在 org 格式的文件中. 最后发布的静态博客也纳入版本控制, 参见 [[http://github.com/redguardtoo/redguardtoo.github.io]].

* 第三方插件推荐
建议对少数优秀插件深入研究.阅读甚至编写相关代码.
    
以下是清单：
| 名称         | 说明                               | 同类插件      |
|--------------+------------------------------------+---------------|
| [[https://github.com/emacs-evil/evil][Evil]]         | 将 Emacs 变为 Vim                  | 没有          |
| [[http://orgmode.org/][Org]]          | Org-mode, 全能的笔记和GTD工具      | 没有          |
| [[https://github.com/company-mode/company-mode][company-mode]] | 自动完成输入, 支持各种语言和后端   | auto-complete |
| [[https://github.com/capitaomorte/yasnippet][yasnippet]]    | 强大的文本模板输入工具             | 没有          |
| [[http://www.emacswiki.org/emacs/FlyMake][flymake]]      | 对不同语言做语法检查               | flycheck      |
| [[https://github.com/abo-abo/swiper/blob/master/ivy.el][ivy]] or [[https://github.com/emacs-helm/helm][helm]]  | 自动完成, 在其上有插件完成具体功能 | ido           |
| [[https://github.com/magit/magit][magit]]        | 玩转 git                           | 没有          |

* Emacs 是一种生活方式
Geek 其他方面也很牛. 举一反三你收获会很多.

[[http://sachachua.com/blog/][Sacha Chua]] 就是这样的女孩, 这是她的 [[http://www.youtube.com/watch?v=eoyi2vrsWow][Youtube 录像]]. 她学习的方式是 [[http://sachachua.com/blog/2012/07/transcript-emacs-chat-john-wiegley/][让 Emacs 自动将手册语音合成]], 这样她在房间里走来走去的时候也可以听文档了.

我现在有意识地整理高手名单, 观察他们 *除了 Emacs 外* 用什么工具.

例如, [[https://github.com/mooz/js2-mode][js2-mode]] 的维护者 Masafumi Oyamada (网名 mooz) 也开发了 [[https://github.com/mooz/keysnail][keysnail]] 和 [[https://github.com/mooz/percol][percol]]. 特别是 percol, 使我命令行效率提高了 10 倍.

这个阶段可称之为 *心中有剑, 手中无剑*.

是否用 Emacs 不重要了, 重要的是随心所欲. 例如, 很多人争论哪个编辑器自带的文件管理较好. 我 [[http://blog.binchen.org/posts/how-to-do-the-file-navigation-efficiently.html][从 mooz 那学到大招后]], 就跳出五行外, 不在三界中了.

* 付之于行动
如何行动因人而异.

关键是真正理解本文要点.

例如，你是否意识到之前的章节意味着以下行动:
- 找出所有插件的作者
- 在 Twitter/GitHub/Reddit 上跟随他们
- 通读他们已发表的贴子

* 使用 Evil
Evil 是 [[https://github.com/emacs-evil/evil][Vim 模拟器]].

如果你不熟悉 Vim, 在命令行里运行 =vimtutor= 或者安装 Emacs 插件 [[https://github.com/syl20bnr/evil-tutor][evil-tutor]] 学习 Vim 基本命令.

该教程大概需要半小时. 关于 Vim 的基本操作的讨论就到此为止了. 网上教程汗牛充栋, 你可自行阅读.

这里展示一些高级技巧 (有些技巧是我独创的).

** Text Object
了解 [[http://vimdoc.sourceforge.net/htmldoc/motion.html][Vim Text Object]] 的概念.

Evil 的强大之处就是你可以用 Emacs Lisp 来自定义 =Text Object=. 自由的 Lisp 使得你完全超越 Vim 的 "约定俗成".

比如在操作自定义的 Text Object 时, 当前焦点完全可以在 Text Object 之外. 这是 Lisp 写的 [[http://blog.binchen.org/posts/evil-text-object-to-select-nearby-file-path.html][寻找附近的文件路径或者 URL.]] 用 Vim Script 写个类似的脚本难很多. 即使你用了 [[https://github.com/kana/vim-textobj-user][vim-textobj-user]] 之类的插件辅助开发也没用的.

而且 Lisp 代码完全可以调用 *任何* 的第三方插件或者 Emacs 的不计其数的 API. 比如 Evil 中操作 =Text Object= 的过程中可以问用户问题, 访问网站等等.

实现这些额外功能对 Vim 来说很难.

** Leader 键
Vim 自带 Leader 键的功能, 你先按了 Leader 键 (很多人定义为空格键) 后, 再按其他键 (比如 =kk=) 会触发你自定义的命令. 本质就是给你更多的快捷键.

在 Emacs 中需要使用第三方插件如 [[https://github.com/noctuid/general.el][general.el]] 来实现此功能.

某些 Vim 用户不能迁移到 Evil 的原因就是自定义了太多使用 Ctrl 键的快捷键, 和 Emacs 默认的快捷键有冲突.

这些用户没有意识到的是借鉴 Emacs 的思想, 他们在 Vim 和 Emacs 的效率可以有巨大的提升. 我只提三点供参考:

第一, 充分利用 Leader 快捷键. 我看过大多数 Vim 高手在 GitHub 上的设置, 他们一般定义 *10 到 20 个* Leader 相关的快捷键.

我定义了 *300 个* 相关的快捷键.

典型 Evil 用户 (如 Spacemacs 用户) 大概有 *3000 到 10000 个* 相关快捷键可用.

第二, Vim 用户的另一个问题是快捷键没有优化. 常用命令的快捷键应按. 何为常用命令须来自 *真实数据*.

这是我用 Emacs 的插件 [[https://github.com/dacap/keyfreq][keyfreq]] 测试月的数据 (我的 Leader 键定义为逗号):
| Times | Percentage | Command                                | Key                   |
|-------+------------+----------------------------------------+-----------------------|
|  4967 |     12.00% | evilmi-jump-items                      | %                     |
|  2892 |      6.99% | compile                                | , o o                 |
|  2178 |      5.26% | find-file-in-project-by-selected       | , k k                 |
|  1953 |      4.72% | copy-to-x-clipboard                    | , a a                 |
|  1566 |      3.78% | paste-from-x-clipboard                 | , z z                 |
|  1227 |      2.96% | er/expand-region                       | , x x                 |
|   897 |      2.17% | evil-repeat                            | .                     |
|   866 |      2.09% | ido-find-file                          | , x f, C-x C-f        |
|   819 |      1.98% | toggle-full-window                     | , f f                 |
|   815 |      1.97% | etags-select-find-tag-at-point         | C-], , h t            |
|   721 |      1.74% | back-to-previous-buffer                | , b b                 |
|   682 |      1.65% | split-window-vertically                | , x 2                 |
|   539 |      1.30% | find-function                          | , h f, C-h C-f        |
|   494 |      1.19% | counsel-recentf-goto                   | , r r                 |
|   397 |      0.96% | counsel-git-grep                       | , g g                 |
|   376 |      0.91% | delete-other-windows                   | , x 1, C-x 1          |
|   372 |      0.90% | evilnc-comment-or-uncomment-lines      | , c i                 |
|   351 |      0.85% | eval-expression                        | , e e, M-:            |
|   326 |      0.79% | evilmi-select-items                    | , s i                 |
|   320 |      0.77% | paredit-doublequote                    |                       |
|   307 |      0.74% | evil-filepath-outer-text-object        |                       |
|   300 |      0.72% | steve-ido-choose-from-recentf          |                       |
|   295 |      0.71% | split-window-horizontally              | , x 3                 |
|   283 |      0.68% | git-add-current-file                   | , x v a               |
|   279 |      0.67% | winner-undo                            | , x u, , s u, C-x 4 u |
|   278 |      0.67% | describe-function                      | , h d, C-h f          |
|   278 |      0.67% | evil-goto-mark-line                    | '                     |
|   269 |      0.65% | ido-kill-buffer                        | , x k, C-x k          |
|   254 |      0.61% | evil-goto-definition                   | g d                   |
|   253 |      0.61% | pop-tag-mark                           | M-*                   |
|   251 |      0.61% | git-messenger:popup-message            | , x v b, C-x v p      |
|   246 |      0.59% | my-goto-next-hunk                      | , n n                 |
|   237 |      0.57% | evilnc-comment-operator                | , ,                   |
|   235 |      0.57% | flyspell-goto-next-error               | , f e, C-,            |
|   214 |      0.52% | evil-exit-emacs-state                  |                       |
|   212 |      0.51% | browse-kill-ring-forward               |                       |
|   210 |      0.51% | flyspell-buffer                        | , f b                 |

第三, 由于 Lisp 的强大 Leader 键的使用在 Emacs 中有无限可能
- 使用 [[https://github.com/noctuid/general.el][general.el]] 定义多个 Leader 键
- 可在切换文件时切换 Leader 键等等.

** Evil 兼容 Emacs 原生插件
如果你真正理解了我前面的章节, 这就根本不是问题.

之前我提到了要保持头脑开放, 要尽可能抄高手的代码, 积极地报 bug 等观点. 现在让我演示一下如何应用.

一开始我每装一个新的插件, 都要辛辛苦苦设置 evil 的快捷键.

有一天我问自己, Lisp 那么强大, Evil 那么优秀, 也许有更方便简洁的方案?许多人说不行不一定是真理, 只有实际调查过的人才有发言权.

我也没有自己钻研 Evil 的代码, 取而代之的是 [[https://github.com/emacs-evil/evil/issues/511][给 Evil 的开发者 Frank Fischer 报了个 bug]], 他给我了一个方案, 根本不需要重设快捷键.

这是这个方案在 [[https://github.com/emacsmirror/git-timemachine][git-timemachine 中]] 的 [[http://emacs.stackexchange.com/questions/9842/disable-evil-mode-when-git-timemachine-mode-is-activated][完美应用]].
** Evil 专用的插件介绍
我选择 [[http://melpa.org][MELPA]] 上最流行的5个Evil插件介绍一下, 类似优秀插件还有很多.

要点不在于你装了多少插件, 而在于理解由于 Lisp 的强大和 Emacs 的自由, 这些插件功能更多, 更容易拓展.

*** [[https://github.com/timcharper/evil-surround][evil-surround]]
对应 [[https://github.com/tpope/vim-surround][vim-surround]].

我通常用 [[https://github.com/magnars/expand-region.el/blob/master/expand-region-core.el][expand-region 选中一段文本, 然后按 =S= 或者 =M-x evil-surround-region= , 再按任意字符 (比如双引号) 就可以在文本]] 首尾两端附加该字符.

当然它也支持修改删除操作.

之前提到的 text object 也完美支持.

懂 Lisp 的话可以修改 =evil-surround-operator-alist= 自己定制操作.

*** [[https://github.com/redguardtoo/evil-nerd-commenter][evil-nerd-commenter]]
对应 [[https://github.com/scrooloose/nerdcommenter][vim-nerd-commenter]], 这是我写的, 功能更强大.

你可以 =M-x 5 evilnc-comment-or-uncomment-lines= 快速注释当前 5 行或者取消注释当前 5 行.

你也可以选中一个区域 =M-x evilnc-comment-or-uncomment-lines=

由于 Emacs 的强大, 默认就支持所有世界上已知的语言, 而核心代码也就是 1 行而已. Vim 插件对应的功能代码要有 400 行.

如果你在 [[http://orgmode.org/][org-mode 格式的单一文件中]] 中混杂多种语言的话, 它也能智能识别.

这个功能在 Vim 中基本不可能实现.
*** [[https://github.com/redguardtoo/evil-matchit][evil-matchit]]
对应 [[https://github.com/tmhedberg/matchit][vim-matchit]]. 又是我写的. 自然功能更强大.

本质就是你当前焦点在文件的某个位置 A, 你按 =%= 或者 =M-x evilmi-jump-items=, 焦点移到位置 B, 你再按同样的键, 又回到了位置 A.

比如在一个 HTML 文件中, 你就可以在 =<body>= 和 =</body>= 间跳来跳去. 其他各种编程语言都支持.

Vim 对应的代码我读过, 限制比较多, 比如你一定要先定义一对正则表达式来匹配 A 和 B 的位置. 这种限制在某些语言如 Python 中就会比较麻烦.

Emacs 的实现就完全体现了 Emacs 的自由精神, 我建立了一个动态查询的矩阵, 矩阵的元素就是函数对象而已. 用户可以在运行时替换这些函数对象, 所以怎么跳转, 跳到哪都是完全自由的.

所以 python 的支持就毫无问题. 想支持更多的语言或者对我的实现不满意, 在 =.emacs= 中写几行 Lisp 代码就可以了.
*** [[https://github.com/syl20bnr/evil-escape][evil-escape]]
按自定义快捷键退出当前的各种状态, 相当于 Vim 中的 =ESC= 或者 Emacs 中的 =C-g=.

我定义自定义快捷键为 =kj=. 如果你想效率高的话, 取消的默认快捷键就太慢了.

让我给你举个例子说明什么叫效率高. 我移动手指去按 ESC 键需要 0.5 秒.

Sublime Text 默认的文本搜索要比我的 Emacs 设置慢 40 倍. 如果 Sublime Text 搜索需要 40 秒, 那么节省取消键的 0.5 秒毫无意义.

Emacs 只要 1 秒完成搜索, 所以取消键从 0.5 秒减少到 0.1 秒的感觉就完全不一样.
*** [[https://github.com/bling/evil-visualstar][evil-visualstar]]
对应 [[https://github.com/bronson/vim-visual-star-search][vim-visual-star-search.]]

选择一段文本, 按 =#= 或者 =*= 搜索.
** 在 Shell 和 Interactive Interpreter 中使用 Evil
可以 =M-x shell= 或者 =M-x term= 进入 Shell.

传统上大家都在 Shell 中用 Emacs 的默认快捷键.

不过仔细计算过后我发现 Vim 的快捷键更有效率.

Shell 的作用无非就是运行命令或脚本代码, 输出运算结果.

当我们在 Emacs 中运行 Shell 的时候, 命令和代码往往是从别的地方拷贝过来的.

粘贴命令和代码到 Shell 中, 分析/过滤/搜索输出的结果, 都是 Vim 的快捷键更方便.

我之前提到的所有关于 Evil 的技巧和插件都适用于此.

Interactive Interpreter 和 Shell 没有本质区别, 无非就是解释器支持的语言不一样罢了. 比如 [[https://github.com/nonsequitur/inf-ruby][inf-ruby]] 支持 Ruby.

可以按 =C-z= 切换回纯 Emacs 快捷键.
** Evil 的小结
对 Vim 用户来说, Evil 不仅提供了 Vim 的完美模拟, 还开辟了用 Lisp 拓展 Vim 的新世界.

对 Emacs 用户来说, Evil 也不仅仅是提供了新的快捷键, 而是提供了更多的可编程的数据结构和范式 (如 text object).

关键是发挥你的创造力, 自由地接合 Emacs 和 Vim 的长处, 发明新技术和新技巧. 这种机会目前是很多的, 赶快行动起来吧.

* 答疑
** 新手怎么开始
到 [[https://github.com/redguardtoo/emacs.d]] 参考 "Install stable version in easiest way" 一节.

只要点击下载两个 zip 文件就可以了, 不需 git 的任何知识.

** 如和理解他人配置
除了官方文档外. 看 EmacsWiki 和源代码也很有效. 窍门是源代码文件的头部有使用指南和作者的联系方式.

** 他人配置是否太重量级?
成熟配置都是轻量级的, 因为优化过了.

例如有种叫 [[http://www.gnu.org/software/emacs/manual/html_node/elisp/Autoload.html][Autoload]] 的技术. 只有用到模块的某一功能时那个模块才会被载入内存.

** 其他第三方配置
[[https://github.com/search?l=Emacs+Lisp&o=desc&q=emacs&ref=searchresults&s=stars&type=Repositories][搜 github]]

也可用 [[https://github.com/redguardtoo/emacs.d][我的配置]]：
** 该使用 Emacs 的哪个版本
目前稳定版是 27.2. 通常不用担心版本问题. 主流的 Linux 发行版会处理.

** Vi 用户要转阵营吗?
嘿嘿, 我也是 Vi 精通后转到 Emacs 的. 就是因为 Emacs 的强大 (例如和 gdb 的完美结合) 以及其脚本语言是 Lisp.

当然 Vi 的多模式编辑和快捷键比 Emacs 要高效得多, 所以最佳方案是 Vi + Emacs.

目前我用 [[http://www.emacswiki.org/Evil][Evil]], 在 Emacs 下模拟 Vim, 结合两者优点.

现在我是 *神用编辑器之神*!

** 为什么很多 Vi 用户不接受 Evil?
因为他们对 Vim 快捷键做了深度配置. Emacs 默认要经常按 Ctrl 键, 如自定义的 Vim 快捷键也用 Ctrl 键, 难免有冲突.

解决办法是大家都使 [[http://stackoverflow.com/questions/1764263/what-is-the-leader-in-a-vimrc][Leader]] (Vim 直接支持, Emacs 需 [[https://github.com/cofi/evil-leader][第三方插件]]).

还有一个办法是待在 Vim 的舒适区里. 如能忍受没有 Org-mode 和 Lisp 的生活, 那么不会有问题.

如犹豫不决, 请重读 "态度决定一切" 一节.

我一旦认识到 Evil 和 Evil-leader 的潜力, 立刻把我 Vim 的设置按 Emacs 的重设了一遍。

更光辉灿烂的例子就是Spacemacs作者了, 无数的 github 星星代表了他的成功.
** 不习惯默认快捷键, 怎么办？
*忍*!

默认快捷键经过几十年考验相当高效, 未成为高手前还是要忍.

如一定要在用 Windows 快捷键的, 可考虑 [[http://xahlee.info/emacs/][ergoemacs]].
** 使用第三方配置后有些奇怪的 bug, 怎么改?
不要改! 参考上文 [[https://github.com/redguardtoo/mastering-emacs-in-one-year-guide/blob/master/guide-zh.org#站在巨人的肩膀上][站在巨人的肩膀上]] 一章, 你觉得奇怪是因为缺乏经验, 把某些特性误认为是 bug. 请坚持至少一年.

例如, 有人反映右边第 80 列处总有一竖线, 希望能去掉.

实际上这是一特性, 提醒用户一行宽度不要超过第 80 列. 这是 [[http://www.emacswiki.org/emacs/EightyColumnRule][每行不要超过 80 列的原因]].

我建议第一年应 *尽量理解而不妄加判断*.

** 已更新软件包, 但是没有任何作用, 也没有任何错误信息
删除 HOME 目录下的 =.emacs=, =~/.emacs.d/init.el= 取代原来的 =.emacs=.
** 有配置问题
- 读官方教程
- 善用网络和我提供的信息

例如,
问：在 =.emacs.d= 中的 =init.el= 文件起什么作用？
答：搜索 "emacswiki init.el".
** 启动报错
先确认已装上了 *你需要的* 第三方命令行工具, 这些工具是可选的, 清单见 [[https://github.com/redguardtoo/emacs.d][我的 README]].

如排除了以上原因, 带上 =--debug-init= 参数重新启动, 然后将错误信息及环境报告到对应的开发者.

报告时应给出细节. 例如很多读者给我的 bug 都是由于第三方插件版本较新引起的, 我拿到版本号后, 才能下载特定版本以重现 bug. 否则只能靠猜, 来回邮件浪费很多时间.
** 自己的简单配置好控制
那你就是走我后悔莫及的老路, 一个人在黑暗中摸索. 开头兴致很高, 但现实是残酷的, 碰到复杂问题解决不了. 只能逃避, 借口 Emacs 太复杂而放弃了.

我最终醒悟过来走上光明大道, 很多走上岐路的人恐怕就没这个觉悟和毅力了.

希望自己掌控坦率地说是一个非技术问题, 因为没有自信心, 所以有补偿心态. 希望通过一种错误的方式来证明自己. 结局无非是恶性循环.

正确地方法是放下身段至少一年 (我已反复强调这一点), 打好基本功, 读书, 虚心学习.

** 自己加的插件无效
Emacs 是个开放平台, 其众多插件发布前并不一定有严格的测试. 所以插件之间可能有冲突.

这也是我为什么建议初学者直接使用第三方配置配置的原因, 众多兼容性问题已解决.

没解决的问题最好提交bug报告, 而不是自己去钻研 Lisp.
** 我想用 Windows 版本的 Emacs 而不是 Cygwin 版本, 怎么做?
需对命令行操作熟悉. 关键知识点有两个：
1. 设置 =HOME= 环境变量, 因为 =.emacs.d= 中的某些 Lisp 脚本假定 =.emacs.d= 在 HOME 所指定的路径中.
2. Emacs 的某些功能需要使用第三方的命令行工具, 这些工具的路径应该添加至环境变量 =PATH= 中 (可选, 原因见后面).

如你不知道如何在 Windows 下添加修改环境变量, 不知道如何安装第三方工具, 建议还是先用 Cygwin 中的 Emacs, 因它已自带工具, 没有的话安装也方便. 且在 Cygwin 下环境变量 HOME 默认已设.

第三方命令行工具清单请参考[[https://github.com/redguardtoo/emacs.d][我的配置]]中的 README.
** Emacs 在代码跳转和自动完成上和商业 IDE 有差距, 怎么办?
现在流行[[https://melpa.org/#/?q=lsp][基于LSP的方案]].

我通常用 =Ctags= 作为后端引擎, 因其通吃所有语言. 虽然解析效果差一点, 但是恰当的命名规范 (尽量少重名) 可以弥补.

Java 和 C# 语言的主力开发工具最好用 IDE 而不是 Emacs.

** 邮件
我用 [[http://www.gnus.org/][Gnus]]. 但有很多其他方案.

如你必须访问 Microsoft Exchange Servers, 还要用 [[http://davmail.sourceforge.net/][Davmail]].

用了 Davmail 后, 还可以用 [[http://getpopfile.org/][Popfile]] 来分捡邮件. Davmail + Popfile 让我生活在天堂.
** 为什么 Emacs 启动时从服务器 (elpa) 安装第三方软件包 (package) 会失败?
请启动 Emacs 后, 运行 =M-x package-refresh-contents= 以从服务器更新软件索引, 然后重启 Emacs 即可.

** 有些网站 Emacs 访问不了
在命令行中启动 Emacs 时加上 =http_proxy=your-proxy-server-ip:port= 前缀.

例如,
#+BEGIN_SRC sh
http_proxy=http://127.0.0.1:8000 emacs -nw
#+END_SRC
** 是否应尽早学习 Emacs Lisp
不用,顺其自然最好.

Lisp 语法和通常的语言不同, 除非有相当编程经验 (至少 10 年), 一般人都会对其有一点负面情绪 (当然是毫无道理的偏见!). 学习任何新东西, 长期来说兴趣最重要. 一开始应避免任何负面情绪.

Emacs Lisp 又是只用于 Emacs 的语言, 有大量术语需要掌握. 如 "Buffer", "Yank", "Font face", 只有资深用户才能理解.

所以在使用经验不足前学习软件拓展语言(Domain Specific Language)很低效.

参考前文关于找到切入点的一节, 我推荐的顺序是, 先用优秀的配置享受到好处, 有了兴趣后学习 Lisp 就水到渠成了.

选择适合自己的路, 一年以后天才和普通人达到的高度都是一样的.
** 掌握 Emacs Lisp 是否是成为高手的必要条件?
否. 但 Lisp 是很强大的语言, 特点是一切皆可改. 当我说 "一切" 的时候, 我就是指字面意义上的 "一切", 不是修辞上的夸张.

我用过许多编辑器, 除了 Emacs 没有一个能做到 "一切可改" 这点 Vim 也不行.

学点 Lisp 对提高 Emacs 水平没坏处. 另外 Lisp 语法不错, 值得一学.

顺便说一下, Lisp 很简单, 比 VB 容易多了, 一旦你适应其语法, 就会发觉它其实蛮友好的, 至少少打很多字.
** 有必要学习键盘宏 (Keyboard Macros) 吗?
没必要, Lisp 足够了.

但是键盘宏生成的 Lisp 代码有时候比较有趣, 建议你精通 Lisp 后再来玩玩键盘宏.
** 基本操作我会了, 下一步学什么迷茫中
关键是你打算用这把瑞士军刀做什么.

前文已强调过以兴趣和解决实际问题作为切入点.

举一些我自己的例子说明:
- 我有写博客需要, 懒得用 Wordpress 那个破界面, 所以用 [[https://github.com/punchagan/org2blog][org2blog]]
- 开发 Ruby on Rails 程序需要 IDE, 装了 rinari
- 做跨平台 C++ 桌面开发, 装了 cmake-mode
- 需在多个子窗口间跳来跳去, 所以装了 [[https://github.com/nschum/window-numbering.el][window-numbering.el]]
- 大项目需同时调试多种语言, 所以装了 [[https://github.com/redguardtoo/evil-nerd-commenter][evil-nerd-commenter]], 这样不用记特定语言的语法就可注释掉代码.
** 如何学习 org-mode?
[[http://www.cnblogs.com/Open_Source/archive/2011/07/17/2108747.html][Org-mode 简明手册]] 是不错的中文教程.

最好的英文教程是 Carsten Dominik (Org-mode 发明者) 在 [[http://orgmode.org/talks.html][google tech talks 上的演讲]]. 其要点为 org-mode 本质是一个文本文件, 只要记住按 TAB 展开或者缩进条目就可以了. 其他特性可慢慢学.
** 对于 "一切都用 Emacs 来完成" 的观点你怎么看?
不要走火入魔. Emacs 本质是个平台, 提供了无限可能性.

从实用角度讲, Emacs 和其他工具结合有时能更快完成工作 (不过在没有一年的修炼之前 *千万不要猜 Emacs 不能做什么*).

以下是 Emacs 不一定能吃独食的地方:
- 剪贴簿: 应结合命令行工具 xsel (Linux) /pbpaste (OSX) /putclip (Cygwin)
- Web 浏览: 用传统浏览器配合其插件
- 远程登录管理: 用 screen/tmux
- FTP: 用专门的 FTP 软件
- 文件管理: 用专用软件
- Lisp 速度比较慢，如有大计算量的工作, 交给第三方工具来作.

重点是头脑灵活, 既坚信 Emacs 无所不能, 也适当变通.

* 联系我
这是我的 [[https://twitter.com/#!/chen_bin][Twitter]] 和 [[https://plus.google.com/110954683162859211810][Google Plus]] 以及 [[http://www.weibo.com/u/2453581630][微博]], 我在新浪微博账号"emacsguru".

博客为 [[http://blog.binchen.org]].

我不回答具体配置的问题. 如你通读本文, 应知道哪里找答案更好.

* 结语
再强调一下本文最重要的观点:
- 以 *解决实际问题* 产生的兴趣引导
- *完全照抄世界顶尖高手如 Steve Purcell 的配置*, 尽量避免自己写 Lisp
- 给高手报 bug 就是最好的学习,
- 学习 Emacs 和 *学任何专业技能 (拉小提琴, 解数学题) 的方法论都是一样的*, 请参考 [[http://book.douban.com/subject/4726323/][一万小时天才理论]].

关键是你以严肃的态度把其当作专业技能学习.

很多人之所以不赞同我的核心观点, 是因为内心深处还有把 Emacs 当玩具来炫耀 "我有多酷" 的意识.

Emacs 强大到可以作为另类娱乐来博眼球. 但本质是专业人士使用的神器.

打个比方, 职业杀手对于刀只关心两件事:
1. 高效地杀人
2. 任何环境下都可靠

刀的装饰是否漂亮或技巧是否自己原创对他并不重要.

Emacs 就是那把刀.
** 如何报 bug
本文官方网址为 [[https://github.com/redguardtoo/mastering-emacs-in-one-year-guide]].

有任何疑问, 请在以上网址报 bug. 这比 Email 快. 因 GitHub 会以邮件通知我, GitHub 邮件永远归类至我的最优先文件夹下.

如给我发 Email, 会淹没于垃圾邮件中.

** 不要复制粘帖本文
Emacs 本质上是一个社区和平台, 不断有新的有趣的人和技术出现. 我会定期更新本文.

如果你拷贝粘帖全文, 会使自己和他人错过更新.

我建议分享本文的链接, 中英文纯文字版会发布在 GitHub 上 ([[https://github.com/redguardtoo/mastering-emacs-in-one-year-guide]])
* 版权
本文采用以下协议进行授权, [[http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh][自由转载 - 非商用 - 非衍生 - 保持署名 | Creative Commons BY-NC-ND 3.0]], 转载请注明作者及出处.
