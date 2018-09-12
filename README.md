# 血细胞分类
## 探索数据
对数据进行基本探索，分有四个文件夹，每个文件夹2800张左右图片，每张图片大小为240*320，彩色。
图片大多有倾斜，有黑色背景，可能是干扰项，但是因为有些目标白细胞在边缘处，也不方便做切割。
由于只有训练集，故将训练集分为训练集和测试集，测试集跟训练集是相同分布，故不作处理效果可能更好。
- [参考代码](data_exploration.ipynb)
- [html](data_exploration.html)

## 三种方案
图片分类，首先想到的是用经典CNN模型做迁移学习，
- 通过经典CNN模型提取特征向量，在用简单神经网络训练新的分类器。测试集acc:0.993975903614457
  - [参考代码](transfer_learning_merged_features.ipynb)
  - [html](transfer_learning_merged_features.html)
- 通过经典CNN模型fine-tuning,去掉分类层加上4分类器，锁定原始模型所有参数训练分类器参数，再放开一些层的参数进行微调，（经典CNN模型大多都很大，参数很多，调参太慢，放弃了）
  - [参考代码](fine_tuning.ipynb)
  - [html](fine_tuning.html)
- 除了迁移学习，也可以自己搭一个CNN模型从头训练 -测试集acc:0.9728915662650602
  - [参考代码](customized_cnn_model.ipynb)
  - [html](customized_cnn_model.html)
