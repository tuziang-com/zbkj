# 正保会计网校刷课脚本


## 脚本

学习网站：正保会计网校 https://www.chinaacc.com/

脚本地址：[正保会计网校-刷课脚本][2]

## 教程

浏览器安装篡改猴插件后，打开[脚本安装地址][2]，进入后点击安装脚本，安装完成刷新你的学习网页就可以愉快使用了。

## 代学

注：如果需要代学，可以联系我微信yizhituziang或者QQ2422270452。

微信二维码：  
![微信二维码](https://www.tuziang.com/wx.jpg)

## 代码

关键代码分享：
```
    if (location.href.indexOf("courseware/") != -1) {
        setInterval(function () {
            var video = document.querySelector("video")
            if (video && video.ended) {
                let length = document.querySelectorAll("div.catalog > div > a").length
                let className = document.querySelectorAll("div.catalog > div > a")[length - 1].className
                if (className.indexOf("cur") != -1) {
                    // 当前是最后一个视频了，返回课程首页
                    location.href = 'https://jxjy.chinaacc.com/learningCenter'
                }

            }
        }, 1000)
    }

    // 在首页自动进入课程
    if (location.href.indexOf("/learningCenter") != -1) {
        var script = document.createElement("script");
        script.type = "text/javascript";
        script.src="https://cdn.jsdmirror.com/gh/MCCRNFC-SNLoong/LayuiCdn/layui-v2.6.8/layui.js";
        document.body.appendChild(script);


        let isSk = true
        let index
        setTimeout(function(){
            index = layer.confirm('3秒后将开始自动刷课，如需取消请点击取消按钮', {
                icon: 3
            }, function() {
                layer.msg('确定');
                layer.close(index);
            }, function() {
                layer.msg('取消');
                isSk=false
            });
        },2000)
        setTimeout(function(){
            layer.close(index);
            if(isSk){
                nextCourse()
                layer.msg('2s后窗口自动关闭');
                setTimeout(function(){
                    window.close()
                },2000)
            }
        },5000)
    }

    // 课程目录
    if(location.href.indexOf("courseware/Index/")!=-1) {
        setTimeout(function(){
            for(let i = 0;i < document.querySelectorAll("tbody > tr.bjqiehuan").length;i++) {
                let item = document.querySelectorAll("tbody > tr.bjqiehuan")[i]
                if(item.innerText.indexOf("已完成")!=-1) {
                    continue
                }
                document.querySelectorAll("tbody > tr.bjqiehuan")[i].querySelector("a").click()
            }
        },2000)
    }

    function nextCourse() {
        for (let i = 0; i < document.querySelectorAll("tr td.study_status").length; i++) {
            let item = document.querySelectorAll("tr td.study_status")[i]
            if (item.innerText.indexOf("开始学习") != -1 || item.innerText.indexOf("继续学习") != -1) {
                document.querySelectorAll("tr td.study_status a")[i].click()
                break
            }
        }
    }
```


  [1]: https://microsoftedge.microsoft.com/addons/detail/%E7%AF%A1%E6%94%B9%E7%8C%B4/iikmkjmpaadaobahmlepeloendndfphd?refid=bingshortanswersdownload
  [2]: https://greasyfork.org/zh-CN/scripts/403646-%E6%AD%A3%E4%BF%9D%E4%BC%9A%E8%AE%A1%E7%BD%91%E6%A0%A1%E5%88%B7%E8%AF%BE%E8%84%9A%E6%9C%AC
