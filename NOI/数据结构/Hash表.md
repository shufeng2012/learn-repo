**定义：** 类似`map`数据结构，通过*Hash函数*将每一个元素映射到Hash表中
# Hash表构建函数
## 直接定址法
函数为$Hash(k)=a\times k+b$ ，**适用于连续的元素**
**示例：**
```cpp
//H(k)=k
int build(int k){
	return k;
}
//H(k)=k-100
int build(int k){
	return k-100;
}
```
## 除留余数法（最常用）
函数为$Hash(k)=k\mod a$，**最常用的构建函数**
> $a$通常为小于等于表长的最大质数，可以极大避免*冲突*

**示例**
```cpp
//表长为8的Hash表
//H(k)=k%7
int build(int k){
	return k%7;
}
```
### 解决冲突方法
***注意：Hash表为循环表***
#### 线性查找法
即从冲突的位置往后查找，直到查找到空位置
**示例：**
```cpp
//表长为8的哈希表，默认空位置为-1
void build(int k){
	int index=k%7;
	if(hash[index]==-1)
		hash[index]=k;
	else{
		while(hash[index]!=-1)
			index=(index+1)%8;
		hash[index]=k;
	}
}
```
#### 平方查找法
从冲突的地方按照$\pm x^2$查找，查找到空位则填入
> 保证Hash表完全填满：$表长=4k+1$

**示例：**
```cpp
//表长为8的哈希表，默认空位置为-1
void build(int k){
	int index=k%7;
	if(hash[index]==-1)
		hash[index]=k;
	else{
		int i=1;
		while(hash[index]!=-1){
			index+=i*i;
			if(hash[index]==-1)
				continue;
			else{
				if(index<0)
					index=-index+1;
				else
					index=-index;
			}
		}
		hash[index]=k;
	}
}
```
# Hash表查找函数
按照Hash函数进行映射，对比**是否相同**，如果不是，则按照**冲突解决方案**进行查找
**示例：**
```cpp
int find(int k){
	
}
```