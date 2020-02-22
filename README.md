# grab_huaban_board
批量下载花瓣网画板、堆糖网专辑


## 解析

* 查看analyze.txt


## 使用

```
git clone https://github.com/staugur/grab_huaban_board
cd grab_huaban_board
```

### for Python

基于python2.7（您需要python环境，不谙此道者建议使用JS版，只需要浏览器即可），测试性地支持py3

1. pip install requests

2. python grab_huaban_board.py --help
```
usage: grab_huaban_board.py [-h] [-a ACTION] [-u USER] [-p PASSWORD] [-v]
                            [--board_id BOARD_ID] [--user_id USER_ID]
                            [--debug] [--proxy] [--proxy_apiurl PROXY_APIURL]

optional arguments:
  -h, --help            show this help message and exit
  -a ACTION, --action ACTION
                        脚本动作 -> getBoard: 抓取单画板(默认); getUser: 抓取单用户
  -u USER, --user USER  花瓣网账号-手机/邮箱
  -p PASSWORD, --password PASSWORD
                        花瓣网账号对应密码
  -v, --version         查看版本号
  -bid BOARD_ID, --board_id BOARD_ID   花瓣网单个画板id, action=getBoard时使用
  -uid USER_ID, --user_id USER_ID      花瓣网单个用户id, action=getUser时使用
  --debug               开启debug输出
  --proxy               开启IP代理池
  --proxy_apiurl PROXY_APIURL
                        IP代理池接口：开启IP代理池后，设置此选项使用非默认接口
```

* 温馨提示：开启IP代理池，需要您使用 `proxy_apiurl` 设置一个能输出ip的接口！

* 详细使用文档请参考: [https://blog.saintic.com/blog/204.html](https://blog.saintic.com/blog/204.html "https://blog.saintic.com/blog/204.html")


### for JavaScript(花瓣、堆糖)

* 详细使用文档请参考：[https://blog.saintic.com/blog/256.html](https://blog.saintic.com/blog/256.html "https://blog.saintic.com/blog/256.html")

* 花瓣网下载脚本主页及安装地址：[请点击我](https://greasyfork.org/zh-CN/scripts/368427-%E8%8A%B1%E7%93%A3%E7%BD%91%E4%B8%8B%E8%BD%BD "请点击我")

* 堆糖网下载脚本主页及安装地址：[请点击我](https://greasyfork.org/zh-CN/scripts/369842-%E5%A0%86%E7%B3%96%E7%BD%91%E4%B8%8B%E8%BD%BD "请点击我")

* 仓库地址：[GitHub](https://github.com/saintic/userscript)

* 当前仓库下有一个`gui_batchdownload.py`脚本用于这两个油猴脚本文本方式的批量下载，用以一定程度上避免迅雷等下载工具。

    - 环境： Windows，Py2.7

    - 依赖： `pip install pyinstaller pywin32`

    - 打包： `pyinstaller.exe -F gui_batchdownload.py -i logo.ico -w --version-file version_file.txt`

## up2picbed

这是一个将花瓣网画板图片上传到[picbed](https://github.com/staugur/picbed)的脚本。

你需要用`grab_huaban_board.py`下载画板或用户，使用`up2picbed.py`上传画板或
用户所有画板，这个脚本会增量上传（即自动跳过已经上传的文件，但此功能基于
本地存储文件.up2picbed.dat且文件索引严格，如果删除dat文件则重传，如果文件名
改变则重传）。

```
$ python ./up2picbed.py -h
usage: up2picbed.py [-h] [-b] [-u] [--picbed-url PICBED_URL]
                    [--picbed-token PICBED_TOKEN]
                    board_or_user

positional arguments:
  board_or_user         画板ID或用户名

optional arguments:
  -h, --help            show this help message and exit
  -b, --board           上传画板，允许逗号选择多个，默认此项
  -u, --user            上传单个用户下所有画板
  --picbed-url PICBED_URL
                        picbed的根域名
  --picbed-token PICBED_TOKEN
                        picbed的用户token
```

示例：

1. 上传画板: `./up2picbed.py --picbed-url https://picbed.saintic.com --picbed-token Token 画板ID`

2. 上传用户: `./up2picbed.py --picbed-url https://picbed.saintic.com --picbed-token Token -u 用户名`

## TODO

1. --board_ids 多画板
2. --user_ids 多用户
3. --igonre 指定忽略画板
4. ~~ip代理池~~

But，以上todo暂无计划，py版目前只针对bug


## 友情链接
1. [MacOS GUI 备份程序](https://github.com/ZhuPeng/grab_huaban_board "MacOS GUI 备份程序")
