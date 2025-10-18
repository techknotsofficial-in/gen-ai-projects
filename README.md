# Ultra-Fast Text-to-Image Generator - README

## 🚀 Overview

This guide will help you set up and run the **Ultra-Fast Stable Diffusion Text-to-Image Generator** in **Google Colab** using **T4 GPU** for optimal performance.

You will learn:

* How to copy and run the notebook in Google Colab
* How to enable GPU (T4) runtime
* How to get your Hugging Face Token
* Sample UI screenshots and generated images (to be added by you)

---

## 📋 1. How to Use This in Google Colab

### ✅ Step 1: Open a New Notebook

1. Go to [https://colab.research.google.com](https://colab.research.google.com)
2. Click on **File > New Notebook**

### ✅ Step 2: Change Runtime to T4 GPU

1. Click **Runtime > Change runtime type**
2. Under **Hardware accelerator**, select **GPU**
3. Under **GPU type**, choose **T4**
4. Click **Save**

> ⚠️ Important: Using T4 GPU provides up to 10x speed improvement over CPU.

---

## 🔑 2. How to Get Your Hugging Face Token

1. Visit: [https://huggingface.co](https://huggingface.co)
2. Create an account or log in
3. Go to **Settings > Access Tokens**
4. Click **New Token** and select **Read** permissions
5. Copy the token

### 🔐 Add Token in Colab

In your Colab notebook,
HF_TOKEN = "replace your hugging face token"

Paste your token when prompted.

---

## ▶️ 3. How to Run the Stable Diffusion Generator

### 📦 Install Dependencies

```python
!pip install diffusers accelerate transformers torch torchvision
```

### 🧠 Load the Model

```python
from diffusers import AutoPipelineForText2Image
import torch
pipeline = AutoPipelineForText2Image.from_pretrained(
    "stabilityai/sdxl-turbo",
    torch_dtype=torch.float16,
    variant="fp16",
    use_safetensors=True
)
pipeline = pipeline.to("cuda")
```

### 🖼 Generate an Image

```python
prompt = "a elden ring game landscape with a knight"
image = pipeline(prompt, num_inference_steps=2, guidance_scale=0.0).images[0]
image
```

---





## 🎯 Conclusion

You're now ready to run **ultra-fast image generation** using Stable Diffusion Turbo on Google Colab with GPU acceleration! Feel free to customize prompts and explore your creativity.

---

## 📞 Support

For any issues, reach out on Hugging Face forums or GitHub Discussions.
