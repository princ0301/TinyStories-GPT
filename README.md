# TinyStories-GPT: Training a Small Language Model from Scratch

This project implements a small, character-level GPT (Generative Pretrained Transformer) trained on the [TinyStories dataset](https://huggingface.co/datasets/roneneldan/TinyStories). It showcases how to build a transformer-based language model using only PyTorch — from tokenization to training and generation.

---

## 📚 Dataset

We use the [TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories) dataset, a collection of short stories designed to be syntactically simple and ideal for small models.

---

## ⚙️ Model Configuration

| Parameter             | Value      |
|-----------------------|------------|
| `vocab_size`          | 50257      |
| `block_size`          | 128        |
| `n_layer`             | 6          |
| `n_head`              | 6          |
| `n_embd`              | 384        |
| `dropout`             | 0.1        |
| `bias`                | True       |
| `batch_size`          | 32         |
| `max_iters`           | 25000      |
| `eval_iters`          | 500        |
| `learning_rate`       | 1e-4       |
| `min_lr`              | 5e-4       |
| `warmup_steps`        | 1000       |
| `gradient_accumulation`| 32        |
| `precision`           | float16 / bfloat16 (if supported) |

---

## 🏗️ Architecture Summary

- 🔹 Decoder-only transformer
- 🔹 Positional embeddings
- 🔹 Causal (masked) multi-head self-attention
- 🔹 MLP + GELU activations
- 🔹 Layer normalization and dropout
- 🔹 Weight tying (embedding ↔ output layer)

---

## 📈 Training vs Validation Loss

<p align="center">
  <img src="assets/loss_curve.png" alt="Loss Curve" width="500"/>
</p>

- ✅ The model was evaluated every 500 steps.
- ✅ Checkpointing occurred on best validation loss.

---

## 🖼️ Sample Output

> **Prompt**: `"Once upon a time there was a pumpkin."`

<p align="center">
  <img src="assets/generated_story_output.png" alt="Generated Story Output" width="600"/>
</p>

📌 The model continues the story with coherent, simple language using only ~25M parameters.

---

## 🚀 How to Run

### Step 1: Clone and Install

```bash
git clone https://github.com/your-username/tinystories-gpt.git
cd tinystories-gpt
