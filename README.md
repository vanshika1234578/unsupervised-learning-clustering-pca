# Unsupervised Learning: K-Means, DBSCAN and PCA

Notes and code for three core unsupervised learning techniques in scikit-learn. All data is synthetic (`make_blobs`, `make_moons`), so no dataset file is needed. Unsupervised means there is no target column: the algorithm finds structure on its own.

## Concepts

**Scaling (`StandardScaler`).** K-Means and DBSCAN use distances and PCA uses variance, so features are scaled to mean 0 and standard deviation 1 first.

**K-Means.** Splits data into K groups around centroids. Place K centroids, assign each point to the nearest one, move each centroid to the mean of its points, and repeat until nothing changes. You must choose K in advance.
- **Inertia (WCSS):** sum of squared distances from points to their centroid. Lower means tighter clusters, and it always falls as K grows.
- **Elbow method:** plot inertia against K and pick the point where the drop flattens. Here inertia went 1000, 297.9, 11.6, then declined slowly, so **K = 3**, matching the 3 centres in the data.

**DBSCAN.** Finds dense regions and needs no K. `eps` is the neighbourhood radius and `min_samples` is the number of points needed to count as dense. Points are core, border or noise, and noise gets the label **-1**. It can follow curved shapes.

**PCA.** Finds new axes (principal components) that capture the most variance, so data can be described with fewer columns. Reducing dimensions **always loses some information**. In this notebook there are 2 features and 2 components, so PCA only rotates the axes and nothing is reduced.

## K-Means vs DBSCAN

| | K-Means | DBSCAN |
|---|---|---|
| Choose K? | Yes | No |
| Shapes | Round, similar size | Any shape |
| Outliers | Forced into a cluster | Marked as noise (-1) |

On two-moons data, K-Means (K = 2) cuts across both moons, while DBSCAN (`eps=0.3`, `min_samples=5`) separates them correctly.

## Notebook contents
1. K-Means with the elbow method on 3 blobs
2. K-Means vs DBSCAN on two moons
3. PCA on 3 blobs, plotted as PC1 vs PC2

## Tech stack
Python, pandas, seaborn, matplotlib, scikit-learn, Jupyter

## How to run
    git clone https://github.com/vanshika1234578/unsupervised-learning-clustering-pca.git
    cd unsupervised-learning-clustering-pca
    pip install -r requirements.txt
    jupyter notebook unsupervised_learning_kmeans_dbscan_pca.ipynb
