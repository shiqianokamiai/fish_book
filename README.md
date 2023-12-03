# fish_book
自学深度学习入门-基于Python的理论和实现，本人很菜


广播
-
**NumPy**中，形状不同的数组之间也可以进行运算。之前的例子中，在2×2的矩阵A和标量10之间进行了乘法运算。在这个过程中，如图1-1所示，标量10被扩展成了**2 × 2**的形状，然后再与矩阵A进行乘法运算。这个巧妙的功能称为**广播（broadcast）**。
![image](https://github.com/shiqianokamiai/-/assets/151977259/ea492c74-8e7f-459d-98ba-c0454d010813)

代码示例：
~~~
import numpy as np
A = np.array([[1,2],[3,4]])
B = np.array([10,20])
print(A*B)
print(A)
print(B)
~~~
3 神经网络
=

3.1 激活函数
-

当激活函数以阈值为界限，超过阈值切换输出结果。这一过程被称作 **“阶跃函数”**。所以可以说感知机内的激活函数就是
**“阶跃函数”**。 如果我们将激活函数发生改变，那么我们就步入了神经网络的领域。
## sigmoid 函数
**sigmoid公式**如下：

![image](https://github.com/shiqianokamiai/fish_book/assets/151977259/249270f7-c2e8-4c3c-9217-7fb46233f5e7)
书中有写到关于阶跃函数的代码在编写时会出现的问题：
~~~
def step_function(x):
	if x > 0:
		return 1
	else:
		return 0
~~~
这里step_function只能接受**实数**，不允许**Numpy 数据**。
~~~
x = np.array([-1, 1, 2])
y = x > 0
~~~
我们先将numpy以布尔型的形式保存，结果为array([False, True, True], dtype = bool)

我们将array从布尔型转化为int
~~~
y = y.astype(np.int)
~~~
3.2 阶跃函数与sigmoid函数
-

两者之间极大的**不同点**在于：阶跃函数在**感知机**内的信号传递是**二元的0或1**,而在**神经网络模型**中，是**流动的实数信号**。
![阶跃函数](https://github.com/shiqianokamiai/fish_book/assets/151977259/4d091978-4665-4966-8c83-d563a57f55e9)
![sigmoid](https://github.com/shiqianokamiai/fish_book/assets/151977259/6d933e96-85ec-4a0a-8a9b-71275873b60c)

3.3 非线性函数
-
阶跃函数与sigmoid函数有着共同点：他们都是非线性函数。
### 为什么不使用线性函数作为激活函数呢？
线性函数的问题在于它的存在会直接摧毁多层神经网络的优势和意义，当数据输入线性函数，前后的变化只会是普通的乘上一个倍数。这一过程其实一个单层无隐藏层的神经网络结构也能够同样地完成。

3.3.1 ReLU函数
-
公式如下：

![image](https://github.com/shiqianokamiai/fish_book/assets/151977259/7a73c126-34e9-40e5-960d-6f67185fe49f)
当输入大于0时，直接输出输入；小于0的时候，始终输出0。
![ReLU](https://github.com/shiqianokamiai/fish_book/assets/151977259/08ceda0c-ea52-4115-929f-49dc2f1695d3)
![combination](https://github.com/shiqianokamiai/fish_book/assets/151977259/9758f1c5-ac7e-4199-8fd2-b3474a0c1d8f)

3.4 3层神经网络的实现
-
![image](https://github.com/shiqianokamiai/fish_book/assets/151977259/b784fb9b-8b06-4729-93de-9927aa8e27e9)
先是各个参数的上下标进行说明。
![image](https://github.com/shiqianokamiai/fish_book/assets/151977259/2dfbb754-9f44-4e97-9894-37039f45d9e5)
具体的标注可以仔细研读鱼书，stackedit不好写符号和公式。
![image](https://github.com/shiqianokamiai/fish_book/assets/151977259/dad9adb4-d942-42a3-a191-3f6c26d33f24)

