# B站上传视频小工具

<img src="./cover.png" width=500 height=300/>

项目地址: <https://gitee.com/nbodyfun/bilibili_video_uploader>

## 介绍
**一个Bilibili视频上传的小工具 :)**

2020/10/10测试有效, 有问题不妨issue～

作者：**NBody编程那些事**

<img src="./img/my_qrcode.jpg" width=250 height=300/>

求关注～

## 功能

1. 上传并发布视频
2. 支持指定标题、视频简介
3. 支持指定分区、标签
4. 支持选择自制或转载(转载可写来源)
5. 查看所有分区
6. 可以当命令行工具使用，也可以代码调用

## 使用帮助

```
usage: bilibili_up.py [-h] [-c COPYRIGHT] [-s SOURCE] [-t TITLE] [--desc DESC]
                      [-d] [-l] [-tid TYPEID] [-ta TAGS] [-sd SESSDATA]
                      [-bj BILI_JCT]
                      [video_path]

一个B站上传发布视频的小工具 :)

positional arguments:
  video_path            视频文件路径

optional arguments:
  -h, --help            show this help message and exit
  -c COPYRIGHT, --copyright COPYRIGHT
                        类型: 1为自制 2为转载。默认为2
  -s SOURCE, --source SOURCE
                        来源声明(转载必要), 默认为"来源于网络"
  -t TITLE, --title TITLE
                        标题, 不加即为视频文件名
  --desc DESC           视频描述, 默认为空
  -d, --debug           调试模式，更详细的输出
  -l, --typelist        查看分区列表
  -tid TYPEID, --typeid TYPEID
                        视频分区id(使用-l参数查看), 不指定则使用推荐分区
  -ta TAGS, --tags TAGS
                        视频标签, 英文逗号分隔, 不指定则使用推荐标签
  -sd SESSDATA, --sessdata SESSDATA
                        身份验证cookie(上传必要), 浏览器cookies中获取
  -bj BILI_JCT, --bili_jct BILI_JCT
                        CSRF身份验证cookie(上传必要), 浏览器cookies中获取
```

## 获取 SESSDATA 和 CSRF

这里以 **谷歌浏览器** 为例。

首先我们可以在链接栏左侧看到一个小锁，如果你没有使用HTTPS，那么可能会显示 **不安全** 的字样，点击以后，下面有个Cookies。

![](./img/step1.png)

点开后，我们在下面找到以下两个键对应的值，分别是 SESSDATA 和 bili_jct，这里注意一下，bili_jct 就是 CSRF 。

![](./img/step2.png)

## 示例

```
python bilibili_up.py -sd 你的sessdata -bj 你的bili_jct demo.mp4
```
