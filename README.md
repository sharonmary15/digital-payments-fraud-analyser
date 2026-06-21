# Digital Payments Fraud Pattern Analyser
Detecting fraud in 6.3 million mobile-money transactions using anomaly detection, 
supervised machine learning, and network graph analysis.


**Headline results:** 99.6% fraud recall with 100% precision, and 44 hidden 
collection-point accounts uncovered through network analysis.


## The Problem
Digital payment platforms process millions of transactions a day, and a tiny 
fraction are fraud. Fraud teams can't review them by hand, so they need a system 
that flags suspicious activity and shows how fraudulent accounts are connected. 
This project builds that system on the PaySim dataset and compares three detection 
approaches.


## Approach
I tested three methods, each with a different strength:

| Method | Recall | Precision | Verdict |
|--------|--------|-----------|---------|
| Rule-based detector | 41% | 1.5% | Transparent but blunt: 227,000 false positives |
| Unsupervised (Isolation Forest) | 2% | 2% | Fails: fraud here isn't statistical outliers |
| Supervised (Random Forest) | 99.6% | 100% | Accurate and precise: the clear winner |


## Key Findings

**Fraud lives in only two transaction types.** Every fraud in the data is a 
TRANSFER or CASH_OUT, never a payment or deposit. Filtering to these cut the data 
56% without losing a single fraud case.

**Feature engineering mattered more than the algorithm.** A balance-consistency 
feature I engineered drove 45% of the model's decisions on its own. The three 
features I designed together accounted for around 60% of predictive power, more 
than all the original dataset columns combined.

**Network analysis revealed 44 collection points.** Most fraud is one victim 
sending to one destination, so a random view shows no structure. But filtering to 
accounts that received from multiple victims exposed 44 collection-point accounts 
where stolen funds converged, the money-laundering layer that transaction-level 
detection alone misses.


## Tools
Python, pandas, scikit-learn (Random Forest, Isolation Forest), NetworkX and Pyvis 
(network graphs), built in Google Colab.


## Files
- `Digital_payment_fraud_pattern_analyser.ipynb` — the full analysis, start to finish
- `fraud_network_final.html` — the interactive collection-point network graph
- `results_summary_fin.txt` — a short results summary
  

## A Note on the Data
PaySim is a synthetic dataset, so the patterns are cleaner than real-world fraud. 
The methods and reasoning are what transfer; the exact accuracy numbers would be 
lower on messier real data.


**About me:** I'm Sharonmary Lazer Baptist Anthony, building a data analytics 
portfolio focused on financial crime, fraud, and risk. I'm targeting data analyst 
roles where this kind of work matters. 

Connect with me on [LinkedIn](https://www.linkedin.com/in/sharonmary-anthony-516078361).
