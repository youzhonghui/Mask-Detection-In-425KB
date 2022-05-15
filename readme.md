## Pruned YOLOv5 Mask Detection Model In 425KB

本项目通过剪枝算法，来获得一个体积极小，推理快速的口罩佩戴的检测模型。基线模型为YOLOv5n，使用[GD剪枝算法](https://arxiv.org/abs/1909.08174)移除了模型87.5%的参数，并保持较好的检测效果（mAP@.5=0.912），数据集来自AIZOO和RMFD，规模大约一万张图片。

模型参数保存到ckps目录下，提供pytorch / onnx / ncnn格式

|  格式 | 模型大小 | 计算量 |
| ------------ | ------------ |------------ |
|  pytorch |  702KB (fp16) | 0.85B (640x640) |
| ncnn | 425KB (fp16) | - |
| onnx  | 1.23MB (fp32)  | - |

其他格式可以使用onnx在[convertmodel](https://convertmodel.com/)上进行转换。

## 如何使用

1. 使用pytorch进行图片/视频推理
```bash
# 输出结果保存在 images/out 中
python yolov5/detect.py --weights ./ckps/pytorch_model.pt --source ./images/test1.png --project ./images/out --line-thickness=2 --hide-conf
```

2. 使用ncnn进行推理 (TODO)

## 实例

![](https://github.com/youzhonghui/Mask-Detection-In-425KB/blob/master/images/out/exp/test1.png?raw=true)