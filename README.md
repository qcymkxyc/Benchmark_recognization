# Benchmark_recognization
一个benchmark数据的损伤识别

## 数据集介绍
>spring_beam.zip includes a folder spring_beam, which includes 100 files acc_xxx.mat.
These are time series from 47 accelerometers with 2859 samples. The variable is y(47x2859).
Measurements 1-50 undamaged, 51-60 damage 1, 61-70 damage 2, 71-80 damage 3, 81-90 damage 4, 91-100 damage 5.

<br>
** 数据琴行图如下**：
>![](images/Data_Violin.png)
<br>


##实验步骤

>该实验共分为3部分

>    1. 基于过滤式的特征提取（指标用信息增益率）
>    2. 利用ARMA模型的自相关函数以及偏自相关函数确定LSTM步数
>    3. 利用双向LSTM作损伤识别


## 1. 基于过滤式的特征提取
这里用信息增益率作为过滤式特征选择的指标。主要是考虑到结构数据很多时候离散数据和连续数据兼有，用互信息又会被类别多少左右，所以参造C4.5算法对ID3的改进，这里选择信息增益率。

用信息增益率（用熵指标应该都会遇到）面临的另一个问题就是连续数据的处理。这里有两个思路：

1. 将数据离散化，利用离散分布建模
2. 直接用连续分布建模

### 1.1 数据离散化方式
>基本参照C4.5算法的离散化方式
### 1.2 连续分布建模
>信息增益率可以看成两部分：特征和类别的互信息（分子）以及特征的信息熵（分母）。但其实仅需要对分子建模，分母用全概率公式即可算得。

>
