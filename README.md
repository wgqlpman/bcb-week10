# 堆，优先序列和堆排序  
## 堆的概念  
最大堆和最小堆是二叉堆的两种形式。二叉堆(binary heap)是一种特殊的堆，二叉堆是完全二叉树或者是近似完全二叉树。二叉堆满足堆特性：父节点总是保持固定的序关系于任何一个子节点的键值，且每个节点的左子树和右子树都是一个二叉堆。  
最大堆：根结点的键值是所有堆结点键值中最大者，且每个结点的值都比其孩子的值大。  
最小堆：根结点的键值是所有堆结点键值中最小者，且每个结点的值都比其孩子的值小。  
堆树的定义如下：  
（1）堆树是一颗完全二叉树；  
（2）堆树中某个节点的值总是不大于或不小于其孩子节点的值；  
（3）堆树中每个节点的子树都是堆树。  
当父节点的键值总是大于或等于任何一个子节点的键值时为最大堆。 当父节点的键值总是小于或等于任何一个子节点的键值时为最小堆。如下图所示，左边为最大堆，右边为最小堆。  
对于最大堆来说，最大元素位于根节点，那么删除操作就是交换根节点与堆的最后一个节点，然后将交换后的最后一个节点(交换前为根节点，value为最大值)移除并返回元素。此时新根节点需要下沉到适合的位置；当插入新元素的时候，将新元素添加至二叉堆的最后一个节点后，此时新节点需要根据value进行上浮操作，直到找到适合的位置。
最小堆和最大堆完全相反，最小元素位于根节点，下沉、上浮操作和最大堆基本相同
## 堆排序  
基本思想：

1.首先将待排序的数组构造成一个大根堆，此时，整个数组的最大值就是堆结构的顶端

2.将顶端的数与末尾的数交换，此时，末尾的数为最大值，剩余待排序数组个数为n-1

3.将剩余的n-1个数再构造成大根堆，再将顶端数与n-1位置的数交换，如此反复执行，便能得到有序数组  
### 步骤  
1. 把无序数组构建成二叉堆。

2. 循环删除堆顶元素，移到集合尾部，调节堆产生新的堆顶。

当我们删除一个最大堆的堆顶（并不是完全删除，而是替换到最后面），经过自我调节，第二大的元素就会被交换上来，成为最大堆的新堆顶。

正如上图所示，当我们删除值为9的堆顶节点，经过调节，值为6的新节点就会顶替上来；当我们删除值为6的堆顶节点，经过调节，值为5的新节点就会顶替上来.......

由于二叉堆的这个特性，我们每一次删除旧堆顶，调整后的新堆顶都是大小仅次于旧堆顶的节点。那么我们只要反复删除堆顶，反复调节二叉堆，所得到的集合就成为了一个有序集合，

堆排序是不稳定的排序，空间复杂度为O(1),平均的时间复杂度为O(nlogn),最坏情况下也稳定在O(nlogn)   

## 优先队列  
能够完成以下两个操作的数据结构叫优先队列：  
* 可以插入新元素
* 可以快速取出所有元素的最值。  
  
  优先队列的实现：堆  
 *  堆是一颗完全二叉树。
 * 重要的性质：父节点一定是其所有子孙节点的最值。  
 * 堆的插入：首先在堆的末尾插入该数值，然后不断向上调整，直到没有大小颠倒为止。
 * 取出最值：最值就在堆顶，即二叉树的第一个元素。
 * 删除最值：首先将堆的最后一个元素复杂到根节点，并删除最后一个元素，然后将根节点不断向下进行调整直到没有大小颠倒。
 * 时间复杂度：堆的插入和删除的时间复杂度为O ( l o g ⁡ n ) O(log⁡n)O(log⁡n)
### 优先队列的实现：  
我们知道完全二叉是可以通过简单的数值实现的，如果我们将完全二叉树中的每个节点进行编号，编号从1开始，编号顺序是从上到下从左到右，然后根据这个编号将树中的节点存储到数组中，父子关系可以通过下面方式得到：  

假设当前节点的编号(数组中的编号)为i ii，则有：  
它的父节点的编号为：i / 2 i/2i/2(整除)  
它的左儿子节点的编号为：2 ∗ i 2*i2∗i  
它的右儿子节点的编号为：2 ∗ i + 1 2*i+12∗i+1

