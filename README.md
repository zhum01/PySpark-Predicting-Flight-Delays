# Predicting-Flight-Delays

**All notebooks exported from databricks.**

**Objective:** Develop and evaluate models to predict flight delays of >15 minutes after scheduled departure time, using only information available at least 2 hours before the scheduled departure. 

**Data sources:** Our main data sources are information on ~31 million flights departing from U.S. airports from 2015–2019, and ~630 million observations from U.S. weather stations over the same time period.

**Evaluation Metrics**
We will use primarily 6 metrics to evaluate the performance of our models: accuracy, precision, recall, F1 score, time required to train the model, and time required for the model to make a prediction on unseen data. The reasoning for using each of these metrics is as followed:

**Accuracy** gives an overall sense of how many correct predictions the model makes, both true positives (correctly predicted delays) and true negatives (correctly predicted not delays). Importantly, due to the class imbalance of the data set (discussed in EDA section), we will always need to keep in mind that chance level is ~80% accuracy for a naive model that predicts only class 0 (no delay). 

**Precision and Recall**: Precision measures TP/(TP + FP) (i.e. given that the model predicts a delay how often is the prediction correct), while recall measures TP/(TP + FN) (i.e. given that there is actually going to be a delay how often can the model predict the delay beforehand). These two metrics represent a tradeoff in capabilities of the model, and potential users may value one metric more than the other. For example, airlines may value recall more because being able to predict as many delays as possible may save more money than the costs of making an incorrect prediction of a delay, whereas some passengers may value precision more because they want more confidence that the prediction of a delay will be correct. Therefore, we will report both metrics so any user of the model can make an informed decision based on which ability the model is better at. We put particular emphasis on the importance of precision in our research question and when evaluating models because we will work under the assumption that making precise predictions is more valuable in most situations.

**F1 Score** represents a composite score (harmonic mean) of precision and recall so while it suffers from a lack of intuitive interpretation that precision and recall have alone, it does give a single metric that weights each component equally, which is useful for assessing model performance as models are tuned.

**Time Required for Training and Prediction**: These metrics will try to capture the third major component of our main question for this project: the cost efficiency of the algorithm. Because both the runtime of the model and the economic costs associated with it will likely be important in most use cases, we wanted to also consider runtimes in evaluating overall model performance. Though for this project, these metrics will likely be heavily influenced by confound variables -- most likely by the number of jobs running on the shared cluster at different times when we run the models -- we will still report them in our model results and believe they can be especially important metrics to use in situations when we have more control over the load on the cluster.

We will evaluate overall model performance by having a good balance of all the above metrics. In particular, to compare models we will use F1 scores and runtimes because they respectively provide composite metrics of key constructs we are trying to optimize: precision and cost efficiency.
