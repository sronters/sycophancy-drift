# Sycophancy as a Pathogen: LLM Behavioral Drift and Delusion Reinforcement

**Author:** Baktiyar Ablaikhan  
**Contact:** neweraprojecta@gmail.com

## Abstract
This study investigates sycophantic behavioral drift in LLMs and its 
potential to reinforce delusional beliefs in psychologically vulnerable 
users. Three novel drift patterns are identified and a DPO fine-tuning 
intervention reduces within-model drift by 62%.

## Repository Structure

| File / Folder | Description |
|---|---|
| `generate_dataset_groq.py` | Synthetic dataset generator using Llama 3.3 70B via Groq API |
| `dpo_pipeline_final.py` | Complete DPO fine-tuning pipeline (Google Colab, T4 GPU) |
| `anti_sycophancy_dataset.jsonl` | 44-example preference dataset (chosen/rejected pairs) |
| `experiment4_summary.json` | Full numerical results for Experiment 4 |
| `figures/` | All paper figures in PNG format |
| `dataset/` | HuggingFace dataset format files |

## Key Results

| Model | Avg Drift Score |
|---|---|
| Claude Sonnet 4.6 | 0% |
| GPT-5.4 | 25% |
| Gemini 3 Pro | 71% |
| Qwen 0.5B baseline | 33.3% |
| **Qwen 0.5B after DPO** | **12.5% (↓62%)** |

## Three Drift Patterns Identified
- **Escalating Drift** — gradual capitulation under sustained pressure
- **Disclaimer-Wrapped Validation** — safety disclaimer + functional harm
- **Ideological Capture** — model adopts and defends user's false narrative

## Requirements
```bash
pip install groq datasets transformers trl peft accelerate bitsandbytes
```

## How to Reproduce

**Generate dataset:**
```bash
export GROQ_API_KEY="TOKEN"
python generate_dataset_groq.py
```

**Run DPO fine-tuning** (Google Colab T4 GPU):
```python
# Upload anti_sycophancy_hf/ folder to Colab, then run:
python dpo_pipeline_final.py
```
