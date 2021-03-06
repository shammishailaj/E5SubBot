# E5SubBot

![](https://img.shields.io/badge/language-go-blue.svg)
![](https://img.shields.io/badge/license-GPL-lightgrey.svg)

A Simple Telebot for E5 Renewal

Golang + MySQL

DEMO: https://t.me/E5Sub_bot

[交流群组telegram](https://t.me/e5subbot)



## 特性

- 自动续订E5订阅(每三小时调用一次)
- 可管理的简易账户系统
- 极为方便的授权方式

## 原理

E5订阅为开发者订阅，只要调用相关API就有可能续期

调用 [Outlook ReadMail API](https://docs.microsoft.com/zh-cn/graph/api/user-list-messages?view=graph-rest-1.0&tabs=http) 实现玄学的续订方式，不保证续订效果。

## 使用方法

1. 在机器人对话框输入 **/bind**
2. 注册应用，使用E5主账号或同域账号登录，跳转页面获得client_secret。**点击回到快速启动**,获得client_id
3. 复制client_secret和client_id，以 `client_id client_secret`格式回复
4. 获得授权链接，使用E5主账号或同域账号登录
5. 授权后会跳转至`http://localhost/e5sub……`
6. 复制整个浏览框内容，在机器人对话框回复 `链接+空格+别名(用于管理账户)`

例如：`http://localhost/e5sub/?code=abcd MyE5`，等待机器人绑定后即完成

## 自行部署
需要MySQL>=5.5版本(开发本地环境是5.5，高的低的没测试过，应该也可以)

Bot创建教程:[Google](https://www.google.com/search?q=telegram+Bot%E5%88%9B%E5%BB%BA%E6%95%99%E7%A8%8B)
#### 二进制文件

在[Releases](https://github.com/iyear/E5SubBot/releases)页面下载对应系统的二进制文件，上传至服务器

Windows: 在cmd中启动e5sub.exe

Linux: 

```bash
screen -S e5sub
chmod 773 e5sub
./e5sub
(Ctrl A+D)
```
#### 编译

下载源码，安装好环境

```shell
go build main.go
```

## 部署配置

在根目录下创建`config.yml`，编码为UTF-8

配置模板

```yaml
#更换为自己的BotToken
bot_token: xxxxx
#不需要socks5代理删去即可
socks5: 127.0.0.1:1080
#公告，/notice触发，\n换行,""别删
notice: "第一行\n第二行"
#最大可绑定数
bindmax: 3
#mysql配置，请提前创建数据库
mysql:
  host: 127.0.0.1
  port: 3306
  user: e5sub
  password: e5sub
  database: e5sub
```

## 注意事项

待填写

## License

GPLv3 