# Enhancing Football Detection with Temporal Fusion: A Multi-Frame FootAndBall Approach

Year 3 Semester 3 Project

## Description
Multi-frame football detection system built by extending the FootAndBall architecture (https://github.com/jac99/FootAndBall) with temporal fusion (difference, variance, attention, weighted average) to improve ball and player detection on the ISSIA-CNR Soccer dataset.


## Results

Evaluated on the ISSIA-CNR Soccer dataset (video sequences 1–4 for training, sequence 5 for validation, sequence 6 as the held-out test set).

| Fusion Type      | Ball AP    | Player AP  | mAP        |
|-------------------|-----------:|-----------:|-----------:|
| Baseline (no fusion) | 0.5080  | 0.4650     | 0.4865     |
| Difference         | 0.5453   | 0.4814     | 0.5133     |
| Weighted Average   | 0.8083   | 0.5285     | 0.6684     |
| Attention          | 0.8161   | 0.4635     | 0.6398     |
| **Variance**       | 0.6606   | **0.8631** | **0.7618** |

**Key findings:**
- Every temporal fusion variant outperforms the single-frame baseline.
- **Variance fusion** achieves the best overall performance (mAP 0.7618), driven by a strong Player AP (0.8631) — players are large, spatially stable targets, so a simple per-pixel variance across frames reliably captures where movement is happening without needing to learn anything.
- **Attention fusion** is strongest specifically for **Ball AP** (0.8161) — the ball is small and frequently occluded or blurred across frames, so an adaptive, learned weighting of "which frame to trust" outperforms treating all frames equally.
