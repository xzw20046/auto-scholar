# 文献自动爬取装置
 
本程序为根据关键词，自动检索并下载该关键词在Google Scholar上的结果。在运行此软件时需要解决两个前提：1. Python版本在3.0以上
2. 拥有可以访问Google Scholar的网络环境
其中 2. 可以用自定义谷歌镜像网址来代替

# 目录说明
    .
    |-- fabfile.py       # 部署文件，用于将项目推送到远程主机
    |-- handle.py        # 入口文
    |-- keys.txt         # 关键词文件，一行一个
    |-- requirements.txt # 环境依赖包
    |-- settings.py      # 配置文件，详情查看注释
    |-- ss.sh            # ubuntu搭建ss代理
    |-- utils.py         # 主要的功能模块文件

# 使用说明

1、初始化环境
      安装程序必须的模块，使用命令：
      pip install -r requirements.txt

2、设置检索关键词
      将需要检索的关键词存入keys.txt文件中，以换行为间隔以此检索

3、执行任务命令，
      python handle.py --datadir /your/abspath --timeout 5
      任务完成后，自动生成一个以关键词命名的“{keywords}.xlsx”结果检索情况汇总文件 
      数据文件存储在设置的路径下 /your/abspathdata/{keywords}/xxxx.pdf

4、参数说明

    .
    |--datadir    数据文件目录的绝对路径，默认为程序所在目录
    |--timeout   休眠时长，单位秒， 默认为10秒
    |--mirror     自定义谷歌学术镜像网站，如不填写，爬取网址为scholar.google.com.hk
    |--keys        搜索关键词文本文件绝对路径，默认为./keys.txt
    |--scihub     自定义sci-hub下载网站
    |--maxpage    自定义搜索页面数目


# 版本更新
v1.2
-增加自定义谷歌镜像，自定义scihub链接参数输入，可根据自身网络环境选择可访问的网址
-增加自定义关键词文档，并增加了外挂脚本，满足将特定关键词分组并根据组属性存入相同的文件夹的需求
-将爬取休息时间参数从绝对时间改为以参数为正态分布参数的随机时间

v1.21
增加日志保存功能，日志保存在程序文件夹下的all.log文件中

v1.22
增加局部结果显示功能,可设置只显示并下载前多少页的搜索结果
