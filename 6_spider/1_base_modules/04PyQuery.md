# PyQuery简介：
    强大又灵活的网页解析库。
    如果觉得正则写起来太麻烦，beautifulsoup语法难记。只要熟悉jquery，pyquery是很好的代替正则和beautifulsoup的选择。
# 安装：
pip install pyquery



字符串初始化：
    import requests
    response = requests.get(url)
    response.encoding = 'utf-8'
    
    from pyquery import PyQuery as pq 
    html = pq(response.text)
    print(html)     #html是一个pyquery对象，但打印出来是html文档

url初始化：
    html = pq(url="https://www.douban.com")

文件初始化：
    html = pq(filename='demo.html')



标签选择器：

    #获取标签
    html('p')                #获取所有p标签

    #嵌套选择
    html('p h1')             #选择p标签内的h1标签 ，有空格隔开 

    #获取多个元素
    for i in html('p').items():     #循环获取每一个p标签，需要items()方法
        print(i)   

    #获取文本
    html('p').text()         #打印所有p标签内的文本，不如p内嵌的p、h1~6的文本，但a之类的非文本标签的文本不会被打印。

    #获取html
    html('p').html()         #打印除了<p>内的所有内容</p>也就是除了<p>和</p>两个标签

    #获取属性值
    html('a').attr('href')   #打印a标签的href属性值



css选择器：
    html('#out.inner')        #没有空格隔开，说明不是嵌套选择，而是查找同时带有out和inner css属性值的标签。
    html('#outlook .inner')   #内嵌选择，类似标签的嵌套选择，需要空格隔开
    html('#outlook p')         #css选择器和标签选择器一起使用，表示选择id为outlook的标签内的p标签

DOM操作：
    addClass 和 removeClass：
        li = html('#out.inner')
        li = removeClass('.inner')     #把inner css属性值从example标签删除
        li.addClass('.inner')          #往example标签添加inner css属性值

    attr 和  css：
        li.attr('name','user')      # 若li标签没有name属性，则为li标签添加name='user'属性值，有的话则覆盖
        li.css('font-size','14px')  #若li没有font-size css属性值，则添加style="font-size:14px",有则覆盖

    remove： 
        p = html('p')
        p('h1').remove()    #删除p标签内的h1标签

        






        


     