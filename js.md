# javaScript

## 数据类型

### 基本数据类型

- ### String

- ### Number

  NaN number类型表示非数字

  - a = Number(a)

    a=‘12’-----12

    a=‘’1qsaf'---NaN

    a='    '-----0

    a=true---1

    a=false--0

  - parseInt()

    将字符串中的数值型取值转换

    非字符串会先转字符串再转换

    parseInt(a,10)第二个参数是指定转换进制

  - parseFloat()

    

- ### boolean

  - Boolean()

    数字转Boolean非0即真，NaN也是false

    null 和undefined是false

    空串也是false

- ### Null

- ### Undefined

### 引用数据类型

- ### Object

## 运算符

### 自增自减  

前++后++ ，前--后--

### ！，&&，||

- #### !

--对一个值进行非运算

--所谓非运算就是值对布尔值进行取反操作

​    true变false  false变true

--如果对非布尔值进行取反操作，则会将其转换为布尔值，然后再取反

  可以为任意一个数据类型做两次！！即可转为布尔值

- #### &&

  --如果对非布尔值进行操作，则会先将其转换为布尔值，然后做做运算，饼干会原值

  --第一个值为false不会检查第二个值，

  --如 5 && 6 返回6， 2  && 0 返回0，  NaN && 1 返回NaN

- #### ||

  只要有一个true就返回true

  --如果第一个值为true直接返回第一个值

  --如果第一个值为false直接返回第二个值

### 比较运算符

非数值的情况

--对于非数值进行比较时，会将其转换为数字然后再比较

--如果符号两侧数值都是字符串，不会将其转换为数字进行比较

   而是会分别比较两个字符串的Unicode编码



## 数组

### slice

截取数组中的元素，并返回新的数组不会改变原数组

slice(1,3)  参数是数组的索引，可以为负值，负值表示倒数第几个元素

### splice

从指定位置删除元素，改变原数组，并将删除的元素返回

splice(1,2) 表示从索引1的位置删除2个元素，并返回别删除的元素

splice(1,2,'3','4') 表示从删除元素位置添加新的元素。

### concat()

连接数组，不影响原数组

### join

将数组中的元素转换为一个字符串

可以指定连接符

### reverse

数组翻转，直接修改原数组

### sort

排序，会影响原数组，按照Unicode编码进行排排序，对数值排序会有错误。

可以指定排序规则，可以使用回调函数

```js
arr.sort(function(a,b){
	//升序排序
	return a-b;
    //降序排序
    return b-a;
})
```



## 函数对象的方法

在调用函数时，浏览器会帮我们传递两个隐藏参数

this和arguments

---artuments是一个类数组对象，是封装实参的。

---arguments.length获取实参的长度。

---通过arguments[0]取出实参。

### call（）

函数对象的方法，通过函数对象来调用。

当对函数调用call() apply()都会调用函数。可以将一个对象指定为第一个参数，被传递的参数（对象）称谓函数执行时的this。

如：fun.call(obj,a,b)

### apply（）

apply()需要封装到数组中

如：fun.apply(obj,[a,b])

## 正则

手机号正则

```js
 var re = /^1[3-9][0-9]{9}$/
```

去除前后的空格

```js
var reg = /^\s+|\s$g/
result = str.replace(reg,"")
```



### split()

字符串的方法，可以传正则参数.

```js
        var str = 'a1b2D3d'
        res = str.split(/[a-z]/i)
        console.log(res)
        ["", "1", "2", "3", ""]
```

### serch()

字符串的方法，可以传正则参数。

```js
 var str = 'a b cd'
  // i 表示忽略大小写，返回查找到的第一个符合条件的索引位置
 res = str.search(/[A-z]/i)
```

### match()

字符串的方法，可以传正则参数。

提取字符串的内容并返回一个数组。

```js
var str = 'a b Dd' 
// ig 表示全局查找，返回所有符合元素的一个数组对象
res = str.match(/[A-z]d/ig)
```

### replace()

字符串的方法，可以传正则参数。

默认替换第一个。使用正则全局模式进行所有替换（删除）。

## 函数

call（）方法可以修改this，函数中都带有call方法，使用函数名.call()调用函数。传递的第一个参数是一个对象，此时的this是传递的对象。

## 回调函数

- 自己定义的

- 自己没有调用

- 最终执行了

  常见的回调函数 事件函数---定时函数---ajax ---生命周期函数

## 匿名函数

隐藏实现---不会污染外部命名空间

## 函数高级

prototype  原型对象

- 每个函数都有一个prototype对象。
- 每个prototype都有一个constructor属性，它指向函数对象。
- 显示原型和隐式原型
  1. 对象的隐式原型的值为其对应的构造函数的显示原型的值 

原型链

- 当访问一个对象的属性时现在自身属性找

- 对象属性没有,沿着__proto__链向上找，最终没找到返回undefined

- 读取属性时，在原型链中查找

- 设置对象属性时，不看原型链。

  ![1593962794(1)](C:\Users\Administrator\Desktop\1593962794(1).jpg)

## 事件

添加点击事件

```html
    <script>
        window.onload = function (){
            var btn = document.getElementById("btn")
            bind(btn,'click',function(){
                alert(this)
            })
        }
        function bind (obj,addevent,callback){
            if (obj.addEventListener){
                obj.addEventListener(addevent,callback,false)
            }else{
                obj.attachEvent('onclick',function(){
                    callback.call(obj)
                })
            }
            
        }
    </script>
    <button id="btn">点我</button>
```

# js高级

## 数据类型

### 基本数据类型

string

number

Boolean

null  ------定义并赋值了，值为null 

undefined------定义了为赋值

### 对象类型

object

array

function

内存 ；临时的存储空间

分配内存：生命变量、函数、创建对象时js引擎会分配一定大小的内存存放数据

内存、变量、数据之间的关系：内存存储数据，变量是内存的标识，通过变量获取内存地址中存储的数据

### 变量提升和函数声明提升

### 全局执行上下文---window

对全局数据进行预处理，var声明的变量为undefined 全局函数赋值fun this赋值为Window

### 函数执行上下文

函数执行之前创建函数

