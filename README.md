具体方案说明相见方案说明书

执行顺序：
./main
./opt
./opt2
./work

根据参数不同，结果会有一定波动，最终大概的效果：
效率: 0.400+, 最好跑到过0.4015+ （远高于冠军队伍的效率值: 0.377）
超时量: < 1e-3，很多参数下都能跑到0
方差: 一般在0.37左右

main.cpp: 初始解生成
算法流程：按时间顺序遍历每一个任务，用当前空闲人员和任务建立二分图。二分图边权为将该任务分配给某一专家后，会在哪个时间点完成。
用最小费用流算法求二分图最小匹配，按匹配来分配任务
程序中有很多参数都可以调整，如任务的聚集量、人员的聚集量等

opt.cpp, opt2.cpp: 第一次调优
算法流程：读入第一步中生成的初始解，不断尝试下列调优策略：改派执行任务的专家，交换两个专家的任务
方差公式拆开之后，O(1)时间维护每一项 （具体看代码）
CheckTime函数用于卡时，最终结果取决于时间多少
（以上两步中，均不考虑任务超时问题）

work.cpp: 第二次调优
在这一步中，首先加入空闲专家填补超时的时间
然后不断尝试下列调优策略：改派执行任务的专家，任务时间前移，将某一任务的前（或后）一部分切到别的专家
CheckTime函数用于卡时，最终结果取决于时间多少

比赛经验总结：
大家好，我是江离数据挖掘俱乐部的江离.重楼。很高兴能参加这次的服务调度大赛，在这次比赛中，我充分发扬了俱乐部的优秀传统，在算法分大幅领先的情况下仍然被翻盘。
这次比赛在赛制上做出了不少革新。众所周知，在早期的数据挖掘竞赛中，客观分数是决定排名的唯一标准(现在还有一些陈腐的平台，如kaggle，依然遵守着这一标准)。这种单一维度的评判太过片面，给一些擅长调优性能指标，实际算法却稀松平常的投机选手(如我们俱乐部的姬哀选手)可乘之机。因此，国内的竞赛中大多都加入了答辩机制，在答辩中，那些使用了朴素算法(例如规则，暴力)的选手就会原形毕露，而真正擅长新颖算法的选手，即使分数偏低，也能在答辩中脱颖而出成功翻盘。
尽管如此，大多数比赛的决赛入围资格仍由客观分数决定，答辩时如果名次变化太大也容易引起选手的不满，擅长调优指标的投机选手仍然会占有优势，这种赛制并不利于发掘那些对业务深入理解、答辩水平出众的有能之士。因此，这次比赛增多了主观性评价指标，在决赛前增加了解决方案评分和线上路演评分，提前筛除了一些客观分数高却不理解业务的选手。同时，通过对榜上评分线性归一化尽量避免了客观分数差距过大。最终的结果也十分合理，虽然冠军队伍前期发挥不力，客观成绩比我的第一次提交还低很多，但凭借着对业务的深刻理解和对症下药的优秀算法，赢得了当之无愧的荣誉。

回顾一下这次被翻盘的过程，希望大家能够引以为戒，在之后的比赛中赛出好成绩。
刷榜阶段
在这一阶段中，我的时间分配十分不合理，大部分时间都投入在性能指标的提高上。从第一次提交的216分到最后一次提交的218分，大概增加了上千行代码，虽然在我看来是很大的改进，但是对最终成绩的提高其实微不足道，可能不如在解决方案里多提及一些业务场景的思考。这次的赛制为我敲响了警钟，在以往的比赛中我总是想投机取巧，为了一点点的算法分数绞尽脑汁，却不去思考背后的业务逻辑和算法的创新性，最终只能自尝被翻盘的苦果。
答辩阶段
答辩阶段分数差距极大，体现出我和冠军队伍完全不在一个水平线上。如果不是靠着客观成绩上的投机取巧，我根本没有和他们同场竞技的资格。
由于答辩阶段没有公布评分细节，我无从得知到底是哪方面因素导致了这么大的差距，我能做的也许只有回小学重新学习语文吧。
展望未来
很高兴看到天池在赛制上做的一系列探究，目前的比赛也朝着主观性越来越强的方向不断进步着。
赛制必定带动选手的发展，以后的选手们看到客观成绩在达到一定值之后，再往上提高的困难程度和最终分数的提高量完全不成比例，就会自然而然地将重心转移到对业务和算法本身的思考上。排行榜这种老旧落后的产物也会慢慢淘汰，以后的比赛选手可能只需要提交一个baseline，就可以专注答辩，尽情地头脑风暴，比拼真才实学。那些只会刷榜的投机选手，终将淡出数据竞赛的舞台。
大江东去浪淘尽。无能的刷榜选手，或许曾经在数据竞赛的舞台上有过自己的时代，但终将被历史的车轮轧过。数风流人物，还看今朝。