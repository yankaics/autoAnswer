# autoAnswer
autoAnswer

和简单搜索、汪仔助手、UC答题助手一起答题。

- 为什么要做这个？

西瓜视频目前不支持分屏应用，得用两个手机，一个看答案一个答题。这个项目可以让这些在电脑上运行。

- 为什么要采用hack客户端的方式？

直接调用Api获取数据要先分析整个鉴权认证过程（模拟cookies，sessionId，和一些不知道的XXId）。

- 为什么sever用python编写？

这个纯粹是因为想练习python。

- 为什么用nginx做反向代理？

有些接口不支持跨域，用nginx只是因为暂时不熟悉python的反向代理写法。。

# process

+ 1、设置浏览器UA为手机的UA，搜索User Agent Switcher，可用的user-agent-string如：
  
  `Mozilla/5.0 (Linux; Android 7.1.1; Google Pixel - 7.1.0 - API 25 - 1080x1920 Build/NMF26Q; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/52.0.2743.100 Mobile Safari/537.36 SogouSearch Android1.0 version3.0 AppVersion/5802`

+ 2、host添加一行（搜狗会校验origin）

  `127.0.0.1 fex.sa.sogou.com`

+ 3、用nginx中start.bat在80端口启动nginx代理，浏览器打开 fex.sa.sogou.com

+ 4、开启Py的Sever接受数据，Sever中调用adb命令点击手机

+ 5、数据手机分析开发中...