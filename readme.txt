# 🏦 Credit Risk Scoring Project

## 🎯 Objective
This project aims to build a machine learning model to predict the probability of default for loan applicants, simulating a real-world banking decision process.

The goal is not only to train a model, but to:
- avoid data leakage
- ensure interpretability
- simulate realistic credit approval decisions

---

## 🧠 Key Concept: Data Leakage

**Data leakage occurs when the model uses information that would not be available at the time of decision.**

In a real banking scenario, the model must rely only on:
- customer information
- historical credit data
- loan characteristics

❌ It must NOT use:
- future payments
- repayment outcomes
- post-loan events

---

## 🟢 Selected Features (Used in Model)

### 💰 Loan Information
- `loan_amnt` – Loan amount  
- `term` – Loan duration  
- `int_rate` – Interest rate  
- `installment` – Monthly payment  
- `purpose` – Loan purpose  

👉 These describe the structure and risk of the loan.

---

### 👤 Customer Information
- `annual_inc` – Annual income  
- `emp_length` – Employment length  
- `home_ownership` – Housing status  
- `verification_status` – Income verification  

👉 These represent financial stability.

---

### 💳 Credit History
- `dti` – Debt-to-income ratio  
- `delinq_2yrs` – Delinquencies in last 2 years  
- `inq_last_6mths` – Credit inquiries  
- `open_acc` – Open credit lines  
- `pub_rec` – Public records  
- `revol_util` – Credit utilization  
- `total_acc` – Total accounts  

👉 These are key indicators of creditworthiness.

---

### 🧠 Risk Rating (Advanced Features)
- `grade`  
- `sub_grade`  

⚠️ Note:  
These are internal risk scores provided by the platform.  
They may introduce bias, so models will be tested:
- with these features  
- without these features  

---

### 🎯 Target Variable
- `loan_status` → converted into:
  - `1 = Default`
  - `0 = Non-default`

---

## 🔴 Removed Features (Data Leakage)

### 💸 Payment-related (post-loan)
- `out_prncp`
- `out_prncp_inv`
- `total_pymnt`
- `total_pymnt_inv`
- `total_rec_prncp`
- `total_rec_int`
- `total_rec_late_fee`
- `recoveries`
- `collection_recovery_fee`

👉 These contain repayment information.

---

### 📅 Post-loan timestamps
- `last_pymnt_d`
- `last_pymnt_amnt`
- `next_pymnt_d`
- `last_credit_pull_d`

👉 Available only after loan issuance.

---

### ⚠️ Hardship indicators
- `hardship_*`

👉 Indicate financial distress after the loan.

---

### 💥 Debt settlement
- `debt_settlement_flag`
- `debt_settlement_flag_date`
- `settlement_status`
- `settlement_date`
- `settlement_amount`
- `settlement_percentage`
- `settlement_term`

👉 Represent default-related outcomes.

---

## 🟡 Removed Features (Simplification / Scope Reduction)

### 🆔 Identifiers
- `id`
- `member_id`
- `url`

👉 No predictive value.

---

### 📝 Text fields
- `emp_title`
- `desc`
- `title`

👉 Require NLP (out of scope).

---

### 🌍 Geographic
- `zip_code`
- `addr_state`

👉 Potentially useful but excluded for simplicity.

---

### 🧾 Highly technical features
- `num_*`
- `mo_sin_*`
- `mths_since_*`
- `acc_*`
- `tot_*`

👉 Will be considered in future iterations.

---

### 👥 Joint applications
- `annual_inc_joint`
- `dti_joint`
- `verification_status_joint`
- `sec_app_*`

👉 Increase complexity without immediate benefit.

---

## 🧠 Methodology

Feature selection is based on:
- temporal availability (pre-loan only)
- interpretability
- business relevance

Original dataset:
- ~145 features

Final dataset:
- ~15 features

👉 This improves:
- model robustness
- interpretability
- realism

---

## 🚀 Future Improvements

- Feature engineering
- Model comparison (with vs without `grade`)
- Handling class imbalance
- Decision threshold optimization
- Business simulation (profit/loss)
- Model monitoring (data drift)

---

## 💡 Key Insight

> A good model is not the most complex one,  
> but the one that reflects real-world decision constraints.

---

## 📌 Author's Note

This project focuses on **thinking like a bank**, not just building a model.
