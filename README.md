# DSER-Net: Deep Semantic Enhancement and Regional Complementary Refinement Network

Official implementation of **DSER-Net**, a deep learning framework for 3D brain tumor segmentation using multimodal magnetic resonance imaging (MRI).

## 1. Overview

DSER-Net is designed to improve brain tumor segmentation by enhancing deep semantic representations and refining regional predictions.

The proposed framework incorporates three complementary components:

- **Spatial-Preserving Bi-Mamba (SP-BiM):** Combines Morton-order serialization, bidirectional state-space modeling, and channel-wise gated fusion to enhance contextual representation while preserving spatial structure.
- **3D Dual-Supervised Reverse Attention (3D-DSRA):** Employs complementary foreground and background responses to refine skip-connection features and improve regional discrimination.
- **Vector Quantization Constraint (VQC):** Uses a learnable codebook to regularize deep semantic representations.

The network follows a 3D encoder-decoder architecture and is implemented based on the nnU-Net framework.

## 2. Network Architecture

The overall architecture of DSER-Net consists of the following components:

1. A 3D U-Net-based encoder-decoder backbone.
2. SP-BiM modules for enhanced semantic feature modeling.
3. 3D-DSRA modules for complementary foreground-background refinement.
4. A vector quantization constraint for deep feature regularization.

The proposed framework is designed for multimodal MRI brain tumor segmentation.


## 3. Requirements

The implementation is based on Python, PyTorch, and nnU-Net v2.

The main dependencies include:

- Python
- PyTorch
- CUDA
- nnU-Net v2
- Mamba-related dependencies
- NumPy
- Other required packages

Please refer to `requirements.txt` for the specific dependency versions.

## 4. Datasets

DSER-Net was evaluated using the following publicly available brain tumor MRI datasets:

### BraTS2021
https://www.med.upenn.edu/cbica/brats2021/

### BraTS-Africa
https://www.cancerimagingarchive.net/collection/brats-africa/

### BraTS-PEDs 2023
https://www.synapse.org/Synapse:syn51156910/wiki/622461

The datasets are not redistributed in this repository. Users should obtain the data directly from the corresponding official repositories and comply with their access and usage policies.

## 5. Data Preparation

The datasets should be prepared according to the nnU-Net v2 data format.

Please configure the dataset information, modality channels, segmentation labels, and preprocessing settings according to the corresponding dataset specifications.

For external evaluation, the original segmentation labels should be mapped to the corresponding evaluation regions (WT, TC, and ET) before calculating the metrics.

## 6. Training

The model is trained using the customized nnU-Net v2 trainer.

Example command:

```bash
nnUNetv2_train DATASET_ID 3d_fullres FOLD \
-tr DSER-NetTrainer
```

Replace `DATASET_ID` and `FOLD` with the corresponding dataset identifier and cross-validation fold.

Please ensure that the custom network modules and trainer are correctly installed and accessible to nnU-Net v2 before training.

## 7. Inference and Evaluation

The trained model can be used to generate segmentation predictions for 3D multimodal MRI scans.

The segmentation performance is evaluated using commonly adopted metrics, including:

- Dice Similarity Coefficient (Dice)
- 95th-percentile Hausdorff Distance (HD95)


## 8. Reproducibility

For reproducibility, users should refer to the provided network implementation, customized trainer, training configurations, and dependency specifications.

The reported results were obtained using five-fold cross-validation on BraTS2021.

Exact reproduction may depend on the software environment, GPU hardware, preprocessing settings, and random seeds.


