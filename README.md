# Diabetic Retinopathy Lesion Detection using YOLOv8

This project fine-tunes a YOLOv8 object detection model to identify four types of retinal lesions (Microaneurysms, Haemorrhages, Hard Exudates, Soft Exudates) from fundus images using the IDRiD dataset.

## Dataset

- **Source:** IDRiD (MICCAI 2018)
- **Used:** A. Segmentation – 54 train, 27 validation images
- **Format:** TIFF masks → Converted to YOLO bounding boxes using HSV thresholding + OpenCV contours

## Model

- Base model: `yolov8m.pt`
- Input size: 1024×1024
- Augmentation: On
- Epochs: 250 (early stopped)
- Evaluation metric: mAP@0.5 and mAP@0.5:0.95

## Results

| Metric             | Value   |
|--------------------|---------|
| mAP@0.5            | 0.383   |
| mAP@0.5:0.95       | 0.169   |
| Best Class (SE)    | AP@0.5 = 0.61 |


## Limitations

- Small dataset size led to lower generalizability
- Highly imbalanced lesion distribution (e.g., only 38 SE lesions)
- Performance could improve by including IDRiD Sets B & C or other DR datasets

## Future Work

- Apply to larger datasets
- Compare RetinaNet, Faster R-CNN
- Use SAM for automatic box extraction from segmentation masks
