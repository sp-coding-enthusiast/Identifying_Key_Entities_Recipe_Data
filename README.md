# Identifying Key Entities in Recipe Data

This repository contains a Jupyter notebook and supporting code for training a Named Entity Recognition (NER) model to extract key entities (quantities, units and ingredients) from recipe ingredient lines. The project uses a Conditional Random Fields (CRF) model (via sklearn-crfsuite) and demonstrates data preparation, feature engineering, training, and evaluation.

Main notebook

- files/Identifying_Key_Entities_Recipe_Data.ipynb

Quick summary

- Goal: Train a CRF-based NER model to label tokens in recipe ingredient strings as quantity, unit, ingredient, etc.
- Data: A JSON file (ingredient_and_quantity.json) that contains two fields for each record: `input` (raw ingredient line) and `pos` (token-level labels). The notebook tokenizes these fields into `input_tokens` and `pos_tokens` and prepares them for CRF training.
- Model: Uses sklearn-crfsuite to train a sequence-labeling model. The notebook contains feature extraction, model training, evaluation (classification reports, confusion matrix), and saving/loading the trained model.

How to run

Option A — Run in Google Colab (recommended for reproducibility)
1. Open the notebook `files/Identifying_Key_Entities_Recipe_Data.ipynb` in Colab.
2. Make sure your dataset (`ingredient_and_quantity.json`) is available in your Google Drive (the notebook uses `/content/drive/MyDrive/ingredient_and_quantity.json` by default). Change the path in the notebook if you store the dataset elsewhere.
3. Run the cells in order. The notebook installs `sklearn-crfsuite` and mounts Google Drive when needed.

Option B — Run locally
1. Create a Python environment and install dependencies (example):
   pip install pandas scikit-learn sklearn-crfsuite spacy joblib matplotlib seaborn
2. Place `ingredient_and_quantity.json` in the working directory or update the file path in the notebook.
3. Launch Jupyter and open `files/Identifying_Key_Entities_Recipe_Data.ipynb`.

Dependencies

- Python 3.8+
- pandas
- scikit-learn
- sklearn-crfsuite
- spaCy (optional for additional NLP utilities)
- joblib
- matplotlib, seaborn

Notebook structure (high level)

1. Imports and environment setup
2. Data ingestion and basic exploration
3. Tokenization of `input` and `pos` into `input_tokens` and `pos_tokens`
4. Feature extraction for sequence labeling
5. Train/test split and CRF training
6. Evaluation and analysis
7. Save/load trained model

Notes and tips

- The notebook currently expects the dataset to be read from Google Drive. If you prefer to store the dataset inside the repository, move `ingredient_and_quantity.json` into the repo (for example `data/ingredient_and_quantity.json`) and update the path used when loading the JSON.
- The CRF model and the feature definitions in the notebook are flexible; you may experiment with additional token-level features (e.g., orthographic, lexical, word-shape, embedding lookups) to improve performance.

License

This repository is provided under the MIT License — feel free to reuse and adapt the code.

Contact

If you have suggestions or improvements, open an issue or contact `sp-coding-enthusiast` on GitHub.
