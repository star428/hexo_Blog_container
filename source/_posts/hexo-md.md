---
title: hexo博客搭建
date: 2023-01-09 17:06:10
tags: [hexo]
---

最近在学习 c++（其实是复习），总想着要把学过的某些东西稍加记忆，要不然每次查询网页速度实在堪忧，思来想去还是得有一个自己的博客记录一下重要的技能，以便下次查阅。

<!-- more -->

## 基于 hexo + github pages 的静态博客搭建

其实博客搭建有个问题，就是如果自己折腾的话迁移性其实一般，因为东西会越加越多，到最后想迁移的时候就会感觉无从下手。而且后面如果有服务器的话就更不必要了。有更好的选择，这里我们仅仅讨论如何迁移目前已有的东西。(阅读本文的前置条件是去找怎么搭一个最简单的 hexo 静态博客)

后续分为四个方面简单介绍 hexo 文件格式和怎么迁移

- **_下载必须项_**
- **_hexo 文件介绍_**
- **_使用 github 迁移_**

### 下载必须项

其实对于不想仔细研究 hexo 内部构成，只想使用博客写作的人而言，其实关注点并不是多么花里胡哨的界面（越花越难以迁移，同时会消耗大量精力），私以为博客的重点在于文章质量而不在于博客多么的花哨，简介大方即可。

首先使用 hexo，最好的学习方式是去官网看完最简单的使用示例，其实 hexo 只有两个东西需要下载，`Node.js`和`git`即可，这里不再赘述如何下载，参照 hexo 官网（[hexo](https://hexo.io/zh-cn/docs/)）即可下载完成（已有的不必再复制粘贴产生网络垃圾，重要的是解决问题的逻辑）

下载完成后其实就要初始化等等操作，anyway，为了简化流程我也把整体的博客代码移到 github 上，这样下次迁移很方便只需要`git clone`即可

### hexo 文件介绍

其实 hexo 也没有那么神秘，强大的其实是 github pages，我们可以将静态网页托管到 github pages 上，github 会给你一个域名叫做`yourName.github.io`，使用这个域名就可以访问放在你这个仓库中的静态网页，而 hexo 呢就是可以帮助你生成这个网页。你只需要写好 markdown，hexo 会帮助你生成静态网页。

后面会介绍相关的 hexo 如何生成的语句，这里我们先介绍一下结构：

```bash
- public // 存放你真正生成的静态网页的地方
- source
  - _data // 存放自定义网页格式，可以修改网页圆角等等
  - _post // 存放你真正博客的地方
  - others // 你定义了tags，categories等等都会生成新文件夹

- config.yml // 改变系统设置的地方
- config.next.yml // 改变next风格的地方（将themes/next里面的config.yml粘贴出来即可，这个文件的优先级比里面的要高会替代同时不会污染原有config）
```

其实大部分修改修改的都是 config.next.yml 里面的东西，anyway 这里怎么修改大可以去自己找好玩的，这里不想对怎么修改长篇大论，没有过多意义，因为我的修改也是从别人那里学来的没有多少创新，这里 po 出来我的相关借鉴文章：
[next 主题的配置使用记录](https://www.cnblogs.com/ywang-wnlo/p/Hexo-NexT.html)

[nexT 主题更改背景图片和边框圆角](https://zhuanlan.zhihu.com/p/280784973)

[hexo 添加动态背景](https://hexo-next.readthedocs.io/zh_CN/latest/next/advanced/%E5%8A%A8%E6%80%81%E8%83%8C%E6%99%AF/)

### 使用 github 迁移

其实实现也很简单，就是把你使用`hexo init`生成的所有文件全部放到 github 上而已，此时如果迁移可以使用如下命令：

```bash
git clone git@github.com:star428/hexo_Blog_container.git
```

结束，此时已经迁移完毕，使用如下语句进行初始化：

```bash
hexo clean // 清除生成的网页
hexo g     // 重新生成hexo网页
hexo s     // 在本地预览网页
hexo d     // 推送网页到yourName.github.io上去
```

最终网页的展示（也不用展示了所见即所得哈哈哈哈哈）
over，下一篇文章见~
