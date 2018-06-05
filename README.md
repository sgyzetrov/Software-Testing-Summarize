# Software-Testing-Summarize

[Software Testing and QA] Keynotes, I prepared my final exam based on this.

## 软件测试复习（部分）

### 概述

程序+文档+数据=软件

狭义的软件测试定义：为发现软件缺陷而执行程序或系统的过程

广义的软件测试定义：人工或自动地运行或测定某系统的过程，目的在于检验它是否满足规定的需求或弄清预期结果和实际结果间的差别
 
为什么要做软件测试

- 发现软件缺陷
    - 功能错
    - 功能遗漏
    - 超出需求部分（画蛇添足）
    - 性能不符合要求
- 软件质量高低：是否符合用户习惯、符合用户需求

测试的任务

- 找出
- 定位
- 修改
- 修改后要做回归测试，对已修改的部分进行再次的测试，避免引入新的错误

测试用例的定义和组成部分

- 测试用例是为特定的目的而设计的一组测试输入、执行条件和预期的结果。测试用例是执行的最小实体。简单地说，测试用例就是设计一个场景，使软件程序在这种场景下，必须能够正常运行并且达到程序所设计的执行结果。
- 包含
    - 用例ID
    - 用例名称
    - 测试目的
    - 测试环境
    - 前提条件
    - 测试步骤
    - 预期结果
    - 其他信息


<mark>一个好的高质量的测试用例在于能发现至今未发现的错误，一个成功的测试是发现了至今未发现的错误的测试</mark>

两个方向

- 找错误，反向思维。
- 证明能正常工作，正向思维。
- 目前的方法出发点一般是“找错误”，因为没法证明软件是正确的。

用户需求

| 要求（用户想要） | 需求（用户目的） | 需要（用户内在欲望）     |
| :--------------: | :--------------: | :----------------------: |
| 牙膏             | 清洁牙齿         | 个人魅力（个人外表整洁） |

<mark>什么时候停止测试</mark>

- 继续测试没有产生新的失效
- 继续测试没有发现新缺陷
- 回报很小
- 以达到要求的覆盖
- 无法考虑新的测试用例（若已遵循测试规则和指导方针，则可以选择）

### 测试过程模型

缺陷具有放大的特点，随着阶段的推进发现bug的成本会指数型上升，所以并不是代码级的测试才叫测试，而是开发过程各个阶段越早开始测试越好。

- 瀑布模型：需求分析->设计（概要、详细）->编程->测试（单元、集成、系统）->维护
- V模型（瀑布-改）：在软件开发的生存期，开发活动和测试活动几乎同时的开始，如概要设计阶段结束后集成测试的测试用例就出来了、详细设计阶段结束后单元测试的测试用例也就出来了等
- W模型（V模型更加细化、每步都加测试，边造软件边进行测试）：需求分析加了需求测试、概要设计加了功能测试、详细设计加了设计测试、编码加了单元测试、集成加了集成测试、确认加了确认测试、验收加了系统测试
- H模型：无实际意义，仅说明可以独立测试

### 软件测试的原则

- 所有的测试都应追溯到用户的需求
- 尽早地和不断地进行软件测试（缺陷具有放大的特点，测试成本随阶段深入而上升）
- 8-2原则
    - 测试中发现的错误80%很可能起源于程序中的20%
    - 提前测试可发现80%，系统测试找出剩余bug的80%（总体的16%），最后的4%可能只有用户大范围长时间使用后才暴露出来
    - 80%的工程用在20%的需求上（即关键需求）
    - ...
- 软件缺陷的寄生虫性：找到的缺陷越多说明软件遗留的缺陷越多
- 避免自己测试自己的程序
- 回归测试：避免引入新的错误

### 软件测试流程

制定测试计划->测试设计->测试开发->测试执行->评估测试

注意

- 测试不是开发后期的一个阶段
- 测试入门其实稍容易，但要求技术一样高
- 测试多数情况下不能覆盖所有输入
- 不要“有时间多测，没时间少测”
- 软件测试不止是测试人员的事，也是开发人员的事
- 调试和测试不一样
- 测试绝非只运行一下软件看结果对不对

L10N：本地化测试

I18N：国际化测试

### 黑盒测试

#### 等价类划分与边界值分析

如何划分有效和无效等价类（一些常用原则）

- 如果一个变量在某一个范围内，给它一个有效等价类两个无效等价类
- 如果一个变量取值在某一个集合范围内，可在集合内取一个有效等价类在集合外取一个无效等价类
- 如果一个变量的条件是“必须怎样”、“一定会是怎样”则去一个值满足“必须要”的条件再取多个不满足的从多个角度去违背这个条件
- 如果一个变量是布尔类型，则取一个对的一个错的

<mark>在找到有效等价类和无效等价类后如何找测试数据</mark>

- 有效等价类：要尽可能多的覆盖有效等价类
- 无效等价类：每找到一组数据要至少覆盖一组无效等价类

如果功能模块的输入是多个，多个自变量放在一起如何找有效等价类、无效等价类、测试数据，4钟方法：

以一个具有自变量X1、X2的函数F为例，X1取值范围为[a, b)、[b, c)、[c, d]；X2取值范围为[e, f)、[f, g]。仅考虑有标记的方块内为一般等价类测试（不处理无效数据的测试）、所有方块都考虑为健壮等价类测试（进行无效数据处理的测试）

```
g |_______|_______|_______|_______|_______|
f |_______|///////|///////|///////|_______|
e |_______|///////|///////|///////|_______|
  |_______|_______|_______|_______|_______|
          a       b       c       d
```

- 弱一般等价类
    - 有假设前提：是单缺陷的，即假设系统出现的缺陷很少是由两个及以上的输入变量共同出现缺陷而引起的。
    - 选取的测试用例覆盖所有的有效等价类
        - 对于X1（横轴）：[a, b)、[b, c)、[c, d]都需要覆盖到；对于X2（纵轴）：[e, f)、[f, g]都需要覆盖到。保证了这两点的情况下，就可以任意取点了

```
g |_______|_______|_______|_______|_______|
f |_______|_______|____x__|_______|_______|
e |_______|___x___|_______|___x___|_______|
  |_______|_______|_______|_______|_______|
          a       b       c       d
```

- 强一般等价类
    - 基于多缺陷假设
    - 选取的测试用例覆盖所有的有效等价类的笛卡尔积（集合A{a1,a2,a3} 集合B{b1,b2} 他们的 笛卡尔积 是 A*B ={(a1,b1),(a1,b2),(a2,b1),(a2,b2),(a3,b1),(a3,b2)} ）
        - 对于X1（横轴）：[a, b)、[b, c)、[c, d]；X2（纵轴）：[e, f)、[f, g]，笛卡尔积的结果就是所有的格子，所以必须所有格子都取点

```
g |_______|_______|_______|_______|_______|
f |_______|___x___|___x___|___x___|_______|
e |_______|___x___|___x___|___x___|_______|
  |_______|_______|_______|_______|_______|
          a       b       c       d
```

- 弱健壮等价类
    - 有假设前提：是单缺陷的，即假设系统出现的缺陷很少是由两个及以上的输入变量共同出现缺陷而引起的。
    - 考虑无效值，对有效输入，测试用例的设计等同于弱一般等价类；对无效输入，测试用例需要保证拥有一个无效值（比如某一变量的有效类的取值范围为x、y、z，则无效类为x-和z+，加起来取值范围一共：x-、x、y、z、z+），并保持其余的值都是有效的。

所以如下图，在保证弱一般等价类的取点后，还需要分别保证X1、X2中有1个属于无效输入的两个额外的取值范围，另一个属于有效输入的原本取值范围（如X1取无效X2取有效或X1取有效X2取无效，并全部覆盖无效范围）

```
g |_______|_______|_______|___O___|_______|
f |_______|_______|___x___|_______|___O___|
e |___O___|___x___|_______|___x___|_______|
  |_______|___O___|_______|_______|_______|
          a       b       c       d
```

- 强健壮等价类
    - 基于多缺陷假设
    - 所有的取值范围取笛卡尔积（比如某一变量的有效类的取值范围为x、y、z，则无效类为x-和z+，加起来取值范围一共：x-、x、y、z、z+，再与另一变量的取值范围取笛卡尔积）

```
g |___O___|___O___|___O___|___O___|___O___|
f |___O___|___x___|___x___|___x___|___O___|
e |___O___|___x___|___x___|___x___|___O___|
  |___O___|___O___|___O___|___O___|___O___|
          a       b       c       d
```
在找测试数据时

- 对于单缺陷的，即只有一个输入变量是处于无效等价类，其他所有输入变量都处在有效等价类中。包含：
    - 单缺陷有效值
    - 单缺陷无效值
- 对于多缺陷的，即多个输入变量同时出现错误引起的。包含：
    - 有效值
    - 无效值

与等价类划分密切相关的就是边界值分析。先划分等价类，再结合边界值产生测试用例。边界值分析中也有假设前提：单缺陷。包含4种设计测试用例的方法：

- 一般的边界值分析
    - 有效范围：最小的、比最小大一点的、正常值、比最大小一点、最大值
    - 无效范围：比最小更小、比最大更大
    - 共7个，再分单缺陷和多缺陷，这样设计测试用例的个数就会指数上升

 
|    -    | 单变量假设   | 多变量假设         |
| :----: | :----------: | :----------------: |
| 有效值 | **一般边界值**5n-(n-1)【n-1个变量取正常值】=4n+1【仅考虑有效区间单个变量边界值（一般边界值）：用最小值、略高于最小值、正常值、略低于最大值和最大值。】 | **一般最坏情况边界值**5^n【仅考虑有效区间多个变量边界值同时作用（一般最坏情况边界值）：用各个变量最小值、略高于最小值、正常值、略低于最大值和最大值的笛卡尔积。】 |
| 无效值 | **健壮性边界值**7n-(n-1)=6n+1【 同时考虑有效区间和无效区间单个变量边界值（健壮边界值）：除了最小值、略高于最小值、正常值、略低于最大值、最大值，还要有略超过最大值和略小于最小值的值。】 | **健壮最坏情况边界值**7^n【同时考虑有效区间和无效区间多个变量边界值同时作用（健壮最坏情况边界值）：用各个变量最小值、略高于最小值、正常值、略低于最大值、最大值、略超过最大值和略小于最小值的笛卡尔积。】 |

常见的边界值

- 16bit整数32767～-32768
- 报表第一行和最后一行
- 屏幕光标最左上和最右下
- 数组的第一个和最后一个
- 循环的第0、1、倒数第一、倒数第二次

#### 决策表

适合于问题有多个条件，条件有多种组合执行不同操作（有很多if、else if、else），不能表达循环结构

最严格、最具有逻辑性

```
判定表
| 条件桩 | 条件项 | ... | 动作项 |
| 动作桩 | 动作项 | ... | 动作项 |
```

规则：条件的任意组合，判定表中的一列（贯穿条件项和动作项）。判定表有多少列就代表有多少条规则。

规则的化简：有的规则相互包含，可以化简

#### 因果图

找出所有的原因，找出结果，可能还有中间结果的产生，在画因果图时注意。

- 从输入考虑
    - I：连虚线出去，如连到ab，表示ab中至少有一个必须成立
    - E：连虚线出去，如连到ab，表示ab不能同时成立
    - R：如处于a指向b的虚线三角箭头上，表示a出现时b也必须出现，不可能一个出现一个不出现
- 从输出考虑
    - M：如处于a指向b的虚线三角箭头上，表示a为1时b必须为0，a为0时b值不定
- 连线：恒等
- ～：非
- ∨：或
- ∧：且
- ci：原因
- ei：结果

画出因果图后，根据图得到决策表从而得到相应的测试数据：原因节点+中间节点为条件桩，结果结点为动作桩

### 白盒测试

#### 逻辑覆盖

```
语句覆盖->判定覆盖->判定/条件覆盖->条件组合覆盖->路径覆盖
      \_条件覆盖/
```

- 语句覆盖：每条语句执行一次
- 判定覆盖：每个判定分支至少执行一次
- 条件覆盖：每个判定条件应取到各种可能的值
- 判定/条件覆盖：同时满足判定和条件
- 条件组合覆盖：每个判定条件的每一种组合各出现一次
- 路径覆盖：每一条可能的路径至少执行一次

关系：

- 条件组合覆盖＞判定覆盖＞语句覆盖(即如果达到条件组合覆盖，就达到判定覆盖和语句覆盖：如果达到判定覆盖，就达到语句覆盖，下面类似理解)。
- 条件组合覆盖＞条件覆盖。
- 条件覆盖不一定包含判定覆盖、语句覆盖。
- 判定覆盖不一定包含条件覆盖。
- 路径覆盖，判定覆盖＞语句覆盖。

#### 基本路径测试

基于程序圈复杂度产生的测试方法，画出控制流程图，算圈复杂度，找到独立路径并压缩为基本路径集合，根据集合中每条路径设计用例。把复合逻辑表达式拆成单个表达式

圈复杂度用于计算程序的基本的独立路径数目（每条新的独立路径都必须包含一条新的有向边，从入口到出口互不相同的路径数）

- 圈复杂的V(G) = e - n + 2p【边-节点+2*连接区域数，连接区域p通常为1】=P+1【判定节点数+1】
- 一般来说，一个单元模块的最大复杂度V(G)<10

如果把覆盖的路径数压缩到一定限度内，例如程序中的循环体只执行0次和1次，就成为基本路径测试，通过导出基本路径集合，从而设计测试用例，保证这些路径至少通过一次

#### 基于数据流的测试

基于真的数据定义到数据的使用来进行测试，需要找到定义的节点（包括赋值的和比较的）和使用的节点

- 定义节点DEF：输入语句、赋值语句、循环语句和过程调用；变量的值会发生变化的语句
- 使用节点USE：数出语句、赋值语句、条件语句、循环控制语句、过程调用

需要找到所有这段功能代码从哪里开始定义，到哪里开始执行，把路径找出来。什么是定义使用路径（某一变量在最初节点定义到最终节点被使用）、定义清除路径（某一个变量从它的定义节点到使用节点这个过程中没有对这个变量进行二次定义）

#### 循环测试

前提是程序是结构化的。

简单循环测试

- 0次通过循环
- 1次通过循环
- 2次通过循环
- m次通过循环（m<=循环最大次数）
- m-1，m，m+1次通过循环

### 测试的过程

#### 单元测试

<mark>单元测试的内容：5点（简答题）</mark>

- 模块接口的测试
- 局部数据结构的测试
- 独立路径测试
- 错误处理测试
- 边界测试

<mark>单元测试的模块</mark>

- 被测模块：被测试的程序的模块
- 驱动模块：用来模拟测试模块的上一级模块，相当于被测模块的主程序
- 桩模块：用来模拟被测模块工作过程中所调用的模块

单元测试的工具：Junit相关的概念：以插入断言的方式进行测试（类似黑盒测试）

- <mark>针对被测代码或者被测的功能点先创建测试类，然后在类里面创建一个个测试方法。通过实例化对象调用被测方法，用断言进行实际值预期值比较。</mark>

单元测试的方法

- <mark>以白盒测试法为主（覆盖），先静态检查代码是否符合规范，再动态运行代码，检查结果。除了需要验证结果是否正确，还需要检查程序的容错能力、边界值处理等问题。</mark>

#### 集成测试

- 一次性的集成big-bang：把所有通过了单元测试的模块按设计要求一次全部组装起来，然后进行整体测试。时间随变短了但急于求成。
- 渐进地集成
    - 自上而下：从主程序模块开始按深度或广度优先策略边组装边测试
    - 自下而上：从最底层模块开始组装和集成测试
    - 汉堡包：两者进行结合，树状图每层画线，顶层采用自顶向下，底层采用自底向上
相邻的集成：上下三层进行集成
成对集成：先成对再相邻
基于MM路径的集成：MM路径不是可执行路径，描述单元之间的控制转移。

最终得到调用图，然后就会到基本路径测试，找复杂度，找路径，得到测试用例的套路

#### 系统测试

黑盒为主

<mark>对哪些内容进行系统测试（9个）：易用性、国际化本地化、性能、功能、界面、兼容性、安全性、文档、安装</mark>

#### Web系统测试

具体到如Web系统测试中的功能测试包含哪些内容、对cookies里面的内容进行测试属于Web系统测试里面的哪一项的测试（属于功能测试）

- 功能测试
    - 页面内容测试
    - 页面链接测试
    - 表单测试
    - Cookies测试、Session测试
    - 设计语言测试
    - 数据库测试
- 性能测试（负载/压力）
    - 连接速度测试
    - 测试工具  LoadRunner
        - 负载测试
        - 压力测试
    - 网页性能Firefox插件：Yslow，Findbug，PageSpeed
    - Dynatrace检查网页性能
- 可靠性测试：不间断测试，看多久不出错
- 用户界面测试/易用性测试
    - 导航测试
    - 图形测试
    - 内容测试
    - 整体界面测试
- 安全性测试
- 兼容性测试
- 接口测试
    - 服务器接口
    - 外部接口
    - 错误处理

<mark>主要讲了性能测试的含义和怎么做，如所涵盖的含义如压力测试怎么做、负载测试怎么做等</mark>

- 性能测试是通过自动化的测试工具模拟多种正常、峰值以及异常负载条件来对系统的各项性能指标进行测试。
    - 时间性能：软件的一个具体事务的响应时间
    - 空间性能：软件运行时所消耗的系统资源
    - 我让你背1袋米(轻松)
    - 我让你背1袋米，但让你去操场上跑圈，看多久累倒（吃力）
    - 我让你背3袋米去操场跑圈，看多久累倒（极限）
    - 我让你背1袋、2袋、3袋、4袋…发现最多背3袋
- 负载测试让被测系统在其能忍受的压力的极限范围之内连续运行，来测试系统的可靠性。
    - 系统能否处理某个时刻同时访问Web系统/某个页面的用户数量
    - 超过了这个数量，会出现什么现象？
    - 在线数据处理的数量
- 负载/压力测试关注什么？
    - 验证系统能否同一时间响应大量的用户，用户传送大量数据时能否响应，系统能否长时间运行。
        - 瞬间访问高峰
        - 每个用户传送大量数据
        - 长时间使用
- LoadRunner性能测试工具原理：录制+回放模拟用户实际操作场景，监控并分析运行结果。

#### 自动化测试

录制+回放+脚本 是主要的方式

常用的自动化测试的工具，哪些种类，每种有什么工具

- 功能测试工具：QTP
- 性能测试工具：LoadRunner
    - 写脚本或者录制脚本
    - 使用用户自定义参数
    - 场景设计
    - 产生虚拟用户的机制：使用控制器，来控制模拟多少用户。
    - 使用监听器，查看测试结果

