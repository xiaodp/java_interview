![image-20200328213723647](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328213723647.png)

![image-20200328213942082](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328213942082.png)

### 一 Java 虚拟机【栈内存】区域，**FILO**：

局部变量

oracle官网查看javadoc：Run-Time Data Area

![image-20200328214500025](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328214500025.png)

栈：

​	为线程分配内存

栈帧：

​	运行方法

​	一个方法对应一个栈帧

![image-20200328214733406](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328214733406.png)

 由此可知，栈可以存放方法的**局部变量**

![image-20200328215223460](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328215223460.png)

除此之外，还有**操作数栈**，**动态链接**，**方法出口**

#### 操作数栈

**javap**

​	javap -c .class文件

![image-20200328215911549](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328215911549.png)

![image-20200328215806080](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328215806080.png) 



```java
public int compute(){
	int a = 1;
	int b = 1;
	int c = (a + b) * 10;
	return c;
}
```

经过javap -c 后，生成如下：

![](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328220625691.png)

​	JVM指令手册

![image-20200328215823899](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328215823899.png)

```java
int a = 1;
```

java执行上述语句，将对应两条jvm指令：

```
iconst_1 ：将int类型的常量1压入操作数栈
istore_1 ：...
```

![image-20200328220354001](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328220354001.png)

现在理解了什么是操作数栈了吧

存放临时操作数的内存区域



![image-20200328221327628](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328221327628.png)

	#### 方法出口

A方法调用B方法时，记录A调用的位置（B执行完成后返回的位置）



栈与堆之间的关系：

对象类型放在堆中，栈中局部变量存放了堆中的对象地址（引用）

![image-20200328221724678](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328221724678.png)

![image-20200328222023200](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328222023200.png)

### 二 程序计数器

![image-20200328220638643](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328220638643.png)

字节码执行引擎去记录修改程序计数器

Q：为什么jvm需要程序计数器？

当前线成被其他线程中断时，通过程序计数器来恢复，继续执行未执行的代码



### 三 方法区

存放 常量 、静态变量 、 类信息

class文件被类装载子系统装载到方法区

```java
public static user = new User();
```

![image-20200328222302573](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328222302573.png)

方法区中有静态变量，如果变量指向某一对象，则方法区中的静态变量存储的是对象在堆中的地址

### 四 本地方法栈

什么是本地方法？

![image-20200328222551674](/Users/xiaodp/OneDrive/学习笔记/java面试必备/image-20200328222551674.png)

有native修饰的方法

1995年之前的代码由c语言等编写，执行本地方法需要的内存区域，调用库函数



### 五 堆内存详解

![image-20200328223055794](/Users/xiaodp/Library/Application Support/typora-user-images/image-20200328223055794.png)





