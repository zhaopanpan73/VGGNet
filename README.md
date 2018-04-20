# VGGNet
### VGGNet的特点：
* VGGNet探索了卷积神经网络的深度与其性能之间的关系，通过反复堆叠3*3的小型卷积核和2*2的最大池化层，VGGNet成功的构筑了16~19层深的卷积神经网络
* VGGNet的网络结构非常简洁，整个网络都使用了同样大小的卷积核尺寸（3*3）和最大池化尺寸（2*2），到目前为止VGGNet依然经常被用来提取图像特征。可用来在domain specific 的图像分类任务上进行再训练（相当于初始化权重），因此被用在了很多地方

### 网络结构说明
* 使用3*3的卷积核和2*2的池化核，通过不断的加深神经网络的结构来提升性能
* 从A到E的每一级网络逐渐变深，但是网络的参数量并没有增长很多，这是因为主要的参数量都消耗在最后3个全连接层，
* 前面的卷积部分虽然很深，但是消耗的参数量不大，比不过训练比较耗时的部分依然是卷积，因其计算量比较大。这其中的D,E也就是我们常说的VGGNet-16和VGGNet-19.C很有意思，相比B多了几个1*1的卷积层，1*1的卷积的蛀牙意义是线性变换，而输入通道数和输出通道数不变，没有发生降维。
* VGGNet拥有5段卷积，每一段内有2~3个卷积层，同时每段尾部都会接一个最大池化层用来缩小图片尺寸。每段内的卷积核数量一样，越靠后面卷积核的数量越多：64-128-256-512-512
* 3个3*3的卷积层串联效果相当于一个7*7的卷积层，而且3个3*3的卷积层的参数要比1个7*7的卷积层的少 eg,3*3*3/(7*7)=55%
  最重要的是3个3*3的卷积层拥有比1个7*7的卷积层的更多的线性变换（前者可以使用三次ReLU激活函数，而后者只有一次），使得CNN对特征的学习能力更强

### 作者总结了一下几个观点：
 1. LRN层作用不大
 2. 网络越深越好
 3. 1\*1的卷积也是很有效的，但是没有3*3的卷积核好，大一些的卷积核可以学习更大的空间特征。


