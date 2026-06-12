---
title: "Statistics and Matrices"
date: 2010-12-08
forum: Education &amp; Science
---

### Post by d5xtgr on 2010-12-08
I would like to find coefficients by which to multiply each of many vectors in order to achieve a desired distribution of the multiple vector elements, while all the elements within a vector maintain their ratios of separation.  I'm not a statistics expert, and I find a lot of literature about fitting curves to data but not data to curves- I'd like to find a method to do this.

Put in explicit terms, I have a matrix A with m rows and n columns and a curve g(x), which we'll assume is defined everywhere that is relevant.  Multiplying A by an n-row column vector x returns an m-row column vector B.  I want to find x such that a histogram (of specified bin size) showing the frequency of terms of B resembles g(x) as closely as possible- I'm not nearly knowledgeable enough to make an informed choice about different fitting methods, so 'as closely as possible' is somewhat open to interpretation.  I need to be able to constrain the elements of x, for example by naming their sum and establishing ranges some or all elements must obey.  I can do this by hand, but if there's a way to do it automatically I'd love to hear about it.

An example application would be a way of applying amplitude (volume) modification to multiple audio streams over time- if I know the volume at many times on multiple input streams, the time is the row index and stream the column index, with volume as the array elements.  The process should be able to provide me with the coefficient by which to multiply each stream input in order to achieve a given distribution of samples of the total volume taken at many times- the constraints here would be simple non-negativity of the coefficients.  By inputting different curves, one could increase the dynamic contrast between loud and soft points, normalize them to be closer to a mean value, et cetera.  The ratio of the volumes at two points in any amplified stream would still be the same as the original.

I intended to use the fit feature in gnuplot, but either its capabilities don't extend to this sort of application or I haven't figured out how to properly apply it.  I also have MATLAB, although I am not familiar with a great deal of it; I would much appreciate hearing your ideas using either one of these programs or another with which you are comfortable.

Thanks much
d5

---

### Post by Choragos on 2010-12-22
This might be too late for your interest, but if so, can I see if I understand this properly?

So you have matrix A, and unknown vector x.  You want A*x to have a distribution that looks like g(x) or you want A*x to be as close as possible to g(x)?

---

### Post by d5xtgr on 2010-12-22
It's the distribution in which I'm interested; elements of A*x need not be prescribed.  I wish it were that simple!

Matrix A is likely to have significantly more rows than columns; I doubt whether I would have sufficient degrees of freedom in x to get anything close to the desired result if I were to explicitly spell out the product A*x.

It's never too late to learn something new.  I'm sure that in the future I will again find applications for this method, and I would be pleased to learn how to implement it.

Many thanks for your time
d5xtgr

---

### Post by spinoza666 on 2010-12-23
Hmm,

I'm sure that if you provide some sample data, and the name and parameters of the desired distribution, it would be possible for some of the more statistics savvy to be of assistance.

You say you can do this by hand, so it's probably a good idea to give short example of how you do this as well.

---

### Post by d5xtgr on 2010-12-23
"I can do this by hand" was in reference to the constraints, not the entire solution; sorry if I was unclear.  The idea was to inform readers that while I would prefer a method with the ability to apply constraints from the start, I would still appreciate learning of methods without this feature.

For example, if I were able to find an optimal candidate for x that had an element beyond the acceptable maximum, I would
-fix that element at the maximum and all others at zero, resulting in a column "x'"
-compute Ax' and determine its mean "&#956;"
-modify A by removing the column associated with the coefficient in question, resulting in A' (m rows and n-1 columns)
-find a candidate y of n-1 rows such that A'y fits g(x-&#956;) optimally.

To be honest, this would work in a pinch, but I am less than satisfied with it.  It should result in a distribution with the correct mean, but if I need to iterate this to fix multiple unacceptable coefficients I imagine I would end up altering the deviation of the distribution.
Also, it's predicated on the ability to find the optimal values for the elements of x, which I still lack; I expect I would find difficulties in practise that aren't apparent in the principle.

---

### Post by Choragos on 2010-12-23
What an interesting problem; I've never considered this before.  If it were as easy as A*x=g, then of course (A'A)^-1*A'g would yield x in a least-squares sense.  Then you could set this up as a global objective function (phi) to minimize as:

phi = phi_d + beta*phi_m + logbarrierterms

Beta is a tradeoff parameter, phi_d is your misfit function, and phi_m is a model weighting term where you can add all your model penalties.  Then in the log barrier terms you can add whatever constraints you want.

However, to get x that gives you a distribution that looks like g is quite another matter.  I suspect there's a way to go about it in the same way, but I'm just not sure.  I'll ask around the office--maybe one of those Bayesian people know the answer.

---

### Post by Choragos on 2010-12-23
Oh, and the method I described can handle severely underdetermined problems if you add in model constraints.

---

### Post by Choragos on 2010-12-23
Sorry for the multiple posts, but this just occurred to me.  The Bayesian geophysicists have this nearly covered.  See if you can find any literature on Bayesian inversion of geophysical data--I think that will point you in the right direction.  They're solving for the distribution, though.  Might be something there you can pull out.

I'm a frequentest so I tend to solve systems for an explicit, prescribed g.  (e.g. x is a model, b is measured data, and A is a sensitivity matrix that contains all the physics and geometry, so we're solving Ax=b+n where n is noise.  We wish to find x subject to bound constraints, data misfits, model characteristics, etc.  This is frequently severely underdetermined, and bound constraints make it nonlinear.)

---

### Post by d5xtgr on 2010-12-24
As requested by spinoza666, an example data set.  Let the matrix represent nine students' performance in a course with three assignments.  The mark earned by each student on each assignment may be found as an element of the matrix, with the row index corresponding to the student and the column index corresponding to the assignment.

80	55	54
50	70	72
80	70	68
100	80	60
90	60	80
90	65	82
100	75	78
90	95	84
100	90	94

Assume the instructor desires a normal distribution for the overall marks awarded to students at the end of the course, with a mean of 78 and a standard deviation of ten.  The plot "hist1" shows the distribution of the final marks if he chooses to count the first mark for thirty percent of the overall mark, the second for twenty percent, and the last mark for fifty percent; the corresponding column vector would be <0.3;0.2;0,5>.  This distribution matches the desired curve closely: each bar matches the integral of the curve to the nearest integer, as you cannot have half a student in any bin, and the mean and deviation are exactly 78 and ten respectively.  Should the weighting be altered to count the second mark as forty percent and the first for only ten, the distribution matches much less closely, as one may see in the plot "hist2".  The mean in this case, for a coefficient vector of <0.1;0.4;0.5>, has dropped to 75.3 and the deviation has increased to 10.8.

In this example, constraints may be nonnegativity, so that no student hurts his mark by performing well, and that the sum of the coefficients is 1, so it is possible to achieve perfect marks.  It may also be desired that a given coefficient is the greatest if it corresponds to an exam, for instance, while the others represent less consequential assignments.

Thank you, Choragos, very much for your thoughtful suggestions.  The literature I have found to this point in the fields you suggested is rather specialized; it will take me some time yet to understand the bulk of it, but it is very much appreciated.

---

