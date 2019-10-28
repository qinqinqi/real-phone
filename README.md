# 移动端真机调试方法

1. chrome真机调试（USB）
2. weinre调试（同局域网）
3. spy-debugger调试（同局域网、证书）



 三种方法的优缺点：

第一种：chrome真机调试，有一个很大的局限性就是，只能调试手机端的chorme浏览器，对于UC、QQ这些浏览器均不适用，因此在调试兼容问题的时候，帮助不大，但是最大的优点是简单快捷。

第二种：weinre调试方法，安装和使用不复杂，适用于全平台的调试，即任何手机的任何浏览器都可以进行调试，不过需要手机和电脑在同一网段下。

第三种：spy-debugger，安装稍微复杂一点，spy-debugger集成了weinre，不过还增加了抓包工具，使用最为方便。但是仍然要求手机和电脑在同一网段下。



# 1.chrome调试

手机端下载好chrome浏览器，使用USB连接到PC，打开手机的USB调试模式。

然后在PC打开chrome浏览器，在地址栏输入：“chrome://inspect ”,勾选“discovery usb device”。然后在手机端浏览网页，点击inspect，进行调试。



# 2.weinre调试

嵌入JS代码   实时刷新

是一款基于webkit的远程调试工具，借助于网络可以在PC上直接调试运行在移动设备上的远程页面。

本地服务器：可以使用http-server、Tomcat等，也可以使用编译器集成的服务。

安装并启动weinre之后，在要调试的页面增加一个脚本：

```
<script src="http://电脑的IP地址:8090/target/target-script-min.js#anonymous"></script>
```

在本地启动一个服务器，点击elements进行调试

最后，调试结束后要删掉值钱啊嵌入的脚本



# 3.spy-debugger调试

Spy-debugger内部集成了weinre，通过代理的方式拦截所有的html自动注入weinre所需的js代码。简化了weinre需要给每个调试的页面增加JS代码。



特点：

​	1.页面调试+抓包

​	2.操作简单

​	3.支持HTTPS

​	4.soy-debugger内部集成了weinre、node-miotmproxy、AnyProxy

​	5.自动忽略原生APP发起的https请求，只拦截webview发起的https请求。对是用来SSL pinning技术的原生App不造成任何影响。

​	6.可以配合其他代理工具一起使用过（默认使用的是AnyProxy）

​	7.手机要安装证书（node-mitmproxy CA根证书）

​	8.在手机上选中一个元素时，可以在电脑上看到相应的信息，还可以在控制台看到JS的log信息。



# 4.nginx调试

安装nginx，在nginx的配置文件中做好相关配置，启动nginx，手机和电脑在同一局域网下，手机端打开配置的域名+端口号链接就可以访问。















