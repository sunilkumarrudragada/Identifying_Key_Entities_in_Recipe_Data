
# 🧠 Identifying Key Entities in Recipe Data

This project applies a Conditional Random Field (CRF) model to identify key entities — `quantity`, `unit`, and `ingredient` — in recipe text instructions using Named Entity Recognition (NER).

---

## 📌 Objective

To build a sequence labeling model that can automatically extract structured entities from unstructured ingredient instructions (e.g., "1/2 cup chopped onions").

---

## 📂 Dataset Overview

- Format: JSON with two columns — `input` and `pos`
- Total rows: 285
- Each row contains a sentence and its space-separated POS tag sequence.
- Example:  
  ```
  Input: "1/2 cup chopped onions"  
  POS:   "quantity unit ingredient ingredient"
  ```

---

## 🧪 EDA Highlights

- **Most common ingredients:** powder, salt, seeds, oil
- **Most common units:** teaspoon, cup, tablespoon
- Frequency plots were used to visualize top entities

---

## ⚙️ Feature Engineering

Extracted token-level and contextual features including:
- Token, lemma, POS tag, shape, digit/alpha flags
- Custom flags: `is_quantity`, `is_unit` using regex + keyword sets
- Context: previous and next tokens
- Class weights applied to handle imbalance

---

## 🤖 Model

- Algorithm: **Conditional Random Field (CRF)**
- Library: `sklearn-crfsuite`
- Hyperparameters: `algorithm='lbfgs', c1=0.5, c2=1.0`
- Training used class-weighted features

---

## 📈 Evaluation

- **Validation Accuracy:** 96.49%
- **Label-wise Accuracy:**
  - Ingredient: 98.62%
  - Quantity: 88.08%
  - Unit: 93.58%

---

## 🚨 Error Analysis

- 101 misclassified tokens in validation set
- Most confusion occurred between `quantity` and `ingredient`
- Misclassified examples analyzed with surrounding context

---

## 📌 Tools Used

- Python, Pandas, Matplotlib
- spaCy (tokenization & linguistic features)
- sklearn-crfsuite
- seaborn (EDA visuals)

---

## ✅ Outcome

- Successfully extracted structured recipe entities using CRF
- Robust generalization with minimal misclassification
- Model ready for extension with domain-specific features or transformer models

---

## 📄 Report

A complete report (PDF) with EDA visuals, model performance, and insights is included in the repository.
