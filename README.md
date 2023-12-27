## 實驗方法
1. 下載code: git clone https://github.com/tcs211/st-gcn-anomaly-detect.git
2. 下載資料及訓練好的模型，下載點列於課堂demo投影片中
3. 安裝下列必要的Environment，安裝openpose python API
4. 修改04_run_pipeline.ipynb中的 openpose 路徑
```
dir_path = r'D:\Projects\anomaly\openpose_full\openpose\build'
sys.path.append(dir_path + r'\python\openpose\Release')
os.environ['PATH']  = os.environ['PATH'] + ';' + dir_path + r'\x64\Release;' +  dir_path + r'\bin;'
model_path = r'D:\Projects\anomaly\openpose_full\openpose\models'
```
5.直接執行04_run_pipeline.ipynb所有code即能重現


## Introduction

A project for the course "AI for anomaly detection" at the National Cheng Kung University.

## Resource

- Openpose python API [https://github.com/CMU-Perceptual-Computing-Lab/openpose]
- ST-GCN [https://github.com/yysijie/st-gcn]
- UR Fall Detection Dataset [http://fenix.ur.edu.pl/~mkepski/ds/uf.html]
- A Framework for Anomaly Identification Applied on Fall Detection [https://ieeexplore.ieee.org/document/9439497]


## Environment

- opencv-python             4.8.1.78      
- python                    3.7.0          
- torch                     1.10.1+cu111       
- torchaudio                0.10.1+cu111         
- torchvision               0.11.2            

## Experiment steps

1. Use openpose to extract the skeleton of the UR Fall Detection Dataset.
1. Use ST-GCN kinects pre-trained model to extract the skeleton features.
1. Use the extracted features to train the autoencoder.
1. Use the trained autoencoder to detect the anomaly.

## Video Example

[![Watch the video](https://img.youtube.com/vi/-YKewWzZIZY/0.jpg)](https://www.youtube.com/watch?v=-YKewWzZIZY)

## Results
```
TP	29
FN	1
TN	35
FP	5

Precision = TP/(TP+FP) = 29/(29+5) = 0.85
Recall = TP/(TP+FN) = 29/(29+1) = 0.96
Accuracy = (TP+TN)/(TP+TN+FP+FN) = (29+35)/(29+35+5+1) = 0.92
F1 = 2*Precision*Recall/(Precision+Recall) = 2*0.85*0.96/(0.85+0.96) = 0.90
```


