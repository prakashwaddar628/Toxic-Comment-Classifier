##📝 Toxic Comment Classification

    This project aims to classify online comments as toxic, severe toxic, obscene, threat, insult, or identity hate using Machine Learning (Logistic Regression, LSTM, BERT).

#📌 Project Structure

    📂 Toxic-Comment-Classification  
    │── 📜 main.ipynb          # Jupyter Notebook with model training  
    │── 📜 requirements.txt     # List of dependencies  
    │── 📜 README.md            # Project documentation  
    │── 📜 train.csv            # Training dataset  
    │── 📜 test.csv             # Test dataset  
    │── 📜 submission.csv       # Final predictions file  
🚀 Installation Guide

#1️⃣ Install Dependencies
    To install all required libraries, run:

    pip install -r requirements.txt
    ✅ This will install pandas, numpy, scikit-learn, nltk, tensorflow, keras, transformers, and other dependencies.

#2️⃣ Download NLTK Resources
    Before running the notebook, execute:

    import nltk
    nltk.download('stopwords')
    nltk.download('punkt')
    nltk.download('wordnet')
📌 Dataset Overview

#1️⃣ train.csv
    Contains labeled comments with 6 target categories:

    toxic

    severe_toxic

    obscene

    threat

    insult

    identity_hate

#2️⃣ test.csv
    Unlabeled comments that need to be classified.

#3️⃣ submission.csv
    Final predictions for test data.

#📌 Model Implementation
    We implemented three models:

#1️⃣ Logistic Regression (Baseline Model)
    Used TF-IDF Vectorization to convert text into numerical features.

    Applied OneVsRestClassifier with Logistic Regression.

#2️⃣ LSTM (Deep Learning Model)
    Used word embeddings and converted text into sequences.

    Built an LSTM network with dropout layers.

#3️⃣ BERT (Transformer-Based Model - Best Performance)
    Used BERT Tokenizer for word embeddings.

    Trained a BERT-based classifier for multi-label classification.

#📌 Model Training & Prediction
    To train the model, run main.ipynb.

    Train Logistic Regression

    model = OneVsRestClassifier(LogisticRegression(max_iter=200))
    model.fit(X_train, y_train)
    Train LSTM

    model_lstm.fit(X_train_padded, y_train, epochs=3, batch_size=64, validation_split=0.1)
    Train BERT

    model_bert.fit(
        {"input_ids": X_train_bert["input_ids"], "attention_mask": X_train_bert["attention_mask"]},
        y_train, epochs=2, batch_size=16
    )
#📌 Predictions & Submission
    Once trained, generate predictions using:

    y_pred_test = model.predict(X_test)
    submission_df.to_csv("submission.csv", index=False)
    For LSTM & BERT, run:

    submission_lstm.to_csv("submission_lstm.csv", index=False)
    submission_bert.to_csv("submission_bert.csv", index=False)
#📌 Results & Accuracy
    Model	Accuracy	Best For
    Logistic Regression	Moderate	Quick baseline model
    LSTM	High	Context understanding
    BERT	Best	State-of-the-art NLP

#📌 Future Improvements
    ✅ Fine-tune BERT for better performance
    ✅ Use more labeled data for training
    ✅ Try other Transformer models (e.g., RoBERTa, GPT)

#📌 Contributors

    [Prakash L Waddar] (Machine Learning Developer)

    Open for Collaboration!

#📌 License
    This project is open-source under the MIT License.