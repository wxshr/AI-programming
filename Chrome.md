# flomo简介

------

flomo是一款小而美的笔记工具，它主要聚焦于以下几个方面：

- **无压记录：**简洁的输入框，让你无压力的记录想法、摘录有价值的观点。无需纠结于主题、段落与排版。
- **方便回顾：**所见即所得，方便你回顾之前记录的内容与统计记录习惯。记录 14 天后，还可开启每日回顾及「随机漫步」功能。
- **弹性管理：**通过标签、批注、搜索、置顶标签及随机漫步等组织方式，将这些内容编织成属于你的知识网络。

更多 flomo 的介绍和使用方法可参考 [flomo 的官方文档](https://help.flomoapp.com/

**痛点：**作为一款笔记软件，经常需要来回切换窗口,复制粘贴多次进行记载,非常的麻烦，所以我想开发一款Chrome插件,在阅读文章时,直接在侧边栏进行笔记的相关操作。

## 1.首先使用Windsurf,制作一个Chrome插件

------

首先新建一个文件夹，使用Windsurf打开。然后在AI对话框中，输入下面的Prompt(提示词):

（flomo的API地址需要替换为自己的地址,flomo会员相关问题参考）

```shell
我想做一个Chrome(chrome)的浏览器插件，使得能够在阅读文章时，通过打开这个插件，在右侧边栏按照制定结构输入内容，然后点击提交，一键通过弗洛莫(Flomo)的API，同步到弗洛莫(Flomo)内。

侧边栏里有几个输入框和一个提交按钮，下面我说说都有哪些文本输入框:
1.原文标题和链接(这个输入框自动带上当前网页的文章内容标题、链接)
2.原文摘要:这里留白给用户自己拷贝进来
3.个人感想:这一部分让用户自己输入

flomo的API地址是:
https://flomoapagecom/iwh/MTY10A/30d923d91fe52a7c9eb6b*******
在flo mo的API说明里，给了个案例，你可以参考:

我想自己开发
POST https://flomoapp.com/iwh/MjE1NDIyMQ/fd4605f107dc9d6155909eadb86b7fa3/
Content-type: application/json
{
    "content": "Hello, #flomo https://flomoapp.com"
}

好了，我是一个不懂代码的产品经理，下面请你先和我讨论清楚产品需求，待我确认后再步步开始
```

**解释:**
这一步相当于实现了两个部分
1.浏览器插件在前端可以被你看到了，并且能够抓到网页链接和标题信息

2.点击提交时，数据能够通过flomo的API，传到flomo的服务器里
其中，我们还把flomo API页面里的代码参考案例提供给了AI，这样AI就知道如何设计代码了，后面还会用到这个小技巧。

------

将上面的内容提交给Windsurf输入框，运行完成后会确定一些细节

![image-20250122230304986](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250122230304986.png)

这里建议你尝试通过和人工智能交流，去表达自己的想法，风帆冲浪是一个很好的工具，我们通过它，能够更多的去表达自己，并指挥人工智能协助我们完成产品工作。

如果你实在不知道说什么好，可以和他说:

你来定吧，开工!

回车后，它就会开始干活:

![image-20250122231424295](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250122231424295.png)

------

![image-20250122234659297](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250122234659297.png)

提示我们需要创建一个简单的图标，包含三种尺寸的图标。（随后我自己使用大模型生成了三个图标，在Windsurf中让它生成也可以）

------

![image-20250122235521782](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250122235521782.png)

![image-20250123000007514](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123000007514.png)

------

**插件测试安装步骤**：



- 打开Chrome浏览器

- 在地址栏输入：`chrome://extensions/`

- 在右上角打开"开发者模式"（Developer mode）

- 点击"加载已解压的扩展程序"（Load unpacked）

- 选择整个插件文件夹（Flomo(插件)文件。这里文件夹指的是自己程序所在的文件夹。

  ------

  

**调试完善步骤：**

![image-20250123000320247](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123000320247.png)

![image-20250123000337055](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123000337055.png)

------

**最终效果：**

![image-20250123000437616](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123000437616.png)

![image-20250123090408143](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123090408143.png)

测试一下，能够正常运行使用，是我期望的效果。

------

小技巧1:先截图，然后在输入框内粘贴，就可以快速把截图提交给windsurf。

小技巧2:“你先想想方案，别急着动手”这句话是因为(windsurf)往往很着急的开始干活，但我们需要它慢一点，先和我们对好方案，等我们确认后再开始，这样可以大幅减少错误率的发生。

------



## 2.开发完成后，记得更新Readme和存档

更新readme，后续自己和AI可以快速了解产品做到哪一步。

存档，如何使用Git，AI修改可能会越改越错，快速回到正确的版本非常重要。

### 2.1更新Readme

在输入框中直接告诉Windsurf：请帮我吧当前版本设置成0.1.0，并更新Readme

### 2.2使用Git存档

首先，打开终端面板。

![image-20250123092450499](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123092450499.png)

在终端里输入初始化Git的命令：

```shell
git init
```

让Git做好添加的准备：

```shell
git add .
```

提交版本，并且对版本写一个注释，后期方便知道（引号中的内容是你自己的注释）：

```shell
git commit -m "0.1.0 完成了插件侧边栏的开发，同步到flomo完成"
```

回车就完成了版本提交：

![image-20250123092923589](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123092923589.png)

查看自己提交的版本：

```
git log --oneline
```

![image-20250123093028525](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123093028525.png)

### 2.3为什么需要使用Git

这一步的重要在于，AI生成的内容是随机的，有可能在某个岔路口越改越乱。当我们无法确定问题所在的时候，最好的办法是回到上一个正确的版本，再从正确的版本启动。

回到上一个版本的命令(87b56db是刚刚git log --oneline命令里面，返回各个版本前面的数字)：

```shell
git reset --hard 87b56db
```

![image-20250123093430090](C:\Users\Tsuki\AppData\Roaming\Typora\typora-user-images\image-20250123093430090.png)

这样便可以返回之前的某个版本，非常方便。

------



## 3.加入AI总结能力

我们开发到现在的v0.1.0版本，只是AI编程软件开发的产品，产品本身并没有AI能力。这个时候可以使用调用大模型的API接口，使得产品具有AI能力。

------

大家可以参考我的（Chinese Name Generator）英文名生成中文名系统，使用智谱免费的GLM-4大模型(在上一个案例里，我们已经和大家介绍了如何获取接口)

```shell
好了，我想在原文摘要右侧加上AI总结功能，点击后调用智谱的API来完成总结:

下面是我看到智谱的模型接入文档:https://bigmodel.cn/dev/api/normal-model/glm-4D然后我的API Key是:3da54b4b6c74c07390875f6981df88dc.D9LxP7XXxxxxx

现在想接入他们的免费大模型:GLM-4 flash，注意，这里必须是GLM-4 flash，不是GLM-4。你先看下，能不能搞定?先回答我，别急着干活
```

最后可以让AI自己总结当前页面内容。（上文中的Prompt中的API Key需要替换为自己的）