---
layout: post
title: "基于Jekyll静态框架的Github站点设计"
data: 2018-01-07 16:27:00 +0800
categories: 开源相关
tag: github
---
* content
{:toc}


这里主要是讲述这个博客搭建过程中的心酸历程，主要涉及的是`Jekyll`、`Github`等。也有搭建站点的一些内容。仅作后来人以及本人回顾。错误之处，请留言指正。

<!-- more -->

## Jekyll相关

Jekyll可以将纯文本转化为静态网站。[`Github page`](https://pages.github.com/) 可以直接运行`Jekyll`是它极大的特点，我也是因为这个才关注到这个开源模板的。

有关Jekyll的具体内容参考：

+ 中文官方主页： [http://jekyll.com.cn/](http://jekyll.com.cn/)
+ 英文官方主页： [https://jekyllrb.com/](https://jekyllrb.com/)

因为`Jekyll`是开源项目，所有也可以参考其`Github`主页：

+ `Github主页` : [https://github.com/jekyll/jekyll](https://github.com/jekyll/jekyll)

介绍和使用放在`jekyll/doc/_doc`中。

> 因为自己也还在摸索和探索过程，所以此处不会详细探讨细节。可能在未来的某天会以另外一篇博文的形式放在博客上。

此处主要说明以下`Jekyll`的安装过程。

### 安装Ruby 和 RubyGems

[`Ruby`](http://www.ruby-lang.org/zh_cn/downloads/)是一门语言，不用多解释。而[`RubyGems`](https://rubygems.org/pages/download)其实就是`Ruby`的包管理工具。相当`pip`之于`Python`，`npm`之于`Node`中。

因为`Jekyll`是用`Ruby`语言编写的，所以我们需要安装他们。

> 您最好将它加入**系统环境变量**，这样就可以使用**命令行**玩耍了。

### 安装Ruby
- 官网下载好安装介质`rubyinstaller-2.4.3-1-x64 .exe`，不要2.5.0，不要2.5.0，不要2.5.0，重要的事情说三遍。
- 一路next，傻瓜式安装，安装完先不要按照提示进行MSYS2的安装，国外源很坑的，关掉所有窗口。
- 2.4以后的ruby使用MSYS2。
- **`MSYS2`**是什么的：是一个MSYS的独立改写版本，主要用于 shell 命令行开发环境。同时它也是一个在Cygwin （POSIX 兼容性层） 和 MinGW-w64（从"MinGW-生成"）基础上产生的，追求更好的互操作性的 Windows 软件。
- <http://www.msys2.org/>下载`msys2-x86_64-20170918.exe`
- 一路next就行，安装完关闭安装界面。
#### MSYS2配置
#### 换源
- 默认的源在有些地方速度还可以,教育网内速度一般,可以添加其他镜像提高速度,下面列举了已知的速度还可以源,请大家自己按照现有网速排序,现在有些开源镜像添加了msys2的源,感谢各个开源镜像站点!
- 编辑安装目录下 \etc\pacman.d\ 文件夹下 mirrorlist.msys 等三个文件,如下所示:
`mirrorlist.msys`
```ini
##
## MSYS2 repository mirrorlist
## Changed on 2014-11-15
##
##中国科学技术大学开源软件镜像
Server = http://mirrors.ustc.edu.cn/msys2/REPOS/MSYS2/$arch
##北京理工大学镜像
Server = http://mirror.bit.edu.cn/msys2/REPOS/MSYS2/$arch
##日本北陆先端科学技术大学院大学 sourceforge 镜像
Server = http://jaist.dl.sourceforge.net/project/msys2/REPOS/MSYS2/$arch
##The UK Mirror Service Sourceforge mirror
Server = http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/m/ms/msys2/REPOS/MSYS2/$arch
## Primary
Server = ftp://148.251.42.38/MSYS2/$arch
## Sourceforge.net
Server = http://downloads.sourceforge.net/project/msys2/REPOS/MSYS2/$arch
```
`mirrorlist.mingw64`
```ini
##
## 64-bit Mingw-w64 repository mirrorlist
## Changed on 2014-11-15
##
##中国科学技术大学开源软件镜像
Server = http://mirrors.ustc.edu.cn/msys2/REPOS/MINGW/x86_64
##北京理工大学镜像
Server = http://mirror.bit.edu.cn/msys2/REPOS/MINGW/x86_64
##日本北陆先端科学技术大学院大学 sourceforge 镜像
Server = http://jaist.dl.sourceforge.net/project/msys2/REPOS/MINGW/x86_64
##The UK Mirror Service Sourceforge mirror
Server = http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/m/ms/msys2/REPOS/MINGW/x86_64
## Primary
Server = ftp://148.251.42.38/MINGW/x86_64
## Sourceforge.net
Server = http://downloads.sourceforge.net/project/msys2/REPOS/MINGW/x86_64
```
`mirrorlist.mingw32`
```ini
##
## 32-bit Mingw-w64 repository mirrorlist
## Changed on 2014-11-15
##
##中国科学技术大学开源软件镜像
Server = http://mirrors.ustc.edu.cn/msys2/REPOS/MINGW/i686
##北京理工大学镜像
Server = http://mirror.bit.edu.cn/msys2/REPOS/MINGW/i686
##日本北陆先端科学技术大学院大学 sourceforge 镜像
Server = http://jaist.dl.sourceforge.net/project/msys2/REPOS/MINGW/i686
##The UK Mirror Service Sourceforge mirror
Server = http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/m/ms/msys2/REPOS/MINGW/i686
## Primary
Server = ftp://148.251.42.38/MINGW/i686
## Sourceforge.net
Server = http://downloads.sourceforge.net/project/msys2/REPOS/MINGW/i686
```
#### 更新 
打开终端，输入以下命令：
```msys2
pacman -Syu	
```
更新所有工具,重启msys2(关了重开bat)即可


### 安装Jekyll

打开终端，输入以下命令：

```ruby
$ gem install jekyll
```

这就就ok了。

### 选择Jekyll模板

在终端输入：

```jekyll
$ jekyll server
```
或者

```jekyll
$ jekyll s
```
打开浏览器，输入`http://127.0.0.1:4000/`，就可以看到`Jekyll`为你生成的页面。真的，非常简陋。

这个时候，你有以下的方法改善：

+ 从头到尾自己设计
+ 选择一个模板

此处我选择较为简单的方式，选择一个**模板**。那么你可能会问，模板从哪里来。因为`Jekyll`开源，所以我们很容易获得很多资源。

+ 当然专门收集模板的网站：[http://jekyllthemes.org/](http://jekyllthemes.org/)
+ 在`Google`上搜索`Jekyll`和`Github`，在人家的仓库中`download`别人的模板(要注意人家是否允许拷贝哦)。

选择了模板后要根据自己的需求更改，而且主要是在`_config.yml`文件中。此处不予详细讨论，以后另有博文详细说明。

**这里，我假设你已经根据自己的要求搭建好了自己的`Jekyll`博客**。

---------------

## Github仓库

#### 有两种方式创建

- 1、在github主页创建新的仓库，命名为`yourname.github.io`，然后本地`clone`下来，把`jekyll`生成的内容放入文件夹上传至`Github`。
- 2、将jekyll生成的文件夹作为仓库命名为`yourname.github.io`，然后通过`Git`命令将整个博客文件上传至`Github`。

这样，在你的浏览器中输入：`https://yourname.github.io`就可以访问你的这个静态博客了。


-----------------

## 搭建自己的站点

有以下几个步骤：

### 购买域名

可以在很多地方购买到域名，这里你们可以自己鉴别。

### 域名实名认证中，后续补充下面的内容



------------------------------------

## 可供参考的网址

+ 在`Hosting`上运行`Jekyll` [https://blog.timowens.io/running-a-jekyll-site-on-reclaim-hosting/](https://blog.timowens.io/running-a-jekyll-site-on-reclaim-hosting/)
+ 我的博客是如何搭建的(`github pages` + `HEXO` + 域名绑定) [http://www.jianshu.com/p/834d7cc0668d](http://www.jianshu.com/p/834d7cc0668d)
+ 搭建一个免费的，无限流量的`Blog`--`github Pages`和`Jekyll`入门[http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

----
转载请署名，请勿非法转载。