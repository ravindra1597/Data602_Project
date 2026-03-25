# Predictive Discounting Engine: Optimizing E-Commerce Conversions

**Executive Summary:** Blanket discount strategies erode profit margins, while offering no discounts leads to cart abandonment. This project developed a behavioral tracking engine that dynamically predicts user purchase intent. By mathematically optimizing our intervention threshold, the final model successfully captures **90% of all true buyers** on the site.

---

## 1. The Business Challenge
Currently, we rely on rigid promotional strategies. The goal of this analysis was to move from guessing to predicting. By observing real-time customer behavior, we can identify which users will buy naturally and which users require a targeted financial nudge to cross the finish line. 

Because missing out on a $100 sale (False Negative) is vastly more expensive than offering a redundant 10% discount (False Positive), this engine was explicitly optimized to capture the maximum number of buyers without hemorrhaging promo codes.

---

## 2. Behavioral Insights (What the Data Showed)
An analysis of 10,000 recent customer sessions revealed distinct patterns between buyers and window-shoppers.

* **Noise vs. Signal:** Metrics like `day_of_week` and `days_since_last_visit` proved to be entirely random noise. However, **Engagement Intensity** (page views relative to session duration) emerged as the strongest indicator of purchase intent.
* **The Segment Gap:** We are currently treating all customers the same, but the data shows a massive divide. **VIP Customers** convert naturally at a rate of 62.7%, while our **At-Risk** segment lags severely at 42.0%. 


<img width="966" height="566" alt="CustomerSegment vs PurchaseRate" src="https://github.com/user-attachments/assets/cd850dcb-a41d-482b-9301-02a484f2b59b" />


<img width="665" height="365" alt="SessionDurationByMinutues" src="https://github.com/user-attachments/assets/c843aa3d-f5c1-42b2-ac06-0403d37891ab" />

---

## 3. The Predictive Engine
To act on these behavioral signals, we engineered a machine learning pipeline utilizing an **Ensemble Model** (combining Random Forest, Gradient Boosting, and Logistic Regression). 

To ensure the model aligned with our financial realities, we evaluated its performance strictly using the **F1-Score**. This metric heavily penalizes the system anytime it allows a true buyer to slip through the cracks, forcing it to balance aggressive marketing with precision.

---

## 4. The Breakthrough: Threshold Optimization
Out-of-the-box, predictive algorithms wait until they are 50% confident before flagging a user as a buyer. However, waiting for 50% certainty leaves money on the table.

We mathematically adjusted the system's internal trigger to match our risk profile. We lowered the required confidence threshold to **41%**. 

**The Result:**
* By telling the system to intervene the moment it is just 41% confident, our F1-Score jumped to a mathematical peak of **0.684**. 
* More importantly, this wider net successfully identifies and captures **90% of all true buyers** on the platform.

<img width="708" height="445" alt="Screenshot 2026-03-25 090754" src="https://github.com/user-attachments/assets/14ef9a8b-9bf1-4103-b5f1-2f6363a0a800" />


---

## 5. Strategic Recommendations
We can turn this predictive engine into immediate revenue through two steps:

1. **Deploy the 41% Net:** Integrate this model into our live session tracker. The second a user's behavior crosses the 41% probability threshold, automatically trigger a customized retention email or a targeted UI discount pop-up.
2. **Shift the Marketing Spend:** Stop deploying generic acquisition capital. Shift that budget toward targeted re-engagement campaigns explicitly designed for the "At-Risk" segment to bridge their 20% conversion gap.

---

## 6. Project Reflection
The most impactful technical takeaway from this project was discovering that default algorithmic thresholds (0.50) are rarely optimal for real-world business problems. Building a dynamic scanner to locate the 41% mark taught me how to perfectly align raw mathematical outputs with actual financial risk and reward.
