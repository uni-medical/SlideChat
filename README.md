# SlideChat: A Multimodal Generative AI Assistant for Whole-Slide Computational Pathology


> **Note**
>
> This repository provides the official code for SlideChat. The expanded study, published in *Nature Cancer*, substantially extends our original CVPR 2025 work with a larger instruction dataset, broader expert-reviewed evaluation, and additional pathology tasks across cancer types.



# Release

We release **SlideChat**, **SlideInstruction**, and **SlideBench** as open-source resources, hoping to facilitate research and development in computational pathology.
- **SlideChat**: The first large vision-language assistant for whole-slide pathology image analysis, capable of generating comprehensive descriptions and contextually relevant responses.
- **SlideInstruction**: The largest comprehensive WSI instruction-following dataset, derived from pathology reports..
- **SlideBench**: A WSI multimodal benchmark including SlideBench-Caption/Report (TCGA, CPTAC, HISTAI) and SlideBench-Closed(VQA-TCGA, VQA-BCNB, VQA-CPTAC, VQA-HISTAI).
Before open‑sourcing, SlideBench‑VQA‑TCGA underwent a second round of expert review with pathologists, further enhancing data quality. The initial version covers 10 cancer types with 1,494 samples. **We later expanded it to 31 additional cancer types, rigorously validated by experts, yielding 3,176 samples (SlideBench‑VQA‑TCGA.csv).** SlideChat achieved an accuracy of 75.23% on the initial version and 74.12% on the expanded version.


The results below correspond to the expanded journal version of SlideChat.

### Closed-Ended Question Answering

| Dataset | Task                              |         SlideChat |            GPT-4o |         MedDr |   Quilt-LLaVA |     LLaVA-Med |
| :------ | :-------------------------------- | ----------------: | ----------------: | ------------: | ------------: | ------------: |
| TCGA    | Histopathological Changes         | **0.859 ± 0.019** |     0.481 ± 0.027 | 0.533 ± 0.027 | 0.311 ± 0.025 | 0.292 ± 0.025 |
| TCGA    | Cytomorphological Characteristics | **0.843 ± 0.040** |     0.584 ± 0.052 | 0.690 ± 0.050 | 0.180 ± 0.042 | 0.216 ± 0.045 |
| TCGA    | Tissue Architecture               | **0.836 ± 0.019** |     0.614 ± 0.026 | 0.601 ± 0.025 | 0.385 ± 0.026 | 0.465 ± 0.026 |
| TCGA    | Tumor Characteristics             | **0.717 ± 0.035** |     0.607 ± 0.039 | 0.612 ± 0.039 | 0.259 ± 0.034 | 0.306 ± 0.035 |
| TCGA    | Disease Classification            | **0.796 ± 0.015** |     0.558 ± 0.017 | 0.489 ± 0.018 | 0.271 ± 0.015 | 0.299 ± 0.016 |
| TCGA    | Disease Detection                 | **0.765 ± 0.067** |     0.371 ± 0.076 | 0.746 ± 0.066 | 0.444 ± 0.073 | 0.372 ± 0.073 |
| TCGA    | Differential Diagnosis            | **0.749 ± 0.039** |     0.532 ± 0.044 | 0.547 ± 0.044 | 0.260 ± 0.040 | 0.317 ± 0.043 |
| TCGA    | Staging                           | **0.656 ± 0.022** |     0.606 ± 0.022 | 0.309 ± 0.022 | 0.185 ± 0.018 | 0.253 ± 0.020 |
| TCGA    | Grading                           | **0.604 ± 0.020** |     0.494 ± 0.020 | 0.406 ± 0.020 | 0.140 ± 0.014 | 0.171 ± 0.016 |
| TCGA    | Treatment Guidance                | **0.774 ± 0.051** |     0.751 ± 0.054 | 0.761 ± 0.053 | 0.397 ± 0.058 | 0.514 ± 0.061 |
| TCGA    | Biomarker Analysis                | **0.738 ± 0.083** |     0.591 ± 0.095 | 0.594 ± 0.094 | 0.588 ± 0.099 | 0.589 ± 0.095 |
| TCGA    | Risk Factors                      | **0.713 ± 0.084** |     0.678 ± 0.087 | 0.640 ± 0.092 | 0.504 ± 0.097 | 0.713 ± 0.086 |
| TCGA    | Prognostic Assessment             | **0.695 ± 0.075** |     0.614 ± 0.076 | 0.587 ± 0.078 | 0.230 ± 0.067 | 0.362 ± 0.078 |
| TCGA    | **Overall**                       | **0.741 ± 0.008** |     0.557 ± 0.009 | 0.490 ± 0.009 | 0.256 ± 0.008 | 0.298 ± 0.008 |
| BCNB    | Tumor Subtype Classification      | **0.894 ± 0.009** |     0.368 ± 0.015 | 0.387 ± 0.015 | 0.560 ± 0.015 | 0.437 ± 0.015 |
| BCNB    | ER Status Classification          |     0.791 ± 0.013 | **0.819 ± 0.012** | 0.309 ± 0.014 | 0.480 ± 0.015 | 0.481 ± 0.015 |
| BCNB    | PR Status Classification          | **0.703 ± 0.014** |     0.533 ± 0.015 | 0.230 ± 0.013 | 0.445 ± 0.015 | 0.438 ± 0.015 |
| BCNB    | HER2 Status Classification        | **0.768 ± 0.013** |     0.687 ± 0.014 | 0.625 ± 0.015 | 0.295 ± 0.015 | 0.287 ± 0.015 |
| BCNB    | **Overall**                       | **0.789 ± 0.006** |     0.602 ± 0.007 | 0.388 ± 0.007 | 0.445 ± 0.008 | 0.411 ± 0.008 |
| CPTAC   | CM Subtype                        | **0.487 ± 0.067** |     0.218 ± 0.053 | 0.418 ± 0.063 | 0.181 ± 0.051 | 0.331 ± 0.062 |
| CPTAC   | LSCC Subtype                      | **0.681 ± 0.060** |     0.500 ± 0.066 | 0.414 ± 0.063 | 0.085 ± 0.036 | 0.068 ± 0.033 |
| CPTAC   | LUAD Subtype                      | **0.418 ± 0.066** |     0.370 ± 0.064 | 0.236 ± 0.055 | 0.215 ± 0.053 | 0.134 ± 0.045 |
| CPTAC   | UCEC Subtype                      | **0.482 ± 0.067** |     0.234 ± 0.054 | 0.364 ± 0.063 | 0.200 ± 0.051 | 0.200 ± 0.051 |
| CPTAC   | **Overall**                       | **0.517 ± 0.033** |     0.330 ± 0.030 | 0.358 ± 0.031 | 0.170 ± 0.024 | 0.183 ± 0.025 |
| HISTAI  | Breast Disease Classification     | **0.795 ± 0.020** |     0.484 ± 0.024 | 0.444 ± 0.024 | 0.336 ± 0.023 | 0.314 ± 0.022 |
| HISTAI  | Skin Disease Classification       | **0.736 ± 0.031** |     0.449 ± 0.036 | 0.272 ± 0.031 | 0.243 ± 0.031 | 0.116 ± 0.023 |
| HISTAI  | Colorectum Disease Classification | **0.695 ± 0.036** |     0.634 ± 0.038 | 0.570 ± 0.040 | 0.506 ± 0.040 | 0.434 ± 0.041 |
| HISTAI  | **Overall**                       | **0.761 ± 0.016** |     0.505 ± 0.018 | 0.387 ± 0.018 | 0.354 ± 0.017 | 0.320 ± 0.017 |

### Report Generation

METEOR scores on the SlideBench-Report:

| Dataset | Cancer Type |         SlideChat |          HistoGPT |         PRISM |
| :------ | :---------- | ----------------: | ----------------: | ------------: |
| TCGA    | ACC         | **0.153 ± 0.050** |     0.079 ± 0.009 | 0.007 ± 0.000 |
| TCGA    | BLCA        | **0.254 ± 0.004** |     0.095 ± 0.003 | 0.028 ± 0.001 |
| TCGA    | BRCA        | **0.250 ± 0.003** |     0.096 ± 0.002 | 0.024 ± 0.001 |
| TCGA    | CESC        | **0.147 ± 0.004** |     0.104 ± 0.004 | 0.024 ± 0.002 |
| TCGA    | CHOL        | **0.246 ± 0.017** |     0.111 ± 0.011 | 0.021 ± 0.003 |
| TCGA    | COAD        | **0.258 ± 0.005** |     0.099 ± 0.004 | 0.032 ± 0.002 |
| TCGA    | DLBC        | **0.109 ± 0.014** |     0.082 ± 0.008 | 0.031 ± 0.006 |
| TCGA    | ESCA        | **0.143 ± 0.006** |     0.118 ± 0.007 | 0.039 ± 0.004 |
| TCGA    | GBM         | **0.235 ± 0.010** |     0.093 ± 0.007 | 0.012 ± 0.001 |
| TCGA    | HNSC        | **0.224 ± 0.005** |     0.097 ± 0.003 | 0.039 ± 0.002 |
| TCGA    | KICH        | **0.187 ± 0.007** |     0.084 ± 0.004 | 0.013 ± 0.001 |
| TCGA    | KIRC        | **0.200 ± 0.004** |     0.089 ± 0.003 | 0.025 ± 0.001 |
| TCGA    | KIRP        | **0.202 ± 0.005** |     0.088 ± 0.004 | 0.017 ± 0.001 |
| TCGA    | LGG         | **0.231 ± 0.005** |     0.088 ± 0.003 | 0.015 ± 0.001 |
| TCGA    | LIHC        | **0.198 ± 0.007** |     0.108 ± 0.003 | 0.023 ± 0.001 |
| TCGA    | LUAD        | **0.245 ± 0.005** |     0.100 ± 0.003 | 0.020 ± 0.001 |
| TCGA    | LUSC        | **0.269 ± 0.005** |     0.106 ± 0.003 | 0.033 ± 0.002 |
| TCGA    | MESO        | **0.163 ± 0.007** |     0.098 ± 0.009 | 0.016 ± 0.002 |
| TCGA    | OV          | **0.121 ± 0.011** |     0.087 ± 0.008 | 0.020 ± 0.003 |
| TCGA    | PAAD        | **0.143 ± 0.007** |     0.090 ± 0.005 | 0.029 ± 0.003 |
| TCGA    | PCPG        | **0.198 ± 0.008** |     0.116 ± 0.005 | 0.015 ± 0.001 |
| TCGA    | PRAD        | **0.196 ± 0.005** |     0.093 ± 0.003 | 0.026 ± 0.001 |
| TCGA    | READ        | **0.265 ± 0.007** |     0.106 ± 0.006 | 0.027 ± 0.002 |
| TCGA    | SARC        | **0.167 ± 0.009** |     0.088 ± 0.005 | 0.011 ± 0.001 |
| TCGA    | SKCM        | **0.200 ± 0.014** |     0.113 ± 0.010 | 0.016 ± 0.002 |
| TCGA    | STAD        | **0.151 ± 0.006** |     0.096 ± 0.003 | 0.032 ± 0.002 |
| TCGA    | TGCT        | **0.163 ± 0.012** |     0.115 ± 0.006 | 0.014 ± 0.003 |
| TCGA    | THCA        | **0.191 ± 0.004** |     0.101 ± 0.003 | 0.025 ± 0.001 |
| TCGA    | THYM        | **0.241 ± 0.007** |     0.109 ± 0.005 | 0.013 ± 0.002 |
| TCGA    | UCEC        | **0.198 ± 0.006** |     0.092 ± 0.002 | 0.022 ± 0.001 |
| TCGA    | UCS         | **0.206 ± 0.008** |     0.075 ± 0.006 | 0.012 ± 0.001 |
| TCGA    | **Overall** | **0.214 ± 0.001** |     0.097 ± 0.012 | 0.025 ± 0.000 |
| CPTAC   | CCRCC       | **0.170 ± 0.007** |     0.114 ± 0.009 | 0.096 ± 0.006 |
| CPTAC   | LSCC        |     0.151 ± 0.013 | **0.156 ± 0.018** | 0.061 ± 0.013 |
| CPTAC   | LUAD        |     0.114 ± 0.008 | **0.144 ± 0.013** | 0.050 ± 0.008 |
| CPTAC   | UCEC        |     0.118 ± 0.004 | **0.140 ± 0.011** | 0.024 ± 0.008 |
| CPTAC   | **Overall** | **0.140 ± 0.005** |     0.139 ± 0.020 | 0.059 ± 0.005 |
| HISTAI  | Breast      | **0.119 ± 0.002** |     0.058 ± 0.001 | 0.012 ± 0.001 |
| HISTAI  | Skin        | **0.084 ± 0.002** |     0.079 ± 0.002 | 0.022 ± 0.001 |
| HISTAI  | Colorectum  | **0.107 ± 0.002** |     0.063 ± 0.001 | 0.022 ± 0.001 |
| HISTAI  | **Overall** | **0.106 ± 0.001** |     0.065 ± 0.001 | 0.018 ± 0.001 |

## Installation

### Environment Setup
This project is built upon [**Xtuner**](https://github.com/InternLM/xtuner). To get started:

```bash
conda create --name xtuner-env python=3.10 -y
conda activate xtuner-env
git clone https://github.com/uni-medical/SlideChat.git
cd SlideChat
pip install -e .
```
### Dependencies
- Python >= 3.10
- [Xtuner](https://github.com/InternLM/xtuner)
- [DeepSpeed](https://github.com/microsoft/DeepSpeed)
- Pytorch

Please refer to `requirements.txt` and `environment.yaml` for the complete list of dependencies.

## Pre-requisites

Download the JSON file containing WSI IDs (TCGA) and conversation data from the [Dataset](https://huggingface.co/datasets/General-Medical-AI/SlideChat). The input image file is in CSV format and contains 512-dimensional feature representations for all patches within the WSI. Example files are provided in the ./dataset/ folder. For slide downloading and processing, please refer to [CLAM](https://github.com/mahmoodlab/CLAM) and [DSMIL](https://github.com/binli123/dsmil-wsi).

## Training

SlideChat serializes each input WSI into a sequence of patches, converting each into visual embeddings with a patch-level encoder [CONCH](https://github.com/mahmoodlab/CONCH). A slide-level encoder then interacts with these features to generate contextual embeddings. Then, a multimodal projector maps the visual features from the slide-level encoder into a unified space, aligned seamlessly with the LLM. SlideChat was trained for two stages: (1) Cross-Domain Alignment: SlideChat is trained to generate descriptive captions using WSI-caption pairs from SlideInstruction. Specifically, only the slide-level encoder and projection are updated, while the patch-level encoder and LLM weights remain fixed; (2) Visual Instruction Learning: we utilize WSI VQAs from SlideInstruction, allowing the slide encoder, projection layer, and large language model components to be fully trainable to ensure comprehensive adaptability.

<p align="center">
    <img src="img/model.png" width="80%"> <br>
</p>

Config files are in `configs/`.
```bash
NPROC_PER_NODE=${GPU_NUM} xtuner train \
 <your config file path>  \
  --deepspeed <deepspeed config file path> \
  --work-dir <workdir path>

# stage1 example
NPROC_PER_NODE=${GPU_NUM} xtuner train \
 configs/slidechat/stage_1.py \
  --deepspeed configs/deepspeed/deepspeed_zero2.json \
  --work-dir work_dirs/stage1

# stage2 example
NPROC_PER_NODE=${GPU_NUM} xtuner train \
 configs/slidechat/stage_2.py \
  --deepspeed configs/deepspeed/deepspeed_zero2.json \
  --work-dir work_dirs/stage2
```
Where ${GPU_NUM} is the number of GPUs

For a detailed explanation of the configuration file, please refer [**here**](https://xtuner.readthedocs.io/zh-cn/latest/training/modify_settings.html).
- `llm_name_or_path`: The parameter `llm_name_or_path` corresponds to the Hugging Face LLM path, such as `internlm/internlm2-chat-7b` or `Qwen/Qwen2.5-7B-Instruct` and so on.
- `data_path`: Training data (.json) path.
- `evaluation_images`: Evaluation data path.

LLAVAModel Hyperparameters:
- `freeze_llm`: Freeze the parameters of the LLM.
- `pretrained_pth`: If it is the stage 2 training , it refers to the checkpoint file from stage 1 training; otherwise, it is set to `None`.
- `train_stage`: `train_stage` indicates the training phase, either Stage `'1'` or Stage `'2'`.
  

## Inference

```bash
xtuner test <your config file path> \
--checkpoint <your checkpoint path> \
--test_slide_csv  <your test file> \
--test_output_csv <result file> \
--local_rank 0

# example
xtuner test configs/slidechat/stage_2.py \
--checkpoint stage2_pth \
--test_slide_csv  SlideBench-VQA(TCGA).csv \
--test_output_csv output_my_test.csv \
--local_rank 0
```

## Computational Resources

### Training
We trained SlideChat using **8 x NVIDIA A100 (80GB)** GPUs.

| Parameter | Stage-1 | Stage-2 |
| :--- | :--- | :--- |
| **Training GPUs** | 8 x A100 (80 GB) | 8 x A100 (80 GB) |
| **Total Training Time** | ~3 hours | ~24 hours |
| **Batch Size** | 1 | 1 |
| **Epochs** | 3 | 1 |

### Inference
SlideChat is deployment-friendly. NVIDIA A100 (80GB) is recommended for processing large slides, while a single NVIDIA RTX 4090 (24GB) is sufficient for WSIs with < 20,480 patches.

# Contact
- Ying Chen: yc4890@columbia.edu or cying2023@stu.xmu.edu.cn
- Yuanfeng Ji: yfj@stanford.edu
- Junjun He: hejunjun@sjtu.edu.cn

# Citation

**BibTeX:**

```bibtex
@inproceedings{chen2025slidechat,
  title={Slidechat: A large vision-language assistant for whole-slide pathology image understanding},
  author={Chen, Ying and Wang, Guoan and Ji, Yuanfeng and Li, Yanjun and Ye, Jin and Li, Tianbin and Hu, Ming and Yu, Rongshan and Qiao, Yu and He, Junjun},
  booktitle={2025 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  pages={5134--5143},
  year={2025},
  organization={IEEE}
}
```
