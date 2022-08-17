# NOTES

## day1
### 基本操作
- 模式
    - normal模式 insert模式
- 基本移动 上下左右 HJKL
- 插入文字 i光标后方 a光标前方
- 出insert模式
- 在终端中如何退出
  - :wq 保存并退出  :q! 强制退出
- ctrl和caps调换位置
 -  系统键盘修改修饰键
- 快速移动
  - 配置 以及 修改键盘设置

> tips： 习惯insert完立即回到Norma模式

## day2
### 行的操作
* 行的移动 ( normal模式下)
行首：^ 改键 H
行尾：g_ 改键 L
由于输入时经常想移动光标，于是就将insert模式下的光标移动改为了 ctrl + hjkl。
* 行的插入
行首插入 A
行尾插入 I
行前 O （换行）
行后 o  （换行）
* 复制粘贴
复制行 yy
删除行 dd （可以粘贴）
粘贴 p

## day3
### 删除复制和基于单词的移动

* vim的语法
    定义：操作符 + 动作 （区域范围、使用移动的一些动作）
* 操作
· 删除 d (hjkl/ H/ L/ webge/ )
· 删除后进入insert模式 c
· 复制 y
* 基于单词和字串的移动
单词的定义： 单词与符号都认定为单个单词
字串的定义： 以空格分割的一串字符
  * 基于单词的移动
    e 单词结尾 往后
    w 单词开头 往后
    b 单词开头 往前
    ge 单词结尾 往前
  * 基于字串的移动
    E 字串结尾 往后
    W 字串开头 往后
    B 字串开头 往前
    GE 字串结尾 往前
* 组合
  * cw 删除当前单词
  * ea 在当前单词结尾处添加

## day4
### 快捷删除和替换、撤销
x 删除当前光标字符
X 删除光标前的字符
s 删除光标字符后进入insert模式
S 删除当前行后进入insert模式
r+【输入】 替换字符
R+【输入多个字符】替换多个字符
undo 和 redo
u 撤销
C + r 撤回撤销

## day5

### 可视化模式
v 进入可视化模式;
V 以行为单位;
C + v 以块为单位;

* 退出可视化模式
esc C+[ 退出
v V 退出

* 选定范围
配合动作
o 切换开始的光标位置
gv 回到上一次选中区域

* 技巧
跨多行同时操作 选中后A I d ...
复制粘贴 利用

## day6

### 文本对象 （范围）

> 释义：
> 操作 + 内/外部 + 文本对象
 内部 i
 外部 a

 **w 一个单词**
 **b  一对括号**
**B  一对{}**
() 一对括号
{} 一对{}
<> 一对<>
其他符号类推
 **t xml标签**
s 一个句子
p 一个段落

vim-textobj-arguments function参数
> ia 不包含分隔符
    aa 包含分隔符
    删除一个参数 daa
    修改一个参数 cia

vim-textobj-entire
> aa 删除当前文本所有
ia 删除当前文本所有 不包含前面和后面空格

## day7

### 滚动

* C + f 向下滚动一屏
* C + B 向上滚动一屏
* C + d 向下滚动半屏
* C + u 向上滚动半屏
* C + e 向下滚动一行
* C + y 向上滚动一行
* 基于配置（更容易记忆）
  * **上五行 K**
  * **下五行 J**
  
* **zz 将当前行置于屏幕中央**
* zt 当前行置于屏幕顶部附近
* zb 将当前行置于屏幕底部附近
* gg 跳转到文件首
* G 跳转到文件尾
* **行数 + gg / G 跳转到指定行**

## day8

### 搜索

* f 正向移动到下一个（char）所在之处
* F 反向向移动到下一个（char）所在之处
* t 正向移动到下一个（char）字符之前
* T 反向移动到下一个（char）字符之前

> ; 下一个
> , 上一个
> 移动用f，配合c d等操作用t

* / 向下全局查找
* ? 向上全局查找

> n/N 下一个/上一个
> / + 方向键 查看搜索历史
> **和操作使用**

* \# 向上查当前光标所在单词
* \* 向下查当前光标所在单词

## day9

### 更高效的移动 （通过两个已经集成的插件）

* esaymotion （使用后会高亮可移动的位置）
  * \<leader>\<leader> w  当前光标往后的word首
  * \<leader>\<leader> e  当前光标往后的word尾
  * \<leader>\<leader> b  当前光标往前的word首
  * \<leader>\<leader> w  当前光标往后的word尾

  * **\<leader>\<leader> h  当前光标往前的word首+尾**
  * **\<leader>\<leader> l  当前光标往后的word首+尾**

  * \<leader>\<leader> j  当前光标往后的行首
  * \<leader>\<leader> k  当前光标往前的行首

* sneak （通过两个字符全局搜索）
  * s + 2个字符 （改键后使用 f | F ）
  * 改键
    * 替换原生的f功能（比f更加强大、不用记这么多键）
    * 利用映射实现原来的s/S/z/Z （与原来的s不冲突）
  
  * 在可视化visual模式下使用 v + f + 2个字符
  * 在操作符下使用 v + f + 2字符  
  
## day10

### 数字

* 语法
  * 操作符 + 数字 + 范围
  * 数字 + 操作符 + 范围

### 点

* 重复上一次的修改 （增加、删除、更新）
  * 例子：diw 删除单词，可用点重复
* **核心：一键移动一键操作**
  * 场景案例1： 句尾加分号
  * 场景案例2： 手动查找替换

## day11

### 多文件之间的跳转

* 标记
  * **mm 单文件**
  * **mM 多文件**
* 跳转
  * ' 跳转到标记的行
  * ` **跳转到标记的行和列**

* **gd 跳转到指定地方**

> 查看函数定义、使用的位置 （类似于vscode的跳转）
> **可以跨文件使用**

* 跳转历史
  * C + i 向前跳
  * C + o 向后跳

> :jumps 跳转的历史列表

### day12
### 处理包裹字符的符号

* cs+已经存在的符号+改变的符号  **改变符号**
* ys+范围+符号 **用符号包裹字符**
* ds+符号 **删除符号**

* **可视化模式下** S + 符号 **用符号包裹字符**