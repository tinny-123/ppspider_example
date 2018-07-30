# ppspider example

## src/quickstart
演示了 @OnStart 装饰器的作用  
在爬虫系统启动后，立即执行一个任务  
任务行为：  
打开 http://www.baidu.com  
加载完成后， 获取并打印所有以 http 开头的连接  

## src/ontime
演示了 @OnTime 装饰器的作用  
在爬虫启动后根据 cron 表达式周期性执行任务  
这例子中仅仅是每个5秒钟打印一次时间  

## src/queue
演示了 @AddToQueue @FromQueue 装饰器的左右  
任务行为： 
系统启动后，抓取所有 http 开头的连接，通过 @AddToQueue 添加到 test 队列中  
@FromQueue 则从 test 队列中获取任务，并交由 printUrl 方法处理    

## src/puppeteerUtil
演示了 PuppeteerUtil 工具类中一些方法的使用方式  

## src/debug  
演示了注入js的调试方法  

## src/dataSave
演示了几种数据保存方案  
由于抓到的大部分数据都是json格式的，建议使用1，然后根据实际数据需求，
后续再转存到其他存储介质中  
1. 保存到本地文件中  
2. 上传到服务器  
3. 存入 mysql  
4. @TODO 添加到 mongodb     

## src/bilibili  
爬取B站视频信息和前几页评论（包括全部楼中楼）  

## src/qqMusic
抓取 qq 音乐的信息 和 前 config.commentPages 页的评论  

## src/twitter
抓取推特上一些主题相关的讨论以及用户信息    

这个例子中演示了 puppeteer 1.6.1 response 丢失的bug的处理方案  
通过 Network.responseReceived 监听 response  
通过 Network.getResponseBody 获取 reponse body  

修改 src/twitter/movies.ts 添加主题  
每行一个  
```
export const movies =
`
主题1
主题2
主题3
`.split("\n").map(item => item.trim()).filter(item => item.length > 0);
```
运行前需要修改的配置  
src/twitter/config.ts   
dev.puppeteer.args --proxy-server=ip:port 设置代理  
dev.twitter.commentMaxNum 一个主题最多抓取多少条评论  
