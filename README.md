
人生规划千万条，遵纪守法头一条。

射频管家不在维护，感谢大家的支持！

——————更新于2024年9月21日——————

现在开源环境不好，你能看见本工程，就默默好好学习，不要干让大家不舒服的事，因为想真心学习的还是大有人在的。但是如果兄弟你真惹出什么事端，别说你在这学到的就行了。

另外有两个问题可能会让大家卡住，一个是编译时缺文件报错，比如"ArduinoJson.h: No such file or directory"；另一个是按键上下呼呼乱翻页的事。

首先这里说明一下，程序没有问题，2.9也好，3.0.x也好，都没问题。

编译报错那个是因为程序中ESPAsyncWebServer库没了（arduino库改名了），在lib文件夹里，你要手动安装一下。可以通过arduino安装zip库的方式安装一下，或者解压后把库文件和ino文件放一起，引用方式由<>改成""。

按键翻页那个，看看是不是按键的10k上拉电阻没焊好。因为对应esp12f，上是GPIO0，确认是GPIO2，下是GPIO14。正常情况，空闲状态这三个按键都是被10k电阻弱上拉，按下去就是下拉到地。如果空闲状态没被上拉，或者对地短路了，就会呼呼翻页。还有人提到说是初始化的问题，先上拉初始化设置，然后能解决类似的问题。

——————更新于2023年8月27日——————

因原作者（bug508）不再维护射频管家RF，所以我在此更新，并命名为RF-Master来加以区分；

一些问题：原始程序使用的是ESPAsyncWebServer.h，但是Arduino中能下载的是ESPAsyncWebSrv.h（库版本的问题），另外原始程序存在string返回不完整的问题（Arduino版本所致）；

以上问题都会导致编译失败；解决方法就是新增一个库[ESPAsyncWebServer](https://github.com/sprlightning/ESPAsyncWebServer)，该库指向Arduino上的ESPAsyncWebSrv库；另外为缺失string返回值的函数增加返回值，用“return "";”即可；

这体现在3.0.1版本中，bug已修复，其中lib文件夹中的就是[ESPAsyncWebServer](https://github.com/sprlightning/ESPAsyncWebServer)库，需要用Arduino手动安装ZIP库的方式加载进去；
