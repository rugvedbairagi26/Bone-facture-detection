# Bone-facture-detection

🦴 Bone Fracture Detection in X-ray Images using YOLOv8
📌 Overview

This project focuses on automatic detection of bone fracture regions in X-ray images using deep learning–based object detection.
The goal is to localize fracture regions by predicting bounding boxes, rather than only classifying images as fractured or normal.

The project is designed as a research-oriented computer vision study, emphasizing:

dataset understanding

controlled experiments

evaluation metrics

qualitative error analysis

📂 Dataset

FracAtlas – Fractured X-ray Images Dataset

X-ray images of different body parts (hand, leg, hip, shoulder)

Annotated with bounding boxes around fracture regions

YOLO-formatted annotations

Dataset split:

Train

Validation

Test

The dataset primarily contains fractured images and is used for localization, not screening.

🧠 Methodology
1. Problem Formulation

Task: Object Detection

Class: fracture

Output: Bounding box around fracture region

2. Models Used

Multiple YOLOv8 configurations were trained to perform experimental comparison:

Model	Image Size	Purpose
YOLOv8n	640	Baseline lightweight model
YOLOv8s	640	Effect of larger model capacity
YOLOv8n	960	Effect of higher image resolution
3. Training Setup

Framework: Ultralytics YOLOv8

Optimizer: Default YOLOv8 settings

Loss: YOLO detection loss

Hardware: NVIDIA Tesla T4 (Kaggle GPU)

📊 Results
Quantitative Evaluation (Test Set)
Model	Img Size	Precision	Recall	mAP@0.5	mAP@0.5:0.95
YOLOv8n	640	0.659	0.328	0.406	0.163
YOLOv8s	640	0.817	0.403	0.490	0.187
YOLOv8n	960	0.755	0.413	0.484	0.202
Key Observations

Increasing model size improves precision and overall accuracy.

Increasing image resolution improves recall and localization quality.

Fracture detection behaves as a small-object, low-contrast detection problem.

🔍 Error Analysis (Qualitative)

Visual inspection of predictions revealed the following failure modes:

Missed fractures often occur when:

fracture lines are very thin (hairline fractures)

contrast between bone and fracture is low

fractures lie near joints or overlapping structures

Low-confidence detections occur in subtle fracture regions.

Challenging cases include:

presence of casts

metal implants

complex anatomical overlaps

These observations explain why higher-resolution input improves recall.

Example outputs are provided in the results/ directory.

📁 Repository Structure
Bone-Fracture-Detection/
│
├── bone_fracture_detection.ipynb   # Clean notebook (no outputs)
├── results/
│   ├── correct_detection_midshaft_tibia.jpg
│   ├── low_confidence_hairline_fracture.jpg
│   ├── missed_fracture_joint_region.jpg
│   └── challenging_case_metal_implant.jpg
├── README.md

⚠️ Limitations

Dataset lacks normal X-ray images, so fracture screening is not addressed.

Bounding boxes provide coarse localization; fracture segmentation would be more precise.

Dataset size is limited, which may affect generalization.

This project should be considered a proof-of-concept and not a clinical diagnostic system.

🚀 Future Work

Fracture segmentation instead of bounding boxes

Inclusion of normal X-ray images for screening

Bone-specific performance analysis

Advanced preprocessing for low-contrast enhancement

👨‍🎓 Author

Rugved Prashant Bairagi
B.E. Computer Engineering (2nd Year)
Interested in Computer Vision, Medical Imaging, Robotics & AI

📜 Disclaimer

This project is intended for academic and research purposes only and should not be used for medical diagnosis.
