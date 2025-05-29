# SBERT Semantic Similarity and Plagiarism Detection

本项目基于 [Sentence-BERT (SBERT)]框架，结合句向量特征增强与逻辑回归分类器，构建了一个用于语义相似度评估与问句抄袭检测的完整系统。

项目支持加载本地 MiniLM-L6-v2 预训练模型，对 Quora Question Pairs（QQP）数据集进行语义微调，并使用多维向量组合特征训练下游分类器，适用于语义匹配、文本去重与语义相似性分析等任务场景。

---

## ✨ 功能亮点

- ✅ 使用本地 SBERT 模型生成高质量句向量
- ✅ 支持 CosineSimilarityLoss 微调 SBERT 表达能力
- ✅ 构建多种句向量组合特征（差值、乘积、距离等）
- ✅ 支持逻辑回归分类器进行判别
- ✅ 支持困难负样本（Hard Negatives）筛选增强模型边界学习
- ✅ 实现余弦相似度与分类器输出的融合判别策略
- ✅ 支持训练过程可视化（损失曲线 PNG）
- ✅ 支持交互式命令行检测与批量预测保存

---

## 📁 文件结构# Semantic-recognition
├── final.py # 主程序代码
├── train_loss_curve.png # 微调损失曲线图
├── DATA # QQP 数据集
    ├──train.tsv 
    ├── dev.tsv 
    ├──test.tsv 
├── finetuned_sbert_model # 微调后的 SBERT 模型文件夹
├──paraphrase-MiniLM-L6-v2 # 预训练的 SBERT 模型文件夹
└── README.md # 项目说明文件

## 环境配置说明
Python 3.7 及以上（建议使用 Python 3.8+）
sentence-transformers>=2.2.2
scikit-learn>=1.0
torch>=1.10
numpy>=1.21
pandas>=1.3
matplotlib>=3.4

## 代码运行流程说明
1.加载训练、验证与测试集（TSV 格式）
2.加载或微调 SBERT 模型
3.计算句向量，构造特征向量
4.两种相似度判别策略评估
5.测试集预测并保存
6.命令行交互检测
