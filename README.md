# Pulsar Stars Classification in Semi-Supervised Learning

The goal of this project is to explore and compare the
performances of the Gradient Descent method (GD) and the
Block Coordinate Gradient Descent methods (BCGD) with randomized
and cyclic rules, in Semi-Supervised Learning.

For this purpose, we will first consider a convex function
minimization problem with respect to randomly
generated points in the 2D space (Toy example). 

Secondly, we will
approach the same problem on a real-world dataset, namely the [HTRU2 dataset](https://archive.ics.uci.edu/ml/datasets/HTRU2) containing a sample
of Pulsar candidates, labeled as Pulsar or Non-Pulsar
stars. Each Pulsar candidate is described by some
continuous statistic measures (mean, standard deviation,
kurtosis and skewness) of the integrated profile
and the DM-SRN Curve, for a total of eight features.

In particular, the classification task is carried out by
examining the feature similarities of the data (see `report/essay.pdf` for more details).

# Toy example

First, we consider a balanced toy example of 400 labeled
and 1000 unlabeled datapoints, generated from
two Gaussian distributions with same variance but different
means. 

There's almost the same smooth gradient
decreasing for GD and Cyclic BCGD, while Randomized BCGD produces a much more irregular
decreasing, since it modifies just one component of the iterate
at each timestep. 

<p align="center">
  <img src="https://github.com/silviapoletti/Semi-supervised-pulsar-stars-classification/blob/d2f7e0b5cd6b67a902707e35f7df85d4c32791b6/report/scatter_toy.png" width="40%"/>
  <img src="https://github.com/silviapoletti/Semi-supervised-pulsar-stars-classification/blob/d2f7e0b5cd6b67a902707e35f7df85d4c32791b6/report/gradplot_cropped.png" width="40%"/>
</p>

Randomized BCGD is the
fastest method because the calculation of the partial
derivatives is much cheaper than computing the whole
gradient, but, for the same reason, it requires much
more iterations to converge.

Cyclic BCGD computes some partial gradients
at each iteration, while GD directly computes the
full gradient. Since the computational complexity of BCGD methods depends on the number of
blocks, then Cyclic BCGD
needs slightly fewer iterations but higher CPU time
than GD to converge.

In conclusion, all the three methods are able to reach
an accuracy of almost 92%.

# Pulsar stars dataset

Since the HTRU2 dataset is strongly unbalanced, we
selected a balanced subset composed by 800 labeled
and 1500 unlabeled datapoints.
This dataset is particularly suitable for our application
because the features of the datapoints are almost
linearly separable, as shown in the following plot.

<p align="center">
  <img src="https://github.com/silviapoletti/Semi-supervised-pulsar-stars-classification/blob/a3ae75bf8d1fa7a6011935561047fe94f184f465/report/pair_plot.png"/>
</p>


<br />
