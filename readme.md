源码部分

    特征工程：
        原始特征：省份处理；手机品牌处理，nnz（非空列个数）这三个特征前期提升比较大

        离散特征：数值类特征取对应的排名值,对排名特征作等值离散化，增加模型稳定性

        计数特征：统计一个样本有多少取值为0,多少取值为1,...

        比值特征：统计各app和app分类的pv占比，筛选出对旅游者影响较大的app和app分类

        交叉特征：性别，年龄，地域，消费力水平，手机品牌两两交叉，筛选出对旅游者影响较大的app和app分类

        组合特征：根据重要性分数，筛选出前k个特征,两两进行log(xy)变换

        特征选择: 线性分类其主要使用皮卡尔相关系数进行筛选，非线性分类主要使用xgb模型的重要性评分进行筛选

    模型选择：
        LR:baseline

        RF:baseline

        XGB:经验参数：深度：11,min_child_weight:25,scale_pos_weight处理正负类不平衡

        LGB:队友推荐使用DART算法，有兴趣的同学可以了解下

        模型自融合:除了以上的特征工程部分，后期加了型号的频次统计。经验指定筛选个数

        STACK:模型融合，充分利用样本和减少训练方差　