时差党看不了OB解说TI预选，本打算挂个直播录像边码代码，无奈斗鱼不知道是服务器弱鸡还是视频流的代码写得太差，预加载总是出问题，而且官方并不提供下载选项，只能自己研究一下。

## 思路
利用url特征进行批量下载，最后进行合并。

## 工具
[Chrono Download Manager](https://chrome.google.com/webstore/detail/chrono-download-manager/mciiogijehkdemklbdcbfkefimifhecn/related?hl=en)， Chrome上的应用，用于批量下载，可以用迅雷或者其它具有相似的产品代替。

## 步骤
s1) 打开直播录像页面，右键空白处选择inspect(审阅)或者ctrl+shift+i进入审阅面板，在审阅面板的控制台中，右键复制流文件的地址，如图所示：
<img src="https://drive.google.com/uc?id=0B-N_s7wEHZ8LQ013bko2RUo3TFk" width="800">  

s2) 将复制的链接地址（如下）拷贝到记事本，011.ts即第一段视频的文件名  
http://vodhls1.douyucdn.cn/live/high_live-58428r0xXzzQWV0u--20170630180606/57fe3a8e89a844a3a87c655f9f270633_0000011.ts?k=20a37ea216a62d369a13f1e3451c3b7c&t=5956a23a&u=76864423&ct=web&vid=910885&d=F3ACF08AA9243811F2181E9CF02C7DB9  
将视频播放条拉到最末尾，同样的方法，获取最后一段视频的文件名，如下，可见719.ts即最后一段视频的文件名  
http://vodhls1.douyucdn.cn/live/high_live-58428r0xXzzQWV0u--20170630180606/57fe3a8e89a844a3a87c655f9f270633_0000719.ts?k=20a37ea216a62d369a13f1e3451c3b7c&t=5956a23a&u=76864423&ct=web&vid=910885&d=F3ACF08AA9243811F2181E9CF02C7DB9  
批文件的特征url可以表示为：  
http://vodhls1.douyucdn.cn/live/high_live-58428r0xXzzQWV0u--20170630180606/57fe3a8e89a844a3a87c655f9f270633_0000xxx.ts?k=20a37ea216a62d369a13f1e3451c3b7c&t=5956a23a&u=76864423&ct=web&vid=910885&d=F3ACF08AA9243811F2181E9CF02C7DB9  
其中xxx表示文件编号。  

s3) 打开Chrono Download Manager，点击上方的加号，在弹出的窗口上拷贝特征url，按照Chrono Download Manager的格式，将xxx换为[011:719]，如下  
http://vodhls1.douyucdn.cn/live/high_live-58428r0xXzzQWV0u--20170630180606/57fe3a8e89a844a3a87c655f9f270633_0000[011:719].ts?k=20a37ea216a62d369a13f1e3451c3b7c&t=5956a23a&u=76864423&ct=web&vid=910885&d=F3ACF08AA9243811F2181E9CF02C7DB9  
<img src="https://drive.google.com/uc?id=0B-N_s7wEHZ8LZDY0MkQyZFplejQ" width="400">  

其它的设置为默认,点击开始(start)即可。  

注意，对于每个文件chrome在任务开始时都会弹出另存为(save as)窗口询问保存位置，批量文件下载数目巨大时请在浏览器的设置->高级里设置默认下载位置并关闭下载前询问保存位置（Ask where to save each file before downloading）开关。  
<img src="https://drive.google.com/uc?id=0B-N_s7wEHZ8LS1JEanJVVWk2Vmc" width="600">  

s4) 下载完成后即可直接播放，或者将其合并成一个视频文件。  
合并方式一： 在视频文件所在目录Shift+右键选择在此处打开控制台，并输入  
~~~
copy/b *.ts filename.ts  
~~~

filename即合并后的文件名     

合并方式二：将本项目中的 合并.bat 复制到视频文件所在目录，双击运行即可  


