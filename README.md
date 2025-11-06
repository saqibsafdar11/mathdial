# MathDial: Predicting Student Self-Correction in AI-Tutored Mathematics

A machine learning project that predicts student self-correction outcomes in AI-tutored mathematics dialogues by comparing Bayesian Networks and Logistic Regression approaches.

## 📊 Project Overview

This project develops and compares two fundamentally different machine learning approaches to predict whether students will successfully self-correct during mathematics tutoring sessions. Using the MathDial dataset, we analyze pedagogical features that drive learning success.

### Primary Aim

Develop and compare Bayesian Networks and Logistic Regression models to predict student self-correction outcomes in AI-tutored mathematics dialogues, while identifying key pedagogical features that drive success.

## 🎯 Key Objectives

1. **Model Development & Comparison**: Implement both a probabilistic graphical model (Bayesian Network) and a linear model (Logistic Regression), comparing their:
   - Predictive accuracy
   - Interpretability
   - Computational efficiency
   - Suitability for educational deployment

2. **Feature Analysis**: Identify which pedagogical characteristics drive learning outcomes:
   - Confusion levels
   - Engagement patterns
   - Teacher intervention strategies
   - Dialogue interaction patterns

3. **Class Imbalance Handling**: Address severe three-class imbalance (75.4% Success / 13.4% Hints / 11.2% Failed) using SMOTE (Synthetic Minority Over-sampling Technique)

## 📁 Dataset

The **MathDial dataset** (Macina et al., 2023) contains nearly 2,848 one-to-one tutoring conversations where expert human teachers guide a simulated "student" through grade-school mathematics word problems from the GSM8k benchmark. Key features:

- **Conversations**: Multi-turn dialogues with speaker labels and pedagogical action tags
- **Problems**: Original math word problems from GSM8k benchmark
- **Student Context**: Grade levels (3-6), learning characteristics, and simulated misconceptions
- **Outcomes**: Teacher-assessed self-correctness (Yes / Yes with hints / No)
- **Annotations**: Teaching strategies ("teacher moves") and learning outcomes

## 🔧 Feature Engineering

Engineered **12 numerical pedagogical features** from raw dialogue data:

### Question Complexity
- `estimated_difficulty`: Problem complexity proxy (question text length × 0.5)
- `careless_error_indicator`: Binary flag detecting trivial mistakes

### Student State
- `confusion_severity`: Teacher-assessed confusion level (1-5 scale)
- `student_engagement_score`: Participation intensity based on dialogue turns
- `student_struggle_ratio`: Confusion severity / engagement score

### Teacher Intervention
- `teacher_guidance_intensity`: Frequency of teacher turns
- `total_turns`: Overall dialogue length
- `teacher_turn_ratio`: Proportion of teacher contributions

### Interaction Quality
- `question_density`: Teacher question frequency (probing/scaffolding)
- `student_response_length`: Average student utterance length
- `dialogue_efficiency`: Turns needed to reach outcome

### Assessment Metrics
- `teacher_typical_confusion_rating`: Teacher assessment of confusion typicality (1-5)
- `teacher_typical_interaction_rating`: Teacher assessment of interaction typicality (1-5)

## 🚀 Methodology

### Phase 1: Data Exploration & Feature Engineering
- Exploratory data analysis
- Feature extraction from dialogues
- Feature validation using ANOVA tests, multicollinearity checks, and Random Forest ranking

### Phase 2: Data Preparation
- Handle class imbalance with SMOTE
- Data scaling and normalization
- Train/test split validation
- Establish baseline metrics

### Phase 3: Model Development
- **Bayesian Network**: Probabilistic graphical model to explore feature relationships
- **Logistic Regression**: Linear model for baseline comparison

### Phase 4: Evaluation & Comparison
- Model performance metrics (accuracy, precision, recall, F1-score)
- Computational efficiency analysis
- Feature importance interpretation
- Educational deployment suitability assessment

## 📈 Key Challenges & Solutions

1. **Severe Class Imbalance** (75.4% / 13.4% / 11.2%)
   - **Solution**: SMOTE synthetic oversampling targeting balanced 33.3% representation
   - Critical for Bayesian Networks which learn P(outcome|features) from observed frequencies

2. **Feature Validity**
   - **Solution**: Three-stage validation pipeline:
     1. ANOVA test (p < 0.05)
     2. Multicollinearity check (|r| > 0.95)
     3. Random Forest feature ranking

3. **Data Quality**
   - **Solution**: Validation pipeline to detect anomalies (zero-turn dialogues, missing fields)
   - Robust imputation strategies for missing data

## 🛠️ Technologies Used

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

- **Machine Learning**: Scikit-learn, imbalanced-learn (SMOTE)
- **Bayesian Networks**: pgmpy
- **Data Analysis**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Statistical Testing**: SciPy, statsmodels

## 📓 Project Structure

```
mathdial/
├── project.ipynb          # Main Jupyter notebook with full analysis
├── pics/                  # Visualizations and figures
└── README.md             # This file
```

## 🎓 Educational Impact

This project contributes to:
- **AI Tutoring Systems**: Understanding which teaching strategies work best
- **Pedagogical Research**: Data-driven insights into effective mathematics instruction
- **Adaptive Learning**: Identifying early warning signs for struggling students
- **EdTech Development**: Building more effective automated tutoring systems

## 📚 References

- Macina, J., et al. (2023). MathDial: A Dialogue Tutoring Dataset with Rich Pedagogical Properties Grounded in Math Reasoning Problems. EMNLP 2023.
- Cobbe, K., et al. (2021). Training Verifiers to Solve Math Word Problems. arXiv:2110.14168.

## 👤 Author

**Saqib Safdar**
Data Science Training Specialist | London School of Economics
[LinkedIn](https://www.linkedin.com/in/saqib-safdar/) | [Website](https://www.saqibsafdar.com/)

## 📄 License

This project is for educational and research purposes.

---

*Part of AI/ML coursework exploring machine learning applications in educational technology.*
