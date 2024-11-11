# DS-5220-Final-Project

## Problem Statement
Bone abnormality detection affects patient care, diagnostic speed, and treatment outcomes. Early and accurate detection helps in diagnosing conditions before they worsen, allowing for timely intervention. Radiographs are often the first line of imaging used to identify musculoskeletal issues, such as fractures, infections, or tumors. Our project aims to detect the presence of abnormality in 7 upper extremity classes based on radiographs of patients.

### Why bone abnormalities?
We have a few different reasons we decided to tackle this project:
1. We wanted the content of our project to address a real-world problem that machine learning can aid.
2. We wanted to work more with images and convolutional neural networks.

To that end, we settled on bone abnormalities for the following reasons:
1. Enhanced Diagnostic Speed and Efficiency: ML-based image classification can analyze radiographs quickly and accurately, which is especially valuable in busy clinical settings where radiologists may have hundreds of images to review. 
2. Improved Accuracy in Detection of Subtle or Rare Conditions: Advanced ML models trained on extensive, diverse datasets can detect patterns in radiographs that even experienced radiologists might overlook, particularly for uncommon or complex cases. 
3. Standardized Diagnosis and Reduced Diagnostic Variability: By offering a standardized analysis, ML models can reduce variability and improve overall diagnostic reliability, ensuring that all patients receive the same high level of care.

## The Dataset
The MURA dataset contains 14,863 musculoskeletal studies of the arm, where each study contains one or more views and is manually labeled by radiologists as either normal or abnormal.
The standard upper extremities include: Elbow, Finger, Forearm, Hand, Humerus, Shoulder, and Wrist.

* Original paper source: https://arxiv.org/pdf/1712.06957
* Dataset sourcing: https://stanfordmlgroup.github.io/competitions/mura/

### The Baseline Model
Baseline model from the original paper (linked above) uses a 169-layer convolutional neural network to detect and localize abnormalities. The model takes as input one or more views for a study of an upper extremity. On each view, the model makes the binary prediction of abnormal if the probability of abnormality for the study is greater than 0.5.

Model was evaluated on the Cohen’s kappa statistic, which expresses the agreement of the model with the gold standard. It was comparable to radiologist performance in detecting abnormalities on finger studies and equivalent on wrist studies, but performed lower than best radiologist performance in detecting abnormalities on elbow, forearm, hand, humerus, shoulder studies, and overall.

## Methodology
We plan to explore this problem from 2 angles. First, determining whether a unified model trained on all of the data performs better or worse than separate models specialized for each body part. Second, whether the best performing of our models is comparable in accuracy to a pre-trained model using transfer learning.

* Data Preprocessing: Data Augmentation, Normalization, Image Resizing
* Model Architecture: Baseline CNN, Specialised sub-models for each class of upper extremity, Transfer learning using pre-trained models
* Evaluation and tuning: Grid search or random search to find the suitable hyperparameters, Record differences in accuracy, F1 score, and speed to abnormality variations across bones
