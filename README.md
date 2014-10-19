MatlabAUC
=========

This download provides a few Matlab functions for plotting ROC curves, estimating the area under the ROC curve (AUC), and various methods for estimating parametric and non-parametric confidence intervals for the AUC estimates. Also included is code for a simple bootstrap test for the estimated area under the ROC against a known value. The available CI estimation methods are:
* Hanley-McNeil, parametric [1]
* Mann-Whitney, non-parametric [2]
* Maximum variance, non-parametric [3]
* Logit, non-parametric [2]
* Bootstrap, non-parametric [2]

You can pass arguments through for different bootstrapping options, otherwise the default is a simple percentile bootstrap. This software depends on several functions from the Matlab Statistics toolbox, namely norminv, tiedrank and bootci.

[1] Hanley, JA, McNeil, BJ (1982). The meaning and use of the area under a receiver operating characteristic (ROC) curve. Radiology, 143:29-36
[2] Qin, G, Hotilovac, L (2008). Comparison of non-parametric confidence intervals for the area under the ROC curve of a continuous-scale diagnostic test. Stat Meth Med Res, 17:207-21
[3] Cortex, C, Mohri, M (2004). Confidence intervals for the area under the ROC curve. NIPS Conference Proceedings

Instructions and example:
Install the functions under your Matlab path and have a look at `Testing/demo.m`. If you're impatient, the following will get you started right away:

```
>> s = randn(50,1) + 1; n = randn(50,1); % simulate binormal model, "signal" and "noise"
% Estimate the AUC and calculate bootstrapped 95% confidence intervals (bias-corrected and accelerated)
>> [A,Aci] = auc(format_by_class(s,n),0.05,'boot',1000,'type','bca')
```

The following figure shows the results of some monte-carlo simulations I ran to explore the different confidence interval estimators. Each set of colored data represents 1000 simulations for a different confidence interval estimator (simulation details follow the figure). The bootstrap and logit methods appear to have the best coverage for more extreme AUC values, tending to widen a bit closer to 0.5.
<img src="http://www.subcortex.net/research/code/area_under_roc_curve/auc-confidence-interval-comparison.png" alt="Drawing" style="width: 700px;" />

## Contributions
Copyright (c) 2014 Brian Lau [brian.lau@upmc.fr](mailto:brian.lau@upmc.fr), see [LICENSE](https://github.com/brian-lau/MatlabAUC/blob/master/LICENSE)

