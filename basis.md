# ***python_basis***

[TOC]

## *1，基本数据类型+运算符*

### *1.1，Number*

#### *1.1.1，int*

```
int(1.56), int(0.156), int(-1.56)
# 1, 0 ,-1
int(True), int(False)
# 1, 0
int(3+2j)
# TypeError: can't convert complex to int
```

#### *1.1.2，float*

```
float(3+2j)
# TypeError: can't convert complex to float
```

#### *1.1.3，bool*

```
bool(1), bool(1.56), bool(3+2j)
# True, True ,True
bool(), bool(''), bool([]), bool(()), bool({})
# False
```

#### *1.1.4，complex*

```
complex(1), complex(1.0), complex(True)
# 1+0j
```

### *1.2，String*

#### *1.2.1，定义*

单引号或双引号定义字符串

三引号定义字符串（支持换行符）

```
string = 'This is a sentence'
string = "This is a sentence"
string = '''This is a sentence'''
# 'This is a sentence'
```

#### *1.2.2，索引,切片*

正索引从0开始，负索引从-1开始

string[x:y:s​tep]，左闭右开，当y省略时左闭右闭，x,y,step均有默认参数

```
string = 'python'
string[0], string[-1]
# 'p','n'
string = 'python'
string[:], string[::], string[-1::-1], string[::-1]
# 'python', 'python', 'nohtyp', 'nohtyp'
string[5:3]
# ''
```

#### *1.2.3，转义*

反斜杠将字符转义

在字符串里想使用单引号或双引号

```
string = 'This\'s a sentence'
string = "This's a sentence"
# "This's a sentence"
```

在字符串里想使用反斜杠

```
string = r'D:\python\Anaconda'
string = 'D:\\python\\Anaconda'
#  'D:\\python\\Anaconda'
```

#### *1.2.4，拼接*

使用+，*拼接字符串，若字符串想与数字拼接，需要将数字转换为字符串

```
string = 'python'
string = string + str(3) + '.com'
# 'python3.com'
```

#### *1.2.5，输出*

‘{参数序号:控制格式}’.format(参数)

控制格式常用的：填充，对齐，千位分隔符，精度，类型

```
age = 22
"我的年龄是%d岁"%(age)
# '我的年龄是22岁'
year, month = 1999, 5
f"我的出生年{year}, 出生月{month}"
# '我的出生年1999,出生月5'

'{:d}'.format(25), '{:6d}'.format(25), '{:06d}'.format(25), '{:*<6d}'.format(25), '{:+>6d}'.format(25)
# '25', '    25', '000025', '25****', '++++25’
'{:f}'.format(25), '{:6.2f}'.format(25.34), '{:06.2f}'.format(25.34), '{:*<6.2f}'.format(25.34), '{:+>6.2f}'.format(25.34)
# '25.000000', ' 25.34', '025.34', '25.34*', '+25.34'
'{:%}'.format(0.25, 0.34)
# '25.000000%'
'{:e}'.format(31415926535)
# '3.141593e+10'
import datetime
now = datetime.datetime.now()
'{:%Y-%m-%d %H:%M:%S}'.format(now)
# '2022-02-15 21:32:52'
```

#### *1.2.6，方法*

##### *1.2.6.1，方法join*

**describe:**

向序列中添加某种字符串

**param:**

type x:sequence

**return:**

rtype : str

**example:**

```
string = '赵钱孙李周吴郑王'
','.join(string)
# '赵,钱,孙,李,周,吴,郑,王'
List = ['湖人', '勇士', '马刺']
'-'.join(List)
# '湖人-勇士-马刺'
```

##### *1.2.6.2，方法split*

**describe:**

分割字符串为列表

**param:**

type x:str

type y:int

**return:**

rtype :list

**example:**

```
string = 'python is a language'
string.split(' '), string.split(' ', 2)
# ['python', 'is', 'a', 'language'], ['python', 'is', 'a language']
```

##### *1.2.6.3，方法count*

**describe:**

统计字符串中某种子串的数量

**param:**

type x:str

type strat:int

type end:int

**return:**

rtype :int

**example:**

```
string = 'python'
string.count('t'), string.count('t', 1, 3)
# 1, 1（前2-3个字符串）
```

##### *1.2.6.4，方法index,find,rindex,rfind*

**describe:**

查找字符串中某种子串的首次出现或最后出现的索引

**param:**

type x:str

type strat:int

type end:int

**return:**

rtype :int

**example:**

```
string = 'python'
string.index('t'), string.find('t', 1, 3), string.rindex('t'), string.rfind('t', 1, 3)
# 2, 2，2，2
```

##### *1.2.6.5，方法isdigit,isalpha,isalnum,isupper,islower*

**example:**

```
'123.4'.isdigit(),'123'.isdigit(), 'abc'.isalpha(), '123abc'.isalnum(), 'ABc'.isupper(), 'ABc'.islower()
# False, True, True, True, False, False
```

##### *1.2.6.6，方法upper,lower*

**example:**

```
string = 'Python'
string.upper(), string.lower()
# 'PYTHON', 'python'
```

##### *1.2.6.7，方法startswith,endswith*

**describe:**

验证字符串是否以某子串开头或结尾

**param:**

type x:str

type strat:int

type end:int

**return:**

rtype :bool

**example:**

```
string = 'python is a language'
string.startswith('py', 0, 2), string.startswith('py', 0, 1),  string.endswith('ge')
# True, False（前1个字符）, True
```

##### *1.2.6.8，方法strip,lstrip,rstrip*

**describe:**

去除字符串中开头结尾的空格或特殊字符

**param:**

type x:str

**return:**

rtype :str

**example:**

```
string = ' python '
string.strip(' '), string.lstrip(' '), string.rstrip(' ')
# 'python', 'python ', ' python'
```

##### *1.2.6.9，方法replace*

**describe:**

替换字符串的子串

**param:**

type x:str

type y:str

**return:**

rtype :str

**example:**

```
string = 'python'
string.replace('p', 'P')
# 'Python'
```

##### *1.2.6.10，方法center,ljust,rjust*

**describe:**

将字符串对齐填充

**param:**

type x:int

type y:str

**return:**

rtype :str

**example:**

```
string = 'python'
string.center(10, '-'), string.ljust(10, '-'), string.rjust(10, '-')
# '--python--', 'python----', '----python'
```

##### *1.2.6.11，方法zfill*

**describe:**

字符串前面填充0，建立编号

**param:**

type x:int

**return:**

rtype :str

**example:**

```
name = ['huawei', 'xiaomi', 'vivo']
for i in range(len(name)):
    print(str(i+1).zfill(3), name[i])
# 001 huawei
# 002 xiaomi
# 003 vivo
```

### *1.3，List*

#### *1.3.1，定义*

用[]定义列表

用list()定义列表

```
List = ['华为', '小米', 'vivo']
list(1.2)
# TypeError: 'float' object is not iterable
list('python'), list((1, 2)), list({'python': 1, 'java': 2}), list({1, 2, 3, 4})
# ['p', 'y', 't', 'h', 'o', 'n'], [1, 2], ['python', 'java'], [1, 2, 3, 4]
```

#### *1.3.2，索引,切片*

见1.2.2

#### *1.3.3，拼接*

见1.2.4

#### *1.3.4，输出*

借助enumerate()遍历输出列表的序号和值

```
List = ['huawei', 'xiaomi', 'vivo']
for index, item in enumerate(List, start=0):
    print('索引:%d,值:%s' % (index, item))
# 索引:0,值:huawei
# 索引:1,值:xiaomi
# 索引:2,值:vivo
```

#### *1.3.5，推导式*

```
[i**2 for i in range(10) if i % 2 == 0]
# [0, 4, 16, 36, 64]
```

#### *1.3.6，方法*

##### *1.3.6.1，方法append,insert,extend*

**describe:**

列表的增加：末尾单个增加，特定位置单个增加，序列增加

**param:**

type x:unkonwn

type x:int

type y:unknown

type x:sequence

**return:**

rtype :list

**example:**

```
List = ['华为', '小米', 'vivo']
List.append('OPPO')
# ['华为', '小米', 'vivo', 'OPPO']
List.insert(1, '联想')
# ['华为', '联想', '小米', 'vivo', 'OPPO']
List.extend(['中兴', '魅族'])
#  ['华为', '联想', '小米', 'vivo', 'OPPO', '中兴', '魅族']
List.extend({'锤子': '手机'})
# ['华为', '联想', '小米', 'vivo', 'OPPO', '中兴', '魅族', '锤子']
```

##### *1.3.6.2，方法pop,remove*

**describe:**

列表的删除：按索引删除，按值删除

**param:**

type x:int

type x:unknown

**return:**

rtype :list

**example:**

```
List = ['华为', '小米', 'vivo']
List.pop(), List.pop(-1), List.remove('小米')
# ['华为', '小米'], ['华为', '小米'], ['华为', 'vivo']
```

##### *1.3.6.3，方法count,index*

**example:**

```
List = ['华为', '小米', 'vivo', '华为']
List.count('华为'), List.index('华为')
# 2, 0
```

##### *1.3.6.4，方法sort,reverse*

**example:**

```
List = ['huawei', 'xiaomi', 'vivo']
List.sort(), List.sort(reverse=True)
# ['huawei', 'vivo', 'xiaomi'], ['xiaomi', 'vivo', 'huawei']
List.reverse()
# ['vivo', 'xiaomi', 'huawei']
```

### *1.4，Tuple*

#### *1.4.1，定义*

用()定义元组

用tuple()定义元组

```
Tuple = ('华为', '小米', 'vivo')
Tuple = 1.2,
# (1.2,)
tuple(1.2)
# TypeError: 'float' object is not iterable
tuple('python'), tuple([1, 2]), tuple({'python': 1, 'java': 2}), tuple({1, 2, 3, 4})
# ('p', 'y', 't', 'h', 'o', 'n'), (1, 2), ('python', 'java'), (1, 2, 3, 4)
```

#### *1.4.2，索引,切片*

见1.3.2

#### *1.4.3，拼接*

见1.3.3

#### *1.4.4，输出*

见1.3.4

#### *1.4.5，推导式*

见1.3.5

#### *1.4.6，方法count,index*

**example:**

```
Tuple = ('华为', '小米', 'vivo', '华为')
Tuple.count('华为'), Tuple.index('华为')
# 2, 0
```

### *1.5，Dictionary*

#### *1.5.1，定义*

键值对中键不可变数据类型且不可重复，值可变数据类型且可重复。

用{}定义字典

用dict()定义字典

```
Dict = {'username': '1234567890', 'password': 666, 'password': 333}
# {'username': '1234567890', 'password': 333}
Dict = dict(['12', [3, 4], (5, 6), {7, 8}])
# {'1': '2', 3: 4, 5: 6, 8: 7}
Dict = dict(('12', [3, 4], (5, 6), {7, 8}))
# {'1': '2', 3: 4, 5: 6, 8: 7}
Dict = dict(one=1, two=2)
# {'one': 1, 'two': 2}
```

#### *1.5.2，访问*

Dict.items()	访问键值对

Dict.keys()	  访问键

Dict.values()   访问元素

```
Dict = {'username': '1234567890', 'password': 666, 'password': 333}
Dict.items(), Dict.keys(), Dict.values()
# [('username', '1234567890'), ('password', 333)], ['username', 'password'], ['1234567890', 333]
Dict['username']
# '1234567890'
```

#### *1.5.3，输出*

```
Dict = {'username': '1234567890', 'password': 666, 'password': 333}
for key, value in Dict.items():
    print(key, ':', value)
# username : 1234567890
# password : 333
```

#### *1.5.4，增加*

```
Dict = {'username': '1234567890', 'password': 666, 'password': 333}
Dict['vcode'] = 'qwas'
# {'username': '1234567890', 'password': 333, 'vcode': 'qwas'}
```

#### *1.5.5，删除*

```
Dict = {'username': '1234567890', 'password': 666, 'password': 333, 'vcode': 'qwas'}
Dict.pop('vcode')
# {'username': '1234567890', 'password': 333}
```

### *1.6，Set*

#### *1.6.1，定义*

用{}定义可变集合

用set()定义可变集合

用frozenset()定义不可变集合

集合可看成仅存在键的字典，即集合的元素不可变数据类型且不可重复

```
Set = {3, 2, 1, 4, 4}
# {1, 2, 3, 4}
Set = set(1.2)
# TypeError: 'float' object is not iterable
Set = set('123')
# {'1', '2', '3'}
Set = set([1, 2, 3])
# {1, 2, 3}
Set = set((1, 2, 3))
# {1, 2, 3}
Set = set({'username': '1234567890'})
# {'username'}
```

#### *1.6.2，访问*

由于集合中元素无序，暂时不知怎么访问

#### *1.6.3，输出*

由于集合中元素无序，暂时不知怎么输出

#### *1.6.4，增加*

```
Set = {1, 2, 3}
Set.update({4, 5, 6})
# {1, 2, 3, 4, 5, 6}
```

#### *1.6.5，删除*

pop随即删除，remove按值删除

```
Set = {1, 2, 3}
Set.pop(), Set.remove(2)
# {2, 3}, {1, 3}
```

#### *1.6.6，关系*

子集，真子集，相等

```
Set = {1, 2, 3}
Set2 = {1, 2, 3, 4}
Set <= Set2, Set < Set2, Set == Set2
# True, True, False
```

#### *1.6.7，运算*

差，对立，并，交

```
Set = {1, 2, 3}
Set2 = {1, 2, 3, 4}
Set - Set2, Set | Set2, Set & Set2
# set(), {1, 2, 3, 4}, {1, 2, 3}
```

### *1.7，运算符*

#### *1.7.1，算术运算符*

+，-，*，/，%，**，//

#### *1.7.2，关系运算符*

```
>，>=，<，<=，==，!=
```

#### *1.7.3，逻辑运算符*

and	or	not

x and y 若x为False，返回x的值，否则返回y的值

x or y 若x为True，返回x的值，否则返回y的值

not x 若x为True,返回False，否则返回True

#### *1.7.4，赋值运算符*

=，+=，-=，*=，/=，%=，**=，//=

#### *1.7.5，按位元素符*

&，|，~，^，<<，>>

#### *1.7.6，成员元素符*

in	not in

#### *1.7.7，身份元素符*

is	not is

## *2，表达式*

当表达式中含多个运算符时，要关注运算符的优先级与结合性，但加括号就可解决。

### *2.1，算数表达式*

**example:**

```
1+2, 1-2, 1*2, 1/2, 1%2, 1**2, 1//2
# 3, -1, 2, 0.5, 1, 1, 0
```

### *2.2，关系表达式*

**example:**

```
1>2, 1>=2, 1<2, 1<=2, 1==2, 1!=2
# False, False, True, True, False, True
```

### *2.3，逻辑表达式*

**example:**

```
10 and 20, 10 or 20, not 10
# 20, 10, False
```

### *2.4，赋值表达式*

**example:**

```
a = 2
a **= 2
# 4
```

### *2.5，按位表达式*

**example:**

```
1 & 1, 1 | 1, ~1,
# 1, 1, -2(1的补码为0000 0001；按位取反后补码 1111 1110；对应原码1000 0010）
1^1, 1<<2, 1>>2
# 0, 4, 0
```

### *2.6，成员表达式*

**example:**

```
'1' in 'python1', 1 in [1, 2, 3, 4], 1 in (1, 2, 3, 4)
# True, True, True
```

### *2.7，身份表达式*

**example:**

```
a, b, c, d = 1, 1, 2, 3
a is b, c is d
# True, False
```

## *3，流程控制语句*

### *3.1，条件语句*

if 布尔表达式1：

​		程序段1

elif 布尔表达式2：

​		程序段2

else:

​		程序段3

### *3.2，循环语句*

for    :

​		程序段

while 布尔表达式：

​		程序段

break为跳出本层循环，continue为跳出本次循环，pass为占位语句

### *3.3，实例：冒泡排序*

```
a = [1, 2, 3, 5, 6, 7, 4]
for i in range(1, len(a)):         # 趟数
    for j in range(len(a)-i):      # 每躺比较次数
        if a[j] > a[j+1]:
            a[j], a[j+1] = a[j+1], a[j]
a
# [1, 2, 3, 4, 5, 6, 7]
```

## *4，函数+类*

### *4.1，作用*

​		在程序中，同一段代码会被重复使用，如果程序由一段冗余的流程控制语句组成，那么程序的可读性会变差，这时候可以使用函数来封装这些重复利用的程序段，并加以注释，用的时候直接调用，可以使代码更清晰。当然也可以使用类来封装，类比函数更灵活，不仅把对象的操作(方法）进行了封装，还把对象的属性（变量）也进行了封装。
值得注意的是，封装伴随着隐藏，就是对外部用户隐藏了操作的内部实现细节，比如拿列表的排序操作来说，sorted(),外部用户只需掌握函数的三要素：函数功能-输入-输出（有例子更好）就可实现排序，而不用在意内部到底是利用直接排序法还是希尔排序法。

​		C语言中只有函数，JAVA中只有方法，C++与Python的函数与方法在于是否在类中定义的，比如python中的方法和函数均是用关键字def定义的，但方法是在类里使用，并且第一个参数按照惯例是self（代表对象的地址）。

### *4.2，区别*

面向过程程序设计（结构化程序设计）思路：分析出解决问题需要的步骤，用函数实现每一个步骤，以步骤划分问题。
面向对象程序设计思路：将构成问题的事物分解成各个对象，描述各个对象的行为，以功能划分问题。
拿五子棋为例：
开始游戏->黑子先走->绘制画面->判断输赢->白子再走->绘制画面->判断输赢->重复过程
问题分为三个对象，棋子（黑白双方）-棋盘-规则

### *4.3，函数*

#### *4.3.1，定义*

##### *内部函数(68)：*

###### *1，函数int,float,bool,complex,str,list,tuple,dict,set*

###### *2，函数chr,ord*

**example:**

```
chr(48), chr(65), chr(97), ord('0'), ord('A'), ord('a')
# '0', 'A', 'a', 48, 65, 97
```

###### *3，函数bin,oct,hex*

**example:**

```
bin(11), oct(11), hex(11)
# '0b1011', '0o13', '0xb'
```

###### *4，函数max,min,sum,abs,round*

**example:**

```
max([1, 2, 3, 4]), min([1, 2, 3, 4]), sum([1, 2, 3, 4])
# 4, 1, 10
abs(-10), abs(10+1j), round(3.14)
# 10, 10.04987562112089, 3
```

###### *5，函数print,input*

是什么类型，print什么类型；无论什么类型，input字符串类型

###### *6，函数len,sorted,reversed*

**example:**

```
List = [1, 4, 3, 2]
len(List), sorted(List), sorted(List, reverse=True), reversed(List)
# 4, [1, 2, 3, 4], [4, 3, 2, 1], <list_reverseiterator at 0x2fb2dab9f88>
```

###### *7，函数map*

**describe:**

对序列的元素做相同的操作

**param:**

type x: function

type y: sequence

**return:**

rtype : sequence

**example:**

```
List = list(map(lambda x: x+2, [1, 2, 3, 4]))
# [3, 4, 5, 6]
```

###### *8，函数filter*

**describe:**

对序列的元素做相同的过滤操作，结果为False的过滤掉(结果为True的留下)

**param:**

type x: function

type y: sequence

**return:**

rtype : sequence

**example:**

```
List = list(filter(lambda x: x != 1, [1, 2, 3, 4]))
# [2, 3, 4]
```

###### *9，函数zip*

**describe:**

将可迭代对象打包为元组，返回由这些元组组成的列表

**param:**

type x: iterable

type y: iterable

**return:**

rtype : list

**example:**

```
List1 = [1, 2, 3, 4, 5, 6]
List2 = ['醉乡民谣', '驴得水', '放牛班的春天', '美丽人生', '辩护人', '被嫌弃的松子的一生']
List3 = ['美国', '中国', '法国', '意大利', '韩国', '日本']
List = list(zip(List1, List2, List3))
# [(1, '醉乡民谣', '美国'),
#  (2, '驴得水', '中国'),
#  (3, '放牛班的春天', '法国'),
#  (4, '美丽人生', '意大利'),
#  (5, '辩护人', '韩国'),
#  (6, '被嫌弃的松子的一生', '日本')]
```

###### *10，函数all,any*

迭代对象中全为True结果为True；迭代对象中有一个为True结果为True。

**example：**

```
all([0, 1, 2, 3, 4]), any([0, 1, 2, 3, 4])
# False, True
```

###### *11，函数eval*

执行字符串表达式

**example：**

```
eval('2019+1'), type(eval('2019+1'))
# 2020, int
```

###### *12，函数id,type,open*

##### *模块中的函数*

```
import random
print(random.random())
# 0.15628513706961977
```

##### *自定义函数*

```
def 函数名(参数列表):
   """
   :describe: 
   :param 参数列表: 
   :return: 
   :example:
   """
```

##### *匿名函数*

使用lambda语句创建匿名函数

```
sum=lambda x, y: x+y       # 将lambda语句作为对象赋值给变量
sum(1, 2)                  # 使用变量名进行调用
# 3
```

#### *4.3.2，参数*

参数分为位置参数，关键字参数，默认参数，可变参数

位置参数很好理解，输入参数时按顺序输入,在默认参数之前

关键字参数可以不按顺序输入，必须放在位置参数之后

默认参数是在定义函数的同时直接定义变量取值
（对开发者可以设置期望的”最好“默认值如range(10),默认start=0，step=1,对用户可以避免初次使用遇到一大堆参数设置的窘境）

加了*的参数会以元组的形式导入，传入的参数不能为关键字参数
加了**的参数会以字典的形式导入，传入的参数需要为关键字参数

```
def printinfo(name,age=18):
    print("名字:", name)
    print("年龄:", age)
    return
printinfo('runoob', 19)
printinfo(age=50, name="runoob")
# 名字: runoob
# 年龄: 50

def printinfo(arg,*args):
    print(arg)
    print(args)
    return
printinfo(70,60,50)
# 70
# (60, 50)

def printinfo(arg,**args):
    print(arg)
    print(args)
    return
printinfo(1,a=2,b=3)
# 1
# {'a': 2, 'b': 3}
```

#### *4.3.3，嵌套*

外部函数返回时要调用内部函数

```
def mean(*args):
    def sum(x):
        sum1 = 0
        for i in x:
            sum1 += i
        return sum1
    return sum(args)/len(args)  
```

#### *4.3.4，变量作用域*

函数体内定义的变量为局部变量，对该变量的操作仅限于函数体内，全局变量在函数体内不能被修改，当局部变量与全局变量同时存在时，全局变量会被覆盖。

```
# 报错
sum1 = 10
def sum(x):
    for i in x:
        sum1 += i
    return sum1

# 覆盖
sum1 = 10
def sum(x):
    sum1 = 0
    for i in x:
        sum1 += i
    return sum1
```

### *4.4，类*

#### *4.4.1，封装*

class 类名（大写）：
    

​		属性(私有属性前加双下划线)
​    

​		方法(私有方法前加双下划线)

构造方法可以无参，但有参的构造方法初始化对象属性

私有属性对象不能直接操作，但可以通过提供的方法接口进行访问

```
class Cat:
    def __init__(self, name, age):
        self.__name = name
        self.age = age
    def sleep(self):
        print(f"{self.age}岁的{self.__name}正在沙发上睡懒觉")
    def eat(self, food):
        self.food = food
        print(f"{self.age}岁的{self.__name}在吃{self.food}")
cat1 = Cat('Tom', 18)
```

#### *4.4.2，继承*

子类只能继承基类的公有属性与方法

```
class Cat():
    def __init__(self, name):
        self.name = name
class Bosi(Cat):
    def __init__(self, name):
        Cat.__init__(self, name) 
bs = Bosi('cat')
```

#### *4.4.3，多态*

类比java

## *5，模块：包含所有定义的函数和变量的文件，后缀名为.py*

### *5.1，random*

#### *5.1.1，random*

**describe:**

生成[0,1)的浮点数

**param:**

无

**return：**

rtype : float

**example:**

```
import random
print(random.random())
# 0.15628513706961977
print(random.random())
# 0.6573823354103464
```

#### *5.1.2，uniform*

**describe:**

生成[x,y]的浮点数

**param:**

type x:float

type y:float

**return：**

rtype:float

**example:**

```
import random
print(random.uniform(1, 2))
# 1.2983525790317427
print(random.uniform(3.2, 3.5))
# 3.2695741706322905
```

#### *5.1.3，randint*

**describe:**

生成[x,y]的整数

**param:**

type x:int

type y:int

**return：**

rtype :int

**example:**

```
import random
print(random.randint(1, 2))
# 1
print(random.randint(1, 5))
# 5
```

#### *5.1.4，randrange*

**describe:**

生成[x,y)的整数

**param:**

type x:int

type y:int

type step:int

**return：**

rtype :int

**example:**

```
import random
print(random.randrange(10))
# 5
print(random.randrange(1, 10, 2))
# 7
```

#### *5.1.5，choice*

**describe:**

序列中选单个

**param:**

type x:sequence

**return：**

rtype:unknown

**example:**

```
import random
print(random.choice([1, 2, 3, 4, 5]))
# 1
```

#### *5.1.6，sample*

**describe:**

序列中选多个

**param:**

type x:sequence

type y:int

**return：**

rtype :unknown

**example:**

```
import random
print(random.sample([1, 2, 3, 4, 5], 3))
# [5, 1, 2]
```

#### *5.1.7，shuffle*

**describe:**

将序列元素打乱

**param:**

type x:sequence

**return：**

rtype :None

**example:**

```
import random
seq = [1, 2, 3, 4, 5]
random.shuffle(seq)
print(seq)
# [1, 5, 2, 3, 4]
```

#### *5.1.8，seed*

**describe:**

设置随机数生成器种子以使生成的随机数一样，默认使用系统时间作为种子

**param:**

type x:unknown

**return：**

rtype :None

**example:**

```
import random
random.seed()
print(random.random())
# 0.48180033014249213
random.seed()
print(random.random())
# 0.7787908806043612

random.seed(2)
print(random.random())
# 0.9560342718892494
random.seed(2)
print(random.random())
# 0.9560342718892494
```

### *5.2，math*

math.ceil()  向上取整

math.floor() 向下取整

math.exp(x)  返回e^x

math.log(x)  返回lnx

math.log10(x)返回lgx

math.sqrt(x) 返回根x

math.sin(x)     弧度

math.asin(x)    数字

math.pi,math.e    

### *5.3，os*

```
import os
path1 = os.path.abspath('.')    # 当前文件夹的绝对路径
# D:\8文档\4Python\2DP\basis\code
path2 = os.path.abspath('..')   # 当前文件夹的上一级文件夹的绝对路径
# D:\8文档\4Python\2DP\basis
```

### *5.4，Json*

JSON 指的是 JavaScript 对象表示法（JavaScript Object Notation）。

#### *5.4.1，dump*

**describe:**

将基本类型数据转换为Json格式字符串后写入文件

**param:**

type x: unknown

type y: fp

**return：**

rtype :None

**example:**

```
import json
with open('..\data\mr.json', 'w') as f:
    json.dump({'a': '123', 'b': '456'}, f, ensure_ascii=False)    # ensure_ascii=False后中文正常显示
# {'a': '123', 'b': '456'}

import json
with open('..\data\mr.json', 'w') as f:
    json.dump(['ID', [1, 2, 3], {'b': '456'}], f, ensure_ascii=False)
# ["ID", [1, 2, 3], {"b": "456"}]
```

#### *5.4.2，load*

**describe:**

读取json文件返回为基本类型数据

**param:**

type x: f

**return：**

rtype : unknown

**example:**

```
import json
with open('../data/mr.json') as f:
    data = json.load(f)
type(data)
# <class 'list'>
```

#### *5.4.3，dumps*

**describe:**

将基本类型数据转换为Json格式字符串

**param:**

type x: unknown

**return：**

rtype : str

**example:**

```
import json
data = json.dumps(['ID', [1, 2, 3], {'b': '456'}], ensure_ascii=False)
type(data)
# <class 'str'>
```

#### *5.4.4，loads*

**describe:**

将Json格式字符串转换为基本类型数据

**param:**

type x: str

**return：**

rtype : unknown

**example:**

```
data = json.loads(data)
type(data)
# <class 'list'>
```

### *5.5，datetime*

#### *5.5.1，datetime.now,datetime.combine*

获取本地当前日期时间

将日期，时间对象合并为日期时间对象

**example:**

```
import datetime
data = datetime.datetime.now()
data.date(), data.time()
datetime.datetime.combine(data.date(), data.time())
# datetime.datetime(2022, 2, 15, 17, 58, 45, 534354)
# datetime.date(2022, 2, 15), datetime.time(17, 58, 45, 534354)
# datetime.datetime(2022, 2, 15, 17, 58, 45, 534354)
```

#### *5.5.2，datetime,date,time*

创建日期时间，日期，时间

**example:**

```
import datetime
datetime.datetime(2022, 2, 15, 17, 58, 45, 534354)
# datetime.datetime(2022, 2, 15, 17, 58, 45, 534354)
datetime.date(2022, 2, 15), datetime.time(17, 58, 45, 534354)
# datetime.date(2022, 2, 15), datetime.time(17, 58, 45, 534354)
```

#### *5.5.3，datetime.strptime*

**describe:**

将日期时间字符串转换为日期时间对象

**param:**

type x: str

type y: str

**return：**

rtype : datetime.datetime

**example:**

```
import datetime
datetime.datetime.strptime('2022/2/15 18:04', '%Y/%m/%d %H:%M')
# datetime.datetime(2022, 2, 15, 18, 04)
```

## *6，包*

sound/   顶层包

 		 _init_.py  目录只有包含该文件才被认为是一个包

  		formats/  子包1

​      				_init_.py

​     			 	wavread.py

​     			 	wavwrite.py

  		effects/  子包2

​     			 	_init_.py

​     			 	echo.py

​      				surround.py

导入echo模块：

一是 import sound.effects.echo as ec

二是 from sound.effects import echo 

导入模块中的函数

一是import 模块名  模块名.函数名

二是from 模块名 import 函数名 函数名

## *7，其他*

### *7.1，好的编程习惯：声明编码与路径*

```
# -*-coding:utf-8-*-
# !D:\python\Anaconda 
```

### *7.2，变量的命名*

（1）要是标识符

（2）不能是保留字（关键字）

（3）不能是内置函数名

（4）风格有大驼峰，小驼峰，下划线分割

```
import keyword
print(keyword.kwlist)

['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

### *7.3，变量的赋值*

多变量赋单值：x=y=z=1

多变量同时赋值：x,y,z=1,2,3

变量之间的赋值传递的是地址：id(x)=id(y)=id(z)

### *7.4，常见错误*

#### *7.4.1，AttributeError属性错误*

'module' object has no attribute 'xxx'，可能由于模块名与文件名一致

'Obj' object has no attribute 'attr'，可能内置对象没有属性

#### *7.4.2，IndentationError缩进错误*

expected an indented block，没有缩进

unexpected indent，缩进多了

unindent does not match any outer indentation level，缩进不一致

#### *7.4.3，IndexError索引错误* 

list index out of range，列表下标越界

string index out of range，字符串下标越界

#### *7.4.4，SyntaxError语法错误*

invalid syntax，无效的语法

invalid character in identifier，标识符中出现无效字符

non-default argument follows default argument，参数定义顺序错误

#### *7.4.5，TypeError类型错误*

can only concatenate str (not "XXX") to str，字符串只与字符串拼接

f() takes exactly 2 arguments(1 given)，参数传递不够

'tuple' object does not support item assignment，元组类型不能修改

#### *7.4.6，NameError名称错误*

name 'test' is not defined，变量没有定义或python3版本不支持python2中的某些函数或方法

#### *7.4.7，ValueError值错误*

could not convert string to float:'12.2月'，不能将字符串转换为浮点型

invalid literal for int() with base 10，传入无效的参数

#### *7.4.8，KeyError键错误*

‘age'，可能由于键不存在

### *7.5，文件*

计算机文件：以计算机磁盘为载体存储在计算机上的信息集合

with语句可以很好地处理上下文环境中产生的异常

encoding参数可以指定某种特定编码的文件

#### *7.5.1，读文本文件*

f.read()读取整个文件内容存储在一个字符串变量

f.readlines()按行读取整个文件内容存储在一个字符串组成的列表

#### *7.5.2，写文本文件*

f.write('字符串')

#### *7.5.3，读csv文件*

```
import csv
with open('..\data\iris.csv', 'r', encoding='utf-8') as f:
    text = csv.reader(f)
    for i in text:
        print(i)
# ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'target']
# ['5.1', '3.5', '1.4', '0.2', '0']
# ['4.9', '3.0', '1.4', '0.2', '0']
# ['4.7', '3.2', '1.3', '0.2', '0']
# ['4.6', '3.1', '1.5', '0.2', '0']
# ['5.0', '3.6', '1.4', '0.2', '0']
```

#### *7.5.4，写csv文件*

```
import csv
with open('..\data\iris1.csv', 'w', encoding='utf-8', newline='') as f:
    write = csv.writer(f)
    write.writerows(text)
```

读写csv文件相比于读写文本文件多了两行，csv.reader(f)与csv.writer(f)。

