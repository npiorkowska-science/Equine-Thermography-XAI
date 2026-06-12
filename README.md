Overview

This repository contains the complete analytical workflow used in the study:

Beyond Classification: Expert-Validated Explainable AI for Thermographic Detection and Hotspot Localization of Distal Forelimb Musculoskeletal Pathology in Horses

The project evaluates whether machine-learning and deep-learning models can distinguish healthy horses from horses affected by distal forelimb musculoskeletal pathology using infrared thermographic images. In addition, explainable artificial intelligence (XAI) methods are quantitatively validated against expert-defined thermographic hotspot annotations.

The workflow includes:

Dataset inventory and quality control
Expert hotspot annotation processing
Inter-rater agreement analysis
Image preprocessing
Classical thermographic feature extraction
Machine-learning model development
Deep-learning model development (ResNet18)
Explainable AI (Grad-CAM and Integrated Gradients)
Expert-validated hotspot localization analysis
Statistical evaluation and uncertainty quantification
Study Design

The study follows a predefined analytical workflow consistent with:

STARD 2015
TRIPOD+AI
CLAIM

The primary endpoint is image-level discrimination between healthy and pathological horses.

The primary evaluation metric is:

ROC-AUC on an independent locked test set

Secondary endpoints include:

Accuracy
Sensitivity
Specificity
Precision
F1-score
PR-AUC
Matthews Correlation Coefficient (MCC)
Brier Score
Calibration performance

The explainability endpoint evaluates correspondence between model attention maps and expert-defined thermographic hotspots.

Repository Structure
Project Initialization
Notebook	Purpose
00_project_setup_and_preregistration.ipynb	Project setup, configuration, reproducibility settings, preregistered workflow definitions
Dataset Preparation
Notebook	Purpose
01_dataset_inventory_and_metadata_qc.ipynb	Dataset inventory, metadata verification, consistency checks
02_annotation_import_and_hotspot_dataset_build.ipynb	Import of expert annotations and hotspot dataset construction
02b_expert_agreement_analysis.ipynb	Inter-rater agreement analysis (Cohen’s κ, IoU, point agreement)
03_image_quality_control_and_exclusion_report.ipynb	Image quality control and exclusion assessment
04_group_split_and_leakage_checks.ipynb	Dataset partitioning and information leakage prevention
Image Processing
Notebook	Purpose
05_preprocessing_segmentation.ipynb	Thermographic image preprocessing and segmentation
Classical Machine Learning Pipeline
Notebook	Purpose
06_classical_feature_engineering.ipynb	Extraction of handcrafted thermographic biomarkers
07_classical_model_development_and_cv.ipynb	Classical model training, cross-validation, model selection
08_baseline_classical_features.ipynb	Baseline thermographic feature analysis
16_classical_feature_importance.ipynb	Logistic regression feature importance analysis
Deep Learning Pipeline
Notebook	Purpose
09_cnn_model_transfer_learning.ipynb	ResNet18 transfer-learning model development
10_deep_model_ablation_and_robustness.ipynb	Ablation studies and robustness analyses
Explainable AI
Notebook	Purpose
11_gradcam_generation.ipynb	Grad-CAM generation and visualization
18_integrated_gradients_xai.ipynb	Integrated Gradients attribution analysis
Localization and Explainability Validation
Notebook	Purpose
12_hotspot_localization_evaluation.ipynb	Quantitative evaluation of hotspot localization performance
17_localization_bootstrap_confidence_intervals.ipynb	Bootstrap confidence intervals for localization metrics
Model Evaluation
Notebook	Purpose
13_error_analysis_and_case_review.ipynb	Error analysis and misclassification review
14_statistical_analysis_and_confidence_intervals.ipynb	Statistical analyses and uncertainty estimation
15_extended_model_validation_calibration.ipynb	Calibration analysis and extended validation
Dataset

The study dataset consists of:

347 thermographic images
347 individual horses
257 healthy horses
90 pathological horses

Each horse contributes exactly one image to prevent subject-level information leakage.

The dataset was partitioned into:

Subset	Images
Training	242
Validation	52
Test	53
Deep Learning Model
Architecture
ResNet18
ImageNet-pretrained initialization
Transfer learning
Binary classification output
Input
Thermographic pseudocolor images
Resolution: 224 × 224 pixels
Training
Batch size: 16
Epochs: 10
Model selection based on validation ROC-AUC
Explainability Methods
Primary Method
Grad-CAM
Sensitivity Analysis
Integrated Gradients

Localization performance was evaluated using:

Pointing-game accuracy
CAM-cell overlap accuracy
CAM-cell IoU
Distance-based metrics
Border activation fraction
Reproducibility

The workflow was executed using:

Python 3.12
NumPy
Pandas
Scikit-learn
PyTorch
Torchvision
OpenCV
Matplotlib

All analyses were performed using:

random_seed = 42

The independent test set remained locked throughout model development and was not used for:

feature engineering
hyperparameter optimization
threshold selection
model selection
explainability method selection
Data Availability

The thermographic dataset is available from the corresponding author upon reasonable request.

Following publication, the curated dataset and associated metadata will be deposited in a public repository.

Code Availability

All source code required to reproduce the analyses reported in the manuscript is contained in this repository.

Citation

If you use this code or build upon this work, please cite:

Piórkowska N., Ostromęcki A., Soroko-Dubrovina M., Dobrowolski M.

Beyond Classification: Expert-Validated Explainable AI for Thermographic Detection and Hotspot Localization of Distal Forelimb Musculoskeletal Pathology in Horses.

(under review)

License

This repository is provided for academic and research purposes. Please cite the original publication when using the code or derived analyses.
