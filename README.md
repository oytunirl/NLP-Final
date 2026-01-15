# IMDb Sentiment Analysis & Scraper

This project is an end-to-end machine learning pipeline designed to analyze sentiment in movie reviews. It includes a custom web scraper built with **Playwright** to harvest data from IMDb and a **Scikit-Learn** model to classify reviews as either "Positive" or "Negative."

## 🚀 Features

- **Automated Scraping:** Uses `Playwright` to navigate IMDb, handle "Load More" buttons, and extract review titles, body text, and star ratings.
- **Data Preprocessing:** Cleans raw text by removing punctuation, lowercasing, and filtering out English stopwords using `NLTK`.
- **TF-IDF Vectorization:** Converts text data into numerical vectors to represent word importance.
- **Sentiment Classification:** Trains a Logistic Regression model to predict sentiment with high accuracy.
- **Instant Inference:** Includes a script to test the model on custom, user-written review strings.

## 🛠️ Tech Stack

- **Python** 3.x
- **Playwright** (Web Scraping)
- **Scikit-Learn** (Machine Learning & Vectorization)
- **NLTK** (Natural Language Processing)

## 📂 Project Structure

```text
├── scrape.py           # Script to scrape IMDb reviews (Positive & Negative)
├── main.py             # Main script for preprocessing, training, and evaluation
├── utils/
│   └── helper.py       # Helper functions for data loading and text preprocessing
├── playwright_data/    # (Generated) Browser session data
├── positive_reviews.json # (Generated) Scraped positive data
└── negative_reviews.json # (Generated) Scraped negative data
```

> **Note:** Ensure `helper.py` is placed inside a `utils` folder, or adjust the import in `main.py` to match your file structure.

## ⚙️ Installation

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/yourusername/your-repo-name.git](https://github.com/yourusername/your-repo-name.git)
    cd your-repo-name
    ```

2.  **Install the required Python packages:**

    ```bash
    pip install playwright scikit-learn nltk
    ```

3.  **Install Playwright browsers:**

    ```bash
    playwright install
    ```

4.  **Download NLTK stopwords:**
    Open a Python shell and run:
    ```python
    import nltk
    nltk.download('stopwords')
    ```

## 🏃 Usage

### 1. Data Collection

Run the scraper to generate the dataset. This will open a browser instance, navigate to specific IMDb pages (e.g., _Avengers_, _Joker_, _Parasite_), and save reviews to JSON files.

```bash
python scrape.py
```

_The scraper is currently configured to look for reviews with specific star ratings (9-10 for positive, 1-2 for negative) to ensure distinct labels._

### 2. Training & Prediction

Run the main script to load the JSON data, train the model, and see the accuracy metrics.

```bash
python main.py
```

## 📊 Model Performance

The script outputs the **Accuracy Score** and a full **Classification Report** (Precision, Recall, F1-Score). It also runs a series of test phrases to demonstrate the model's capabilities:

```text
Example prediction:
[1] Expected: Positive ("This movie was great! Loved it!")
[0] Expected: Negative ("Movie was stupid, boring...")
```

## 📝 License

[MIT](https://choosealicense.com/licenses/mit/)
