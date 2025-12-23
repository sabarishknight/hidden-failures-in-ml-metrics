# Accuracy Hides Failure

## Overview

Machine learning models are often evaluated using aggregate metrics such as overall accuracy or AUC. While these metrics provide a convenient summary, they can be misleading in real-world systems where performance may vary significantly across different subpopulations.

This project demonstrates how a model with strong overall accuracy can still perform poorly for critical subgroups, leading to hidden risks in deployment. Using a real-world credit risk dataset, we show why slice-based evaluation is essential for trustworthy and responsible machine learning.

---

## Motivation

In many production systems, decisions made by machine learning models affect diverse groups of users. Relying solely on overall performance metrics can conceal systematic failures that disproportionately impact specific segments, such as high-risk or underserved populations.

The goal of this project is to highlight a simple but often overlooked idea:

> **Good overall accuracy does not guarantee reliable performance for everyone.**

---

## Dataset

- **Dataset:** UCI Credit Card Default Dataset  
- **Task:** Binary classification (default vs non-default)
- **Type:** Tabular, real-world financial data
- **Size:** ~30,000 records

This dataset is widely used in industry and academic settings, making it a practical choice for illustrating real deployment concerns.

---

## Methodology

1. Train a simple and interpretable machine learning model (Logistic Regression).
2. Evaluate standard overall accuracy on a held-out test set.
3. Perform **slice-based evaluation** by dividing the data into meaningful subgroups:
   - Credit limit segments (low to high)
   - (Optional) Age groups or risk-related features
4. Compare subgroup-level performance against the aggregate metric.

No complex architectures or heavy computation are used. The focus is on **evaluation quality**, not model complexity.

---

## Key Results

- **Overall test accuracy:** ~81%
- **Subgroup performance varied significantly:**
  - Low credit limit customers: ~74% accuracy
  - High credit limit customers: ~87% accuracy
- A gap of more than **13 percentage points** exists between subgroups.

Despite strong aggregate performance, the model systematically underperforms for the group most likely to default.

---

## Why This Matters

In real-world decision systems:
- Low-performing subgroups often correspond to higher risk or higher impact users.
- Aggregate metrics can create a false sense of reliability.
- Silent failures may go unnoticed until they cause financial, ethical, or operational harm.

This project highlights the importance of:
- Slice-based evaluation
- Segment-level monitoring
- Responsible metric selection in production ML systems

---

## Takeaway

> **Overall accuracy is necessary, but not sufficient.**  
> Understanding *who* a model fails for is just as important as how often it succeeds.

This insight is critical for building reliable, fair, and trustworthy machine learning systems.

---
