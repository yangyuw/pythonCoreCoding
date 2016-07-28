# 第2章 python起步
### 列表解析

```python
[x**2 for x in range(10)]
```
# 第3章 python基础
- **除了真正需要执行的代码以外,几乎所有的功能代码都在函数中.**  
- python是一种解释型语言,在赋值时,解释器会根据右侧的操作数来决定新对象的类型,在对象创建后,一个该对象的引用会被赋值给左侧的变量.  
### 引用计数
- 在对象被创建,或另外的别名被创建,或被作为参数传递给函数,或成为容器对象的一个元素时, 引用计数增加  
- 在本地引用离开了其作用范围时,或对象的别名被显式销毁,或对象的别名被赋值给其他的对象,或对象被从一个窗口对象中移除,或窗口被对象本身销毁(del mylist) 时, 引用计数减少  
- del x 可以删除对象的一个引用
### 第一个python程序  
- ls = os.linesep(换行符)为属性取别名可以缩短变量名和改善访问该变量的性能.  
# 第4章 python对象  

- python使用对象模型来存储数据.构造任何类型的值都是一个对象 
- 所有的python对象都有三个特性:身份,类型和值
- is 用来比较两个变量是否指向同一个对象
- python仅缓存简单整数(-255到256)
- cmp()用来比较两个对象obj1和obj2, 如果obj1<obj2,返回负整数,否则返回正整数,如果相等返回0
- eval()可以把字符串当做表达式来求值
- repr()可以把python的**变量和表达式**转换为字符

### 工厂函数

- 工厂函数看上去像函数,实质上他们是类,当你调用它们时,实质上是生成了该类的一个实例,就像工厂生产货物一样.

### 标准类型分类

##### 存储模型

标量/原子类型: 数值,字符串

容器类型: list, tuple, dict

##### ID可变模型

| 可变类型 | 不可变类型  |
| ---- | ------ |
| list | int    |
| dict | string |
|      | tuple  |

- list ,dict的值无论怎么变, ID始终不变
- int,tuple,string的值改变, id会改变

##### 访问模型

- 直接访问: int
- 顺序访问: string, list, tuple
- 映射访问: dict


# 第5章 数字

### 数字类型

- python支持 整型,长整型,布尔型,双精度浮点型,十进制浮点型和复数.
- 删除对象用del()

### 整型

- 用L表示长整型(避免和1混淆)

### 双精度浮点数

- 浮点数值通常都有一个小数点和一个可选的后缀e

### 复数

- 虚数: j = √-1
- 复数是一对有序浮点数(x, y)  x是实数部分, y是虚数部分. 4.213+ 1j    0.23-8.33j

##### 复数属性

| 属性              | 描述                    |
| :-------------- | --------------------- |
| num.real        | 该复数的实部                |
| num.imag        | 该复数的虚部                |
| num.conjugate() | 返回该复数的共轭复数(实部相等虚部相反数) |

### 除法

- ```1 / 2``` # 0
- ```1.0 / 2.0``` # 0.5


- 地板除: ```5 // 2``` # 2

### 幂运算

- ``` -3 ** 2``` #  -9

### 内建函数

- abs()返回给定参数的绝对值
- coerce()返回一个包含类型转换完毕的两个数值元素的tuple.  coerce(1.3, 134L)  # (1.3L, 134L)
- divmod()把除法和取余结合起来,返回包含商和余数的tuple.
- pow()和 ** 都是指数运算.
- round()对浮点数进行四舍五入运算, 第二个参数代表函数将结果精确到小数点后指定位数.

# 第6章 序列: 字符串, 列表和元组

> 成员有序排列的, 并且可以通过下标偏移量访问到它的一个或者几个成员, 这种python类型称为序列

### 序列

| 序列操作符              | 作用                      |
| ------------------ | ----------------------- |
| seq[index]         | 获得下标为index的元素           |
| seq[index1:index2] | 获得下标从index1到index2的元素集合 |
| seq * expr         | 序列重复expr次               |
| seq1 + seq2        | 连接序列seq1 和 seq2         |
| obj in seq         | 判断obj元素是否在seq中          |
| obj not in seq     | 判断obj元素是否不包含在seq        |

### 字符串

- 字符串是不可改变的,不能仅仅删除或者改变一个字符串里的某个字符.

### 字符串和操作符

- 在做比较操作的时候, 字符串是按照ASCII的值得大小来比较的.
- join('str1', 'str2')用于连接字符串

### 原始字符串

- 为了对付那些在字符串中出现的特殊字符. print r'\n'


- 三引号 "' hi \n'" 保存字符串中的特殊字符
- 字符串不变性: 为了修改字符串, 我们需要用现有字符串的子串来构建一个新串 s = '%sC%s' % (s[0:2], s[3:])

### 列表

- 更新列表的值: 通过指定索引, 或者用append()追加元素
- 删除列表的值: del aList[1]  或者 aList.remove(123)

### 元组

- **只有一个元素**的元组需要加(,) 防止跟普通的分组操作符混淆


- **不可变性** : 我们把数据传给不了解的API时, 可以确保我们的数据不会被修改.
- **""可变性"** : 可以修改元组里面列表的值, 元组的ID不变

### 浅拷贝

- 因为数组是可变的, 所以在修改一个引用数组变量的变量的时候, 原变量的值是会被改变的
- 元组即便是调用copy()模块也只能进行浅拷贝

# 第7章 映射和集合类型

> 字典是python中唯一的映射类型

### 字典

- 哈希表是一种数据结构: 键值对.哈希表一般有很好的性能, 因为用键查询相当快.

- 创建字典: dict = {}.fromkeys(('x', 'y'), -1) , 如果没有给出值,默认为none

- 遍历字典:

  ```python
  dict = {'name': 'earth', 'port': 80}
      for key in dict.keys():
          print 'key=%s, value=%s' % (key, dict[key])
  ```


- 得到字典的值

  ```print 'host %(name)s is running on port %(port)d' %dict2```


- 删除字典

  ```del dict2['name']```

### 映射类型操作符

- 用in 和 not in 操作符来检查某个键是否存在于字典中
- dict.copy()拷贝一个字典
- len()会返回字典的键值对数
- dict([container])创建字典的工厂函数. 如果提供了容器类,就用其中的条目填充字典.

### 映射类型内建方法

- dict.setdefault('port'. 8080)检查字典中是否含有某键,如果这个键存在,你可以取到它的值,如果不存在,可以给这个键赋默认值并返回次值.
- {}.fromkeys()用来初始化字典

### 字典的键必须是可哈希的

- 如果用元组作为字典的键,必须要加以限制,元组中职能包括像数字和字符串这样的不可变参数才可以作为字典中有效的键.

### 集合类型

- 子集/超集

  ```set('shop') < set('cheeseshop')```

  ```set('bookshop') >= set('shop')```


### 集合类型操作符

- 联合(|) 两个集合的联合是一个新集合
- 交集(&) : 该集合中的每个元素同时是两个集合中的成员
- 相对补集(-): 只属于集合X, 不属于集合Y
- 对称差分(^): 只能属于集合s或者集合t的成员,不能同时属于两个集合
- set([obj]): 可变集合工厂函数. obj必须是支持迭代的,由 obj中的元素创建集合,否则是空集合
- frozenset([obj]): 不可变集合工厂函数. 执行方式和set()方法相同

# 第8章 条件和循环

### else

- for-else:用于处理遍历失败, 在for循环完整后再执行else,如果中途从break跳出,则连else一起跳出.

- ```python
  from math import sqrt
  for n in range(99, 80, -1):
      root = sqrt(n)
      print (root)
      if root == int (root):
          print n
          break
  else:
      print ("Didn't find it!")
  ```

- ​

### 与序列相关的内建函数

> sorted(), reversed(), enumerate(), zip()

- sorted(): 给序列排序
- print list(reversed([123, 214, 212, 111])): 反转数组
- enumerate 函数用于遍历序列中的元素以及它们的下标: for i,j in enumerate(('a','b','c'))
- zip函数接受任意多个（包括0个和1个）序列作为参数，返回一个tuple列表

### continue语句

- 当遇到continue语句时,程序会终止当前循环,并且忽略剩余的语句,然后回到循环的顶端.

### pass语句

- pass语句表示不做任何事情

### 迭代器和iter()函数

```python
myTuple = (123, 'xyz', 45.67)
i = iter(myTuple)
i.next()
```

- 字典

```python
for eachKey in myDict:
```

- 文件

```python
for eachLine in myFile
```

- 如何创建迭代器? 
- - 对一个对象调用iter()就可以得到它的迭代器
  - 如果你传递一个参数给iter(), 它会检查你传递的是不是一个序列, 如果是, 根据索引从0一直迭代到序列结束.

### 列表解析

- [(x ** 2) for x in range(6) if x > 1]


- 矩阵样例 [(x+1,y+1) for x in range(3) for y in range(5)]
- 磁盘文件样例: f = open('hhga.txt', 'r')    len([word for line in f for word in line.split()])

### 生成器表达式

- ```python
  sum(len(word) for line in data for word in line.split())
  ```


- 寻找文件最长的行(因为文件本身就成为了它自己的迭代器,不需要调用readlines())

```python
f = open('/etc/motd', 'r')
allLineLens = [len(x.strip()) for x in f]
f.close()
print max(allLineLens)
```

> 简化为

```python
max(len(x.strip()) for x in open('/etc/motd'))	
```

# 第9章 文件和文件输出

### 文件内建函数

```python
fp = open('/etc/motd')# 以读方式打开 fp = open('test', 'w')# 以写方式打开
fp = open('test', 'w')# 以写方式打开
fp = open('data', 'r+') # 以读写方式打开
fp = open(r'c:\io.sys', 'rb') # 以二进制读模式打开
```

- 所有的open()方法都可以用file()来替代

### OS模块访问函数

| 函数                       | 描述                   |
| ------------------------ | -------------------- |
| remove()/unlink()        | 删除文件                 |
| rename()                 | 重命名文件                |
| chdir()                  | 改变当前工作目录             |
| listdir()                | 列出指定目录的文件            |
| rmdir()/removedirs()     | 删除目录/删除多层目录          |
| mkdir()/makedirs()       | 创建目录/创建多层目录          |
| getcwd()                 | 获得当前位置               |
| os.path.expanduser('~/') | 返回当前路径的绝对路径(**跨平台**) |

# 第10章 错误和异常

### 检测和处理异常

- try 语句有两种主要形式: try-except 和 try-finally 
- 我们可以在一个except子句里处理多个异常. except语句在处理多个异常时要求异常被放在一个tuple里.
- try -finally 无论如何都执行

### 上下文管理

- with语句: 仅能工作于支持上下文管理协议的对象(file.....)

# 第11章 函数和函数式编程

### 返回值

- 返回值可以是一个值或对象,也可以是list或者tuple

### 默认参数

- 默认参数让程序的健壮性上升到极高的级别,因为它们补充了标准位置参数没有提供的一些灵活性,这种简洁极大帮助了程序员.
- def net_conn(host, port=80, style='tcp')

### 函数式编程

- lambda表达式: true =  lambda: True

- def add(x, y): return x + y  ? lambda x, y: x + y

- ```python
  a = lambda x, y=2: x + y
  ```


- apply()  filter()  map()  reduce()  ?

# 第12章 模块

### 模块和文件

- 模块被保存在sys.path里面,这是一个列表,我们可以对它进行修改: sys.path.append('/home/andy/py/lib')

### 名称空间

- __builtins__ 和 _builtin__    : buildins模块包含内建名称空间中内建名字的集合,其中大多数来自__buildin__模块,该模块包含内建函数,异常以及其他属性. 
- 名称空间可以理解为一个容器,这个容器中可以装许多标识符,不同容器中同名的标识符不会冲突.

### 导入模块

- from module import name: 导入指定的模块属性
- import Tkinter as tk: 使用自己想要的名字替换模块的原始名称

### 包

- 包是一个有层次的文件目录结构,它定义了一个由模块和子包组成的python应用程序执行环境.
- 我们可以这样导入子包: import Phone.Mobile.Analog
- 可以使用from-import实现不同需求的导入. from Phone import Mobile
- from package.module import *

# 第13章 面向对象编程

### 介绍

- **新式类**: 在2.2以前类和类型是不同的,为了统一类和类型,引入新式类,更多的内置属性将会被引入, 描述符的引入, 属性可以用来计算等等. 用户默认定义的是经典类, 新式类需要继承自所有的类的基类(object)或者继承自object的新类.    在旧式类中，所有的 类对象的类型都被视为 classobj 类型， 所有的实例对象的类型都被视为 instance 类型；而所有 实例对象的类型都是对应的类对象，所有实例对象的类都是对应的类对象,也就是说python中新式类的所有对象(包括类对象，实例对象)所拥有的类和类型都统一了。


在新式类中，所有的类对象的类型都是 type 类型，所有类对象的类都是 type 类(也就是类对象是type的实例对象)；

- ```python
  class CC:            #经典类
      def __init__( self ):
          pass

  class CCN(object):    #新类
      def __init__( self ):
          pass 

  c1 = CC()
  c2 = CCN()

  c1.__class__            # 输出-> <class __main__.CC at 0x0137BF10>
  type(c1)                # 输出-> <type 'instance'>

  c2.__class__            # 输出-><class '__main__.CCN'>
  type(c2)                # 输出-><class '__main__.CCN'>
  ```

- *用类名作名称空间容器**: 

- ```python
  class MyData(object):
      pass
  mathObj = MyData()
  mathObj.x = 4
  mathObj.y = 5
  mathObj.x + mathObj.y
  ```

  ```python
  class AddrBookEntry(object): # 类定义 'address book entry class'
  def __init__(self, nm, ph): # 定义构造器 
      self.name = nm # 设置 name
      self.phone = ph # 设置 phone
      print 'Created instance for:', self.name
  def updatePhone(self, newph): # 定义方法 
      self.phone = newph
      print 'Updated phone# for:', self.name
  ```


- 子类: 继承了父类的属性,每个子类最好定义它自己的构造器,不然父类的构造器会被调用.

### 类

- 创建类:

- ```python
  class ClassName(bases):
      'class documentation string' #'类文档字符串'
      class_suite #类体
  ```

- 使用类的方法的时候一定要初始化类 mc = myClass()    mc.myNoActionMethod()

### 类属性

- 特殊类属性

- | 属性名称           | 作用        |
  | -------------- | --------- |
  | `C.__name__`   | 类C的名字     |
  | `C.__doc__`    | 文档字符串     |
  | `C.__bases__` | 所有父类构成的元组 |
  | `C.__dict__`   | 属性        |
  | `C.__module__` | 所在的模块     |
  | `C.__class__`  | 对应的类      |

### 子类

- 创建一个子类

- ```python
  class Parent(object): # define parent class 定义父类
       def parentMethod(self):
           print 'calling parent method'
  class Child(Parent): # define child class 定义子类 def childMethod(self):
  print 'calling child method'
  >>> p = Parent() # instance of parent 父类的实例 
  >>> p.parentMethod()
  calling parent method
  >>> c = Child()# instance of child 子类的实例 
  >>> c.childMethod() # child calls its method calling child method
  >>> c.parentMethod() # calls parent's method calling parent method
  ```

- `__init__`: 当从一个构造器的`__init__`的类派生,如果你不去覆盖`__init__`,它将会被继承并自动调用.但如果你在子类中覆盖了`__init__`,子类被实例化时,父类的`__init__`就不会被自动调用. 如果想调用父类的`__init__`, 就需要明确指出父类. (`P.__init__(self)`)

### 内建函数

- isinstance(): 判断一个对象是否是另一个给定类的实例
- super(): 用来查找父类的属性 ` super(MyClass,self).__init__()`


- var() 返回一个包含对象存储于其`__dict__`中的属性及值.

- ```python
  class C(object):
      pass
  >>> c = C()
  >>> c.foo = 100
  >>> c.bar = 'Python'
  >>> c.__dict__
  {'foo': 100, 'bar': 'Python'}
  >>> vars(c)
  {'foo': 100, 'bar': 'Python'}
  ```

# 第14章 执行环境

### 可执行的对象声明和内建函数

- compile()函数允许程序员在运行时刻迅速生成代码对象,然后就可以用exec语句或者内建函数eval()来执行这些对象或者对他们进行求值.

### 执行python程序

- 当导入python模块后,就执行所有的模块.

# 第15章 *正则表达式*

| 记号       | 说明                | 举例            |
| :------- | :---------------- | :------------ |
| literal  | 匹配字符串的值           | foo           |
| re1\|re2 | 匹配正则表达式re1或 re2   | foo\|bar      |
| .        | 匹配任何字符            | b.b           |
| ^        | 匹配字符串的开始          | ^Dear         |
| $        | 匹配字符串的结尾          | /bin/*sh$     |
| *        | 匹配前面出现的正则表达式零次或多次 | [A-Za-z0-9]*  |
| +        | 匹配前面出现的正则表达式一次或多次 | `[a-z]+\.com` |
| ?        | 匹配前面出现的正则表达式零次或一次 | goo?          |
| {N}      | 匹配前面出现的正则表达式N次    | [0-9]{3}      |

| {M,N}          | 匹配重复出现M次到N次的正则表达式                     | [0-9]{5,9}              |
| -------------- | ------------------------------------- | ----------------------- |
| [...]          | 匹配字符串里出现的任意一个字符                       | [aeiou]                 |
| [..x-y..]      | 匹配从字符x到y中的任意一个字符                      | [0-9],[A-Za-z]          |
| [^...]         | 不匹配此字符集中出现的任何一个字符,包括某一范围的字符           | [^aeiou]                |
| (*\|+\|?\|{})? | 用于上面出现的任何'非贪婪'版本重复匹配次数符合(*, +, ?, {}) | .*?[a-z]                |
| (...)          | 匹配封闭括号中正则表达式,并保存为子组                   | ([0-9]{3})?,f(oo\|u)bar |
| \d             | 匹配任何数字,和[0-9]一样(\D是\d的反义:任何非数字)       | data\d+.txt             |
| \w             | 匹配任何数字字母字符,和[A-Za-z0-9]相同(\W是\w的反义)   | [A-Za-z_]\W+            |
| \s             | 匹配任何空白符,和[\n\t\r\v\f]相同,(\S是\s的反义)    | of\sthe                 |
| \b             | 匹配单词边界(\B是\b的反义)                      | \bThe\b                 |

| \nn    | 匹配以保存的子组(请参考上面的正则表达式符号: (...)) | price: \16  |
| ------ | ------------------------------ | ----------- |
| \c     | 逐一匹配特殊字符c(取消它的特殊含义,按字面匹配)      | `\., \\, *` |
| \A(\Z) | 匹配字符串的起始(结束)                   | \ADear      |

- 管道(|) 匹配多个表达式
- [] 匹配方括号内任意一个字符

# 第18章 多线程编程	





