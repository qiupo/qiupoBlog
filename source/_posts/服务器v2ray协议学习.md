---
title: 服务器v2ray协议学习
author: Taoqiupo
date: 2021-01-13 08:48:27
tags: v2ray
category: 服务器
index_img: https://proxy.qiupo.workers.dev/?https://raw.githubusercontent.com/qiupo/myImages/master/img/20210113091123.png
---
## v2ray搭建
&emsp;&emsp;之前看过一些网络协议，在研究的时候就发现有这么个v2ray的工具，可以加密连接，所以拿来研究以下。
1. 首先你需要买一台服务器/轻量云服务器，哪个便宜买哪个，我自己测试之后，8M的带宽就能完全应付日常使用了，装上Centos系统。
2. 买好之后ssh连接到服务器上，可以用电脑自带的终端/cmd，或者用别的软件，我用的是Termius，比较方便，输入账号密码之后，进入服务器
3. 我之前使用的官方自己的代码搭建的，虽然也可以但是不够直观，所以又找到一个比较好的轮子，v2-ui，可以在可视化的操控v2ray的连接情况。只需要在控制台输入
```
bash <(curl -Ls https://blog.sprov.xyz/v2-ui.sh)
```
一般来说都没问题的，会直接进入下面的环节，然后就是漫长的等待，等待他下完v2-ui-linux，如果网速快不需要的多久，不快的话可能就得20来分钟了.
项目地址是[v2-ui](https://github.com/sprov065/v2-ui)
+ PS:如果遇到连接问题，修改etc/hosts，新增一行
```
199.232.28.133 raw.githubusercontent.com
```
大概率可以解决问题的。
+ 如果输入命令没有显示，需要把`-Ls`改成`-L`，这样就把错误暴露出来了，可以直接按照错误去修正

4. 全新安装后，在浏览器中打开 http://<服务器IP>:65432 即可访问面板，默认用户名和密码都是 admin，当然你也可以在控制面板中输入v2-ui,按照提示修改端口和重置。

***！！！不过请你一定要到服务器的安全设置里，将端口放行，一般在安全配置里面，不放行是进不去网页的***

5. 进入网页后的操作就简单多了，直接添加就行，改动端口和传输配置ws或者tcp，可以自行研究

6. 另外呢，还可以自己添加bbr加速tcp连接，可以让网速更快，直接在控制台输入这个：
```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```
7. 运行完之后会出现脚本页面，自己选择安装魔改还是plus，整个流程大致就是先按1或者2 ，然后在按照提示运行完成后，在次进入这个页面输入4或者5或者6，成功之后就会显示开启成功，加速成功啦。
8. 服务器最好dd以下系统，给你一个纯净系统
综上就是大致的流程了。