---
title: 翻墙神器－shadowsocks
date: 2016-06-09 21:31:07
tags:
  - 翻墙神器
  - ss
  - shadowsocks
  - aws
  - GFW
  - 国防网
  - 谷歌
---

技术的进步来源于对未知的探索，想成为一个伟大的老司机离不了国外牛逼的技术社区，而GFW的强大众所周知，怎么样跨过GFW来科学上网是每个程序员的必备技能

so经过这么多翻墙工具的坑之后隆重推荐一个翻墙的神器-->shadowsocks，shadowsocks的优点就不多说了，在使用方面来说，跨平台无疑是最大的优点。
提供windows、mac、linux、android、和ios版本。
推荐去[https://shadowsocks.com/client.html](https://shadowsocks.com/client.html)  下载对应的版本，也可以购买付费套餐（但不建议购买，有点贵，不过应该挺稳定的）。这个网站提供的服务靠谱、速度也挺快，就是太贵了。适合那种一开电脑就科学上网的人。
本文介绍是基于VPS服务器搭建shadowsocks服务

## 第一步：VPS服务器

自己选择VPS服务器的推荐选择比较靠谱的云主机提供商，不然经常宕机也是个不小的坑，推荐
[https://www.linode.com/](https://www.linode.com/)，价钱来说属于比较便宜的：
![linode](http://7xpwlr.com1.z0.glb.clouddn.com/linode.png)，对VPS云主机来说选择1GB得足够使用了。
也可以选择AWS，绑定信用卡的话AWS会送一年云主机的使用权，属于比较划算的类型。
AWS地址：[https://aws.amazon.com/cn/](https://aws.amazon.com/cn/)

## 第二步：搭建VPS
### 服务器端：
Debian / Ubuntu:
```
apt-get install python-pip
pip install shadowsocks
```
CentOS:
```
yum install python-setuptools && easy_install pip
pip install shadowsocks
```
使用
```
ssserver -p 443 -k password -m rc4-md5
```
如果要后台运行：
```
sudo ssserver -p 443 -k password -m rc4-md5 --user nobody -d start
```
如果要停止：
```
sudo ssserver -d stop
```
如果要检查日志：
```
sudo less /var/log/shadowsocks.log
```
用 -h 查看所有参数。你也可以使用 配置文件 进行配置。具体请看[这里](https://github.com/shadowsocks/shadowsocks/wiki/Shadowsocks-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
### 客户端
客户端下载
[Mac](https://github.com/shadowsocks/shadowsocks-iOS/releases)
[Windows](https://github.com/shadowsocks/shadowsocks-windows/releases)
文档：[https://github.com/shadowsocks/shadowsocks/wiki](https://github.com/shadowsocks/shadowsocks/wiki)
具体配置：
![http://7xpwlr.com1.z0.glb.clouddn.com/aws%20ss.png](http://7xpwlr.com1.z0.glb.clouddn.com/awsss.png)
将刚才填写的对应地址端口号填入相对位置，然后打开Chrome浏览器，输入[https://www.google.com](https://www.google.com)，
你会发现打开了新世界大门：
![site:virgo.one](http://7xpwlr.com1.z0.glb.clouddn.com/google.png)
