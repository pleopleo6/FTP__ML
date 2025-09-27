# K-Nearest Neighbors – Questions

## a)

The figure above illustrates the **K-nearest neighbors (K-NN)** algorithm using Euclidean
distance, represented by circles.  
Based on a **majority voting** and **shortest distance** (when tie), which class would the “Test” instance be assigned
to with:

- \(K = 2\) : Tie between red and green but green is closer, so green.
- \(K = 5\) : Blue as the 3 blues are majority
- \(K = 7\) : Tie between red and blue but blue's are closer, so blue.
- \(K = 8\) : Red as it is the majority

---

## b)

Explain in your own words the differences between **instance-based learning** and **model-based learning**.

Model based learning means that there was initially a training that went through the data before inference in order to
adjust its weights, resulting in a function that was determined not mathematically but rather adapted from the data
itself. Although initial training may be expensive, it comes with the advantage that it is more efficient for inference.

As for instance-based learning, the approach is different. Indeed, there is not really a training step, the
previous datas are just stored for inference and when there is a new data coming, it is compared to all the data points,
which is often simple, such as KNN but this learning has the disadvantages that the inference is slower and memory usage
is also higher.

Both methods need some tuning of hyperparameters beforehand.

---

## c)

Is **K-NN** an **instance-based learning** or a **model-based learning**?

It is instance-based, as there is no training. At inference, all data is pushed to memory and the new value is compared.

---

## d)

When are **larger \(K\)** beneficial?

A larger number of K might be beneficial when data has some noise or has too much variability. Indeed, it helps in
accuracy as it
provides a bigger decision point of view when making predictions (more neighbours), possibly making it more stable and
less sensitive to
outliers.

---

## e)

Why are **too large \(K\)** detrimental?

When the algorithm starts looking at points that are too far away (for example, from other clusters), it becomes
influenced by unnecessary data in making the final prediction. This can lead to a loss in accuracy due to poor local
focus.

---

## f)

When used in **classification** mode, what can we do when the first categories have **equal number of votes** with a
K-NN?

As seen in class, there are several options :

- Use the distance as crucial information, for example a closer point = more trust in that class. This could be for
  example implemented by applying a weighted voting. For example by multiplying a trust by 1/dist.
- Another idea with the distances is to choose the class where the distances are in average closer.
- last idea saw is to apply trust based on ranking (distance based ranking.)

---

## g)

Are **K-NN algorithms** good candidates to build a **1’000 classes image classification system**?  
Explain your answer.

Although it is not advised, it may depend in the end to the data at disposal, the features being used and the task
complexity. But in general, we would say :

- 1'000 classes potentially mean that the dataset is quite large, and as explained in previous answers, KNN is an
  instance based model, meaning that for each inference there will be much computational resources needed, also making
  it slower. If the features are the pixels directly, the quantity of operations needed is huge.
- Additionally, 1'000 classes means that there is a higher risk for the model to make mistakes. As KNN is a simple
  model, more advanced models like CNNs or transformers are usually better suited for this scale of image
  classification as they approach deep learning.

---

## h)

Is **K-NN** impacted by the *curse of dimensionality*? Explain your answer.

Yes, it is impacted. As the different points' dimensions grow, so do the distances between them in general, which
increases the sparsity in the given dimension.

The article https://www.geeksforgeeks.org/machine-learning/k-nearest-neighbors-and-curse-of-dimensionality/
mentions that this provokes equal distances between the different entries of the dataset. This phenomenon, known as
distance concentration, makes it difficult for K-NN to distinguish between near and far neighbors, leading to poor
classification performance.

Additionally, more dimensions mean more data is needed, emphasizing the computing difficulties that K-NN may encounter,
as previously explained.

To mitigate this, some feature engineering could be applied with for example algorithms like PCA that could be used in
order to reduce dimensions.

---

## i) *(Difficult)*

What is the **expected error rate** computed on the **training set** with \(K = 1\)?

0% errors as all the points will be placed exactly on top of themselves. 100% overfit.

---

## j) *(Difficult)*

What is the **expected error rate** computed on the **training set** with \(K = 2\) and a **shortest distance based tie
resolution**?

Again 0% error. Whenever there is a tie, the algorithm will choose the nearest point = the same point itself, so the
distance is still 0.