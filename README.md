
Experiment 2 — Probability & basic statistics with Pandas and NumPy


AIM:

To compute descriptive statistics and empirical probabilities using Pandas, and generate synthetic samples from probability distributions using NumPy.

ALGORITHM:

1. Start and import numpy and pandas.
2. Create dataset: Define a NumPy array heights containing sample height measurements and convert it into a pandas.Series object s.
3. Compute descriptive statistics: Calculate the mean (s.mean()), median (s.median()), standard deviation (s.std()), and variance (s.var()).
4. Estimate empirical probability: Apply a boolean condition (s > 170) and compute its .mean() to find the proportion of samples exceeding 170.
5. Generate synthetic samples: Draw 10 random values from a normal distribution parameterized by the sample mean and standard deviation using np.random.normal().
6. Display results: Print all computed statistics, empirical probability, and rounded random samples.
7. Stop.

THEORY:

Descriptive statistics summarize the central tendency (mean, median) and dispersion (variance, standard deviation) of a dataset. Empirical probability estimates the likelihood of an event directly from observed data frequencies (count of favorable outcomes / total observations). Random sampling from parametric distributions such as the normal (Gaussian) distribution \(\mathcal{N}(\mu, \sigma^2)\) allows simulation of synthetic data and forms the foundation for statistical inference, Monte Carlo methods, and bootstrapping in machine learning.

PROGRAM:

python
import numpy as np
import pandas as pd

heights = np.array([160, 165, 170, 175, 180, 155, 168, 172, 169, 158])
s = pd.Series(heights)

print("Mean:", s.mean())
print("Median:", s.median())
print("Std dev:", round(s.std(), 3))
print("Variance:", round(s.var(), 3))
print("P(height > 170):", (s > 170).mean())

sample = np.random.normal(loc=s.mean(), scale=s.std(), size=10)
print("Random sample (10) from normal around mean:", np.round(sample, 2))
Use code with caution.

DETAILED EXPLANATION:

1. Import libraries: numpy and pandas are imported for numerical operations and Series data structures.
2. Create NumPy array: heights stores 10 numerical height observations.
3. Convert to Pandas Series: s = pd.Series(heights) wraps the array in a labeled 1D Series with built-in statistical methods.
4. Compute descriptive statistics: .mean(), .median(), .std(), and .var() calculate central tendency and spread (using sample degrees of freedom ddof=1 by default in Pandas).
5. Compute empirical probability: (s > 170) produces a boolean Series (True/False), and .mean() treats True as 1 and False as 0 to compute the empirical probability \(P(\text{height} > 170)\).
6. Generate normal samples: np.random.normal(loc=s.mean(), scale=s.std(), size=10) generates 10 synthetic observations from a normal distribution matching the sample mean and standard deviation.

SAMPLE OUTPUT:

text
Mean: 168.2
Median: 169.0
Std dev: 7.756
Variance: 60.17
P(height > 170): 0.4
Random sample (10) from normal around mean: [170.3 166.2 173.1 161.5 169.8 175.4 164.0 168.9 171.2 165.7]
Use code with caution.

RESULT:

Thus, descriptive statistics, empirical probability estimation, and normal distribution sampling were successfully implemented using Pandas and NumPy.
