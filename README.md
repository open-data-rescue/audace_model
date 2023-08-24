# AUDACE Project Report

**Author:** Oliver Wang

## Introduction

The AUDACE Project is an extensive research initiative aimed at analyzing social vulnerability in the face of disruptive weather events. This document offers an insight into the methodologies and tools used, particularly in modeling. The results can be viewed on [Google Colab](https://drive.google.com/drive/folders/1Cdi5GR_NjhLuq3w-_XCIHle4rkLO9slu?usp=drive_link).

## Methodologies

### Latent Dirichlet Allocation (LDA)

LDA is a probabilistic topic modeling technique. Within the AUDACE Project, the implementation involved:

- **Data Collection and Preprocessing:** Articles related to disruptive weather were sourced from platforms like ProQuest and Eureka. The preprocessing steps included:
  - Tokenization: Breaking down text into individual words or terms.
  - Stop-word removal: Excluding commonly used words that don't add significant meaning.
  - Lemmatization: Reducing words to their base or root form.

- **Topic Modeling:** The Gensim library was employed to train the LDA model. The best number of topics was ascertained using coherence scores.

- **Topic Interpretation:** Topics received labels based on dominant keywords.

- **Visualization:** The pyLDAvis tool provided an interactive visualization of the topics, shedding light on their interrelationships and distributions.

### BERT Model

BERT, a state-of-the-art transformer model, was employed for text classification. The steps included:

- **Fine-Tuning:** The model was adjusted using the Hugging Face Transformers library.
- **Model Evaluation:** Metrics such as accuracy, precision, recall, and F1-score assessed the model's performance.
- **Inference:** The trained model could categorize new documents and highlight attention on keywords linked to disruptive weather and vulnerability.

## Scripts Overview

The project comprises 8 main scripts:

1. **PROQUEST_CORPUS_DOCUMENTATION.IPYNB:** Handles the splitting and cleaning of English articles from the Canadian Newstream database on ProQuest. Outputs a list of dictionaries marking article elements.

2. **EUREKA_CORPUS_DOCUMENTATION.IPYNB:** Similar to the ProQuest script but focuses on modern French articles from Eureka.

3. **RANDOM_50.IPYNB:** Assigns transcription tasks to team members to verify the OCR error rate.

4. **ENGLISH_CLASSIFICATION_LDA.IPYNB:** Conducts unsupervised classification on the English modern corpus.

5. **CLASSIFICATION_LDA_INCLUDE_SUBJECT.IPYNB:** Similar to the English classification script but includes subject words from the database.

6. **FRENCH_CLASSIFICATION_LDA.IPYNB:** Undertakes unsupervised classification on the French modern corpus.

7. **CLASSIFICATIONI_NOMIC.IPYNB:** Imports data from the English modern corpus and visualizes clustering using the NOMIC API.

8. **CLASSIFICATION_BERT.IPYNB:** Executes supervised classification based on the LDA model's results. It has two main sections: Pytorch and Tensorflow.

## Directory Structure in the [Google drive](https://drive.google.com/drive/folders/1Cdi5GR_NjhLuq3w-_XCIHle4rkLO9slu?usp=drive_link)
### CORPUS

This directory has two main subdirectories:

1. **ENGLISH_MODERN:**
   - Contains a directory named `canadian_newstream`. The subdirectories within are named by the search term and house the txt files exported from ProQuest.

2. **FRENCH_MODERN:**
   - Houses all the txt files converted from the PDF files exported from Eureka.

### CLEANED_CORPUS

This directory also has two main subdirectories:

1. **ENGLISH_MODERN:**
   - Files produced by the `proquest_corpus_documentation.ipynb` script.

2. **FRENCH_MODERN:**
   - Files produced by the `eureka_corpus_documentation.ipynb` script.

### MODEL

This directory stores all the saved LDA and BERT models. It contains several subdirectories related to LDA models:

- `lda_backups`
- `lda_models`
- `dictionary`
- `french_corpus`
- `french_dictionary`
- `french_text`

All dictionaries, corpus, and texts are modern. The English corpus, being relatively smaller, does not have saved versions of `english_corpus` and `english_text`. The `dictionary` is essentially the `english_dictionary`. These are crucial when loading the pre-trained LDA models and evaluating the coherence score. Instructions on how to load pre-trained LDA models are provided in the English and French LDA model scripts.

### CLASSIFIED_TEXT

This directory houses the classification results of the LDA models (currently for modern English). The BERT model was intended to be trained on this unsupervised classification result. Hence, the accuracy of this result is vital for the BERT model's performance.

- An assessment of the unsupervised classification's error rate is essential to determine the BERT model's true accuracy.

## Improvements and Recommendations

Several areas of improvement have been identified:

- Enhancing the "remove_duplicates" function for efficiency.
- Re-searching articles due to changes in the modern period.
- Enhancing data cleaning, especially for the French corpus.
- Examining the accuracy of unsupervised classification labels.
- Tuning the Pytorch and Tensorflow models for better accuracy.

For a detailed breakdown of each script and the associated improvements, please refer to the [report](https://drive.google.com/file/d/1r_XFnLCgoyTmUKYVa1nqD-KwYw-xmgt3/view?usp=drive_link).


