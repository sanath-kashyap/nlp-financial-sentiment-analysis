# NLP-Based Financial Sentiment Analysis: Lexicon Benchmarking

## Project Objective
Natural language processing (NLP) models designed for general text frequently misclassify corporate financial disclosures because common regulatory words carry vastly different connotations in a market context. For example, standard dictionaries tag words like "liability," "risk," or "share" as heavily negative or penalizing, whereas they are often standard compliance metrics. 

This project constructs a text-analytics pipeline in Python to analyze the tone of Apple’s earnings call transcript, explicitly benchmarking the domain-specific Loughran-McDonald (LM) financial lexicon against VADER (a popular generic sentiment tool) to quantify this misclassification error.

## Methodology & Text Pipeline
The processing architecture ingests raw text and applies the following natural language engineering steps:
1. **Text Preprocessing:** Regular expressions (`re`) are used to extract specific structural patterns, followed by tokenization, stop-word removal, and lemmatization using the Natural Language Toolkit (`nltk`).
2. **Generic Sentiment Evaluation:** Implementing VADER to generate baseline positive, negative, and compound polarity scores.
3. **Domain-Specific Dictionary Mapping:** Indexing the text against the Loughran-McDonald financial word list to isolate localized risk, litigious, positive, and negative sentiment densities.

## Key Quantitative Interpretations
* **The VADER Bias:** In my analysis, VADER generated a near-perfect compound score of **+1.000**. While it successfully captured the overwhelmingly upbeat tone of Tim Cook's strategic remarks, it completely ignored standard corporate caveats and legally required negative phrases, resulting in an overly optimistic sentiment distortion.
* **The Loughran-McDonald Contrast:** The LM dictionary correctly treated standard corporate risk language more cautiously. It recognized that phrases like *"forward-looking statements involve risks and uncertainties that may cause results to differ"* represent compliance text rather than fundamental business distress, verifying that general-purpose word lists fundamentally misclassify financial text.
* **Institutional Value:** By resolving these semantic errors, this pipeline provides a framework for generating cleaner textual alpha signals that can be fed directly into quantitative trading models or risk management systems.

## Tech Stack
* **Language:** Python
* **Natural Language Processing:** `nltk`, Regular Expressions (`re`), Loughran-McDonald Financial Lexicon, VADER
* **Data Processing:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
