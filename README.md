# Pet Adoption Likelihood Predictor 🐾

![Model Performance](confusion_matrix.png)

## 📖 Project Overview
This project builds a machine learning model to predict whether a pet is likely to be adopted based on various physical characteristics and shelter information. By analyzing factors such as breed, age, size, and vaccination status, the model helps shelters understand adoption trends and optimize their strategies.

The project implements a full data science pipeline, from exploratory data analysis (EDA) to model tuning, achieving a final accuracy of **91%** using a Decision Tree Classifier.

## 📊 Dataset
The dataset (`pet_adoption_data.csv`) contains information on 2,007 pets with 13 distinct features.

* **Target Variable:** `adoption_likelihood` (0 = Unlikely, 1 = Likely)
* **Key Features:**
    * **Physical:** `pet_type`, `breed`, `color`, `size`, `weight_kg`
    * **Health:** `vaccinated`, `health_condition` (Healthy/Medical condition)
    * **Shelter info:** `timein_shelter_days`, `adoption_fee`
    * **History:** `previous_owner`

## 🛠️ Project Workflow

### 1. Data Exploration (EDA)
* Loaded and inspected the dataset structure.
* Visualized the target distribution (`adoption_likelihood`) to check for class balance.
* Analyzed numerical distributions for `age_months` and `adoption_fee`.

### 2. Data Preprocessing
* **Encoding:**
    * Mapped ordinal feature `size` to numerical values (Small=1, Medium=2, Large=3).
    * Applied One-Hot Encoding to categorical variables: `color`, `pet_type`, `breed`.
* **Scaling:**
    * Applied **MinMax Scaling** to `weight_kg`.
    * Applied **Standard Scaling** to `adoption_fee` to normalize costs.

### 3. Model Training & Evaluation
* **Baseline Model:** Trained a default `DecisionTreeClassifier` which achieved an accuracy of **86%**.
* **Hyperparameter Tuning:** Improved the model by experimenting with specific parameters:
    * `criterion='entropy'`
    * `max_depth=5`
    * `min_samples_split=10`
    * `min_samples_leaf=5`

## 📈 Results
The hyperparameter tuning significantly improved model performance.

| Metric | Default Model | Tuned Model |
| :--- | :--- | :--- |
| **Accuracy** | 86% | **91%** |
| **Precision (Likely)** | 75% | **90%** |
| **Recall (Likely)** | 88% | **81%** |

The confusion matrix (shown above) illustrates that the tuned model has a high true positive and true negative rate, making it a reliable tool for prediction.

## 💻 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/pet-adoption-prediction.git](https://github.com/yourusername/pet-adoption-prediction.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas matplotlib seaborn scikit-learn
    ```
3.  **Run the Notebook:**
    Open `Pet-Adoption-Likelihood-Predictor.ipynb` in Jupyter Notebook or Google Colab and execute the cells.

## 🤝 Credits
Dataset provided by [Rabie El Kharoua on Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-pet-adoption-status-dataset).
