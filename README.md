# LLM Lab 10: Alignment Experiment (DPO)

University of Gwadar | Department of Computer Science | Large Language Models
BS IT 8th Semester | Instructor: Engr. Bakhteyar Ghafoor

This project investigates how preference alignment changes the behaviour of a base language model.
Qwen2.5-0.5B is aligned with Direct Preference Optimization (DPO), and the base and aligned models
are compared on the same prompts.

## Links

| What | Link |
|---|---|
| Aligned model, beta = 0.1 | https://huggingface.co/TaniraAbbas/qwen2.5-0.5b-dpo-beta01 |
| Aligned model, beta = 0.5 | https://huggingface.co/TaniraAbbas/qwen2.5-0.5b-dpo-beta05 |
| Interface (Vercel) | ADD YOUR VERCEL LINK HERE |
| Live app | Runs from the Colab notebook (public Gradio link, temporary) |

## Repository files

| File | Content |
|---|---|
| `alignment_lab10.ipynb` | Full experiment notebook (Google Colab, T4 GPU) |
| `index.html` | Interface page that embeds the live app |
| `requirements.txt` | Python libraries used |
| `README.md` | This file |

## Setup

- Base model: `Qwen/Qwen2.5-0.5B`
- Preference dataset: `trl-lib/ultrafeedback_binarized` (2,000 training pairs, 100 evaluation pairs)
- Method: DPO with LoRA (r = 16, alpha = 32, dropout = 0.05, all linear layers)
- Training: learning rate 5e-5, batch size 2 with gradient accumulation 8, 1 epoch, max length 512, fp16
- Runs: beta = 0.1 (baseline) and beta = 0.5 (additional beta)
- Generation for evaluation: greedy decoding, `repetition_penalty = 1.1`, up to 200 new tokens, same settings for all three models

## Test prompts

1. What is PPO (Proximal Policy Optimization) in reinforcement learning? Explain simply.
2. What is the difference between PPO and DPO?
3. I have a job interview in 2 days and I feel stressed. What should I do?
4. Write a short, polite message to my class teacher asking for an extension on my assignment deadline.
5. If a car travels 5 km in 2.5 hours, what is its speed? Show steps.
6. Why did the Khan of Kalat give Gwadar to Oman in 1783?

Task types: explanation (1, 2), advice (3), professional writing (4), reasoning (5), question answering (6).

## Evaluation method

Each response is scored manually from 1 to 5 on helpfulness, relevance, clarity and instruction following,
using the same rubric for the base model and both aligned models. The notebook saves the answers to
`evaluation.csv` and computes the average scores.

## Results

Fill these in after running the notebook.

| Model | Average score (1-5) |
|---|---|
| Base | |
| DPO, beta = 0.1 | |
| DPO, beta = 0.5 | |

Summary of findings:

- Overall effect of DPO:
- Prompt types that improved most:
- Prompts where the base model was better:
- Effect of changing beta:

## How to run

1. Open `alignment_lab10.ipynb` in Google Colab and choose Runtime, then Change runtime type, then T4 GPU.
2. Run the cells from top to bottom. The first cell asks you to approve a Hugging Face login with a link and a short code.
3. The last cell starts the Gradio app and prints a public link.
