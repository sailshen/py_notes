# python 笔记
## 1.变量与集合
* 列表li
  + 用来保存序列
  + []保存序列，初始化列表，访问元素
  +  append()方法添加末尾元素
  +  pop()方法移除末尾元素
  +  del()方法删除特定元素
  +  切片语法可以看做区间可以省略开头和末尾的元素
  +  list1 + list2合并列表(*并不会改变源列表)
  +  或通过extend()方法合并列表
  +  in检查元素是否在列表中
  -  len()方法返回列表长度
* 元组tup
  +  类似列表但是不可改变
  +  使用()初始化
  +  可以将元组解包分给多个不同变量
  +  a, b, c = (1 , 2, 3)
  +  不加括括号自动设为元组
  +  d, e, f = 4 , 5, 6
  +  e, d = d, e 交换d ,e的值
* 字典dict
  +  存储映射关系
  +  初始化使用大括号
  +  empty_dict = {“one”: 1, "two": 2, "three": 3}
  +  可以使用[]来访问元素，若不存在返回KeyError
  +  key()方法可以把键存在列表中(*因为字典的随机性列表顺序不唯一)
  +  values()方法把键值存在列表中(*随机性)
  +  get()方法读取元素可以避免KeyError，
  +  （当键不存在时可以返回一个默认值，
  +  例如
  +  filled_dict.get("one", 4)  # => 1
  +  filled_dict.get("four", 4)  # => 4
    ）
  +  setdefault(）是一种更安全的添加字典元素的方法他不会覆盖原有的键值
* 集合set
  +  用于存储无顺序的元素
  +  2.7版本以前初始化使用set([])方法
  +  2.7版本以后可以直接使用 {} 来初始化集合
  +  filled_set = {1, 2, 2, 3, 4}  # => {1 2 3 4}
  +  add()方法可以添加元素
  +  使用&来计算两个集合之间的交集
  +  使用|来计算两个集合之间的并集
  +  使用-来计算两个集合之间的差
  -  in来判断元素是否存在于集合中
## 2. 控制流程
```python
  if
    # 新建一个变量
    some_var = 5

    # 这是个 if 语句，在 python 中缩进是很重要的。
    # 下面的代码片段将会输出 "some var is smaller than 10"
    if some_var > 10:
        print "some_var is totally bigger than 10."
    elif some_var < 10:    # 这个 elif 语句是不必须的
        print "some_var is smaller than 10."
    else:           # 这个 else 也不是必须的
        print "some_var is indeed 10."
  用for循环遍历列表
      输出:
          dog is a mammal
          cat is a mammal
          mouse is a mammal
      """
      for animal in ["dog", "cat", "mouse"]:
          # 你可以用 % 来格式化字符串
          print "%s is a mammal" % animal

      """
  range(number)` 返回从0到给定数字的列表
      输出:
          0
          1
          2
          3
      """
      for i in range(4):
          print i

      """
  while 循环
      输出:
          0
          1
          2
          3
      """
      x = 0
      while x < 4:
          print x
          x += 1  #  x = x + 1 的简写
  ```
## 3.函数
  + def 新建函数
  + 可以使用关键字赋值来调用函数
  + *args可以接受多个位置参数，存放在元组中
  + **kwargs可以接受多个多个关键字参数，存放在字典中
  + 可以嵌套
  + 匿名函数lambda
  ```python
    >>> map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9])
    [1, 4, 9, 16, 25, 36, 49, 64, 81]
  ```
## 4. 类

  ```python
    #新建类是从object中继承的
    class Human(object):
    # 类属性，由所有类的对象共享
     species = "H. sapiens"

     # 基本构造函数
     def __init__(self, name):
         # 将参数赋给对象成员属性
         self.name = name

     # 成员方法，参数要有 self
     def say(self, msg):
         return "%s: %s" % (self.name, msg)

     # 类方法由所有类的对象共享
     # 这类方法在调用时，会把类本身传给第一个参数
     @classmethod
     def get_species(cls):
         return cls.species

     # 静态方法是不需要类和对象的引用就可以调用的方法
     @staticmethod
     def grunt():
         return "*grunt*"

     #实例化一个类
     i = Human(name="Ian")
     print i.say("hi")     # 输出 "Ian: hi"

     j = Human("Joel")
     print j.say("hello")  # 输出 "Joel: hello"

     # 访问类的方法
     i.get_species()  # => "H. sapiens"

     # 改变共享属性
     Human.species = "H. neanderthalensis"
     i.get_species()  # => "H. neanderthalensis"
     j.get_species()  # => "H. neanderthalensis"

     # 访问静态变量
     Human.grunt()  # => "*grunt*"
  ```
## 5. 模块
  + import调用模块
  + from ... import从模块调用特定函数
  + from ... import * 调用所有函数(警告 不推荐使用)
  + dir()方法查看模块的属性和方法
