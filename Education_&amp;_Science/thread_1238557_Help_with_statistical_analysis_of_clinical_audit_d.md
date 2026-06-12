---
title: "Help with statistical analysis of clinical audit data"
date: 2009-08-12
forum: Education &amp; Science
---

### Post by ugm6hr on 2009-08-12
I'm afraid I'm not a statistician, but rather a physician, so excuse any glaring errors in my understanding...

I have data pertaining to the X-ray doses of a number (about 130) of patients who underwent the same procedure (currently in an ods spreadsheet).

X-ray dose is a continuous variable, with lower limit of 0.

A picture of the frequency histogram / bar chart is attached.

From my memory of college stats, this perhaps resembles a skewed binomial distribution, or was it Poisson?  While I would often just quote median and centiles, I thought it might be nice to use a mean and standard deviation, given the continuous variable.

I have now downloaded and installed gretl (which I like), PSPP (which I think is a bit limited), and R-CRAN (which I don't have the inclination to learn to use for just this 1 project).

How can I use one of these to:

1. Find an appropriate fitting distribution to super-impose on my frequency histogram?

2. Find the mean / sd of this distribution?

If I get help, I may be back needing advice on comparing 2 separate populations (I think a t-test is what I need)...

---

### Post by gunksta on 2009-08-12
Let me start this with a very simple fact: I am not a physicist and I am not a doctor. My usual realm of statistics is in the social-services and psychiatry.

That being said, sometimes numbers are just numbers. I won't really pretend to understand exactly what these numbers mean, but I have a few thoughts.

I'm concerned with using a straight up mean on this data. Like many data sets, this data set is obviously skewed (positive skew in this case). On the far left side, you have a very steep tail. On the right side you have a very long tail.

Why is this?? I don't have any idea. But, I can tell you that using a mean (average) with a strongly skewed data set is usually a recipe for a mis-leading number. One caveat is that I do not know what measure of central tendency is normally used in this particular field. For all I know, everyone ignores the skew and just reports the average. I'd love to hear form someone with more experience measuring x-ray dosages (do we have such a person?).

In my experience, median and quantiles would give you a more accurate shape description of the data.

As for a t-test (comparison of means) you can use it to compare two groups, but again you have to to deal with the skew. Before running a t-test, you should run the log of the numbers. This will tend to eliminate the skewness of the data, which makes it possible to compare two different groups, although the resulting averages are, in and of themselves, basically meaningless.

This is the 5 minute answer. I'm getting ready to leave work. I'm curious to see if anyone else has any thoughts on this.

---

### Post by tgalati4 on 2009-08-12
You are using a linear scale for dosage from 0 to 8000.  Perhaps changing to logarithmic scale for dosage will yield a more useful/descriptive curve.

I'm assuming that radiation behaves like light, sound, and other physical transmissive waves, where doubling of the quantity is perceptable.  Doubling sound pressure results in a 3 dB increase, which is noticeable.  A linear increase in sound is hard to quantify.

Edit:  Depending on what radiation units you are using, a linear model may be more useful:

[http://en.wikipedia.org/wiki/Linear_no-threshold_model](http://en.wikipedia.org/wiki/Linear_no-threshold_model)

---

### Post by ugm6hr on 2009-08-13
Thanks for the advice so far.

As mentioned, I would normally use median / quartile / centiles for description of data spread and comparison, but I was wondering whether a non-normal model could be used.

The dose is actually a patient Dose-Area-Product: [http://faxil.leeds.ac.uk/learning/dose/measures/patient/dap.xml](http://faxil.leeds.ac.uk/learning/dose/measures/patient/dap.xml)

The reason for the positive skew is that the procedure complexity is dependent on multiple factors, including patient size, patient anatomy, specific procedure type and operator experience.  The dose cannot be less than 0, and most procedures are "straighforward" and constitute the bulk of the weight in the left of the data spread.  Occasional procedures are more complex, and can therefore require an unlimited dose / radiation exposure, leading to the long tail to the right.

As for what the standard description for central tendency, I don't know.  Publications relating to "recommended" or "target" **maximum** doses have used a 3rd quartile of population sample.  Description (in different publications) have included: mean and range; mean, median and quartiles.  This reporting of means without standard deviation or skewness was why I thought a better model might be obtained with more detailed analysis.  However, I may just stick to median and quartiles if that is the advice.

As for using a logarithmic scale, I do not think that the actual numbers would mean anything, although if a mean of the log data is felt to be a better comparison for a t-test, then that is acceptable (given that it will be a yes-no hypothesis).  The hypothesis would be to break down the data into "senior" and "junior" operator data, with a null hypothesis that means are the same, and alternative that senior operator doses are lower (i.e. I think 1-tail t-test).  However, if the t-test is felt inappropriate, I won't bother (the data set is smaller than anticipated due to lots of exclusions, so it is unlikely to reveal a significant difference).

I will calculate log data and repost a picture.  EDIT: Done - total LnDose data is less skewed.  Perhaps a t-test of this is more appropriate?

---

### Post by sdbrogan on 2009-08-13
Your data are certainly not Poisson or binomial, as those are discrete distributions.  It looks like a gamma distribution might be suitable (with a shape parameter around 1.2).

The R package fitdistrplus has some v. good tools for fitting various distributions: you would use [FONT="Courier New"]gfit<-fitdist(x,"gamma")[/FONT] for a maximum-likelihood fit, [FONT="Courier New"]summary(gfit)[/FONT] for parameter estimates & some goodness-of-fit statistics, & [FONT="Courier New"]plot(gfit)[/FONT] for some diagnostic plots. To compare two populations, you would probably use the generalized linear model function [FONT="Courier New"]glm[/FONT] with [FONT="Courier New"]family[/FONT] & [FONT="Courier New"]link[/FONT] set appropriately.

But thats a lot of fuss (for a non-statistician) just to come up with some descriptive statistics for your data & test for differences between two groups; it would be worth it if you had a theoretical motivation for wanting knowing the distribution or needed to do more complex modelling.  Gunksta's advice is sound (& if you have two gamma populations with the same shape but different scales his log transformation will also stabilize the variances for your t-test). 

PS Looks like you have an outlier in that last plot

---

### Post by ugm6hr on 2009-08-13
The gamma model appears to be in gretl too, and available with a few clicks.  I have reviewed the data, and removed some confounding data points (to be analysed separately).  There is still 1 outlier, which I need to check the accuracy of the data for.  I've attached the gretl graph again to ensure this is reasonable.

Nevertheless, after the advice here (thanks for that), I've decided to go with quartiles for description.  Is there an easy way to get quartile results out of gretl (or R - gretl can load the data set into R).  I would normally just sort in the database, and pick out the relevant results, but I figured it might be useful to know how to do this with these new bits of software.

I will go on to do the t-test to compare logs of the means of the 2 subsets later (I may need advice on how to do that too).

Thanks again.

EDIT: found quantile in R
quantile(EnteredDose, na.rm=TRUE, type=4)

Found the test statistic calculator in gretl for t-test

---

### Post by gunksta on 2009-08-14
EDIT: Never mind. Upon re-reading your posts I now realize that the graphs were in fact produce in R, which is why they look like R plots. I will now go sit in the corner.

Looks like you are making some progress. And, I could be totally off-base here, but those plots look ALOT like R plots. Is gretl a front-end for R?

(Sorry, not trying to disrupt the thread.)

---

### Post by ugm6hr on 2009-08-14
> **gunksta said:**
> I could be totally off-base here, but those plots look ALOT like R plots. Is gretl a front-end for R?

I didn't think so, but it does launch an R Terminal using your data.

Either way, I think it is brilliant.

---

### Post by IanH on 2009-08-15
The t-test assumes your data follows a normal distribution, which this clearly does not. It is a pretty robust test (that is, it tends to work reasonably even when assumptions are wrong), but you'd be better off with a nonparametric alternative. The Wilcoxon-Mann-Whitney should work for you data, and I'm fairly sure there is an R package supporting it on CRAN. The WMW is similar to the t-test, but tests for differences in medians, using the ranks of observations rather than their actual values. This allows you to get rid of any distribution assumptions, as ranks are always uniformly distributed.

---

### Post by sdbrogan on 2009-08-17
Bear in mind he's planning to transform the data before the t-test, so the transformed data should be normal. If they're not (& there's no guarantee of finding a suitable transformation) the Mann-Whitney test is a good idea.  The flip side of its making fewer assumptions is that it's less powerful than parametric tests.
I often like to do two tests, one parametric & one non-parametric.  Much of a difference alerts you to the fact that your conclusions are sensitive to distributional assumptions, which is worth knowing.

---

### Post by ahmatti on 2009-08-19
> **IanH said:**
> The Wilcoxon-Mann-Whitney should work for you data, and I'm fairly sure there is an R package supporting it on CRAN. 

This is in R base (meaning it install with the default installation) as "wilcox.test" and I agree it is a safe alternative to t-test, because you can use it on any distribution and it almost as efficient as t-test even for normally distributed data. Doing both and seeing how they agree is not a bad idea either. 

BTW. t-test is "t.test" in R

---

### Post by gunksta on 2009-08-19
The Wilcoxon-Mann-Whitney is a non-parametric test. Thus, it makes fewer assumption about the data. For example, the t-test assumes that the data conforms (roughly) to the normal distribution. When this isn't the case, you can use a log to (usually) correct this. In contrast, the Wilcoxon-Mann-Whitney does not assume the data conforms to the normal distribution.

What all this mumbo-jumbo means in plain-speak is simple. In order for the Wilcoxon-Mann-Whitney test to show a statistically significant difference, it typically needs a larger sample size than a t-test would. They are not directly comparable tests (they measure different aspects of the distribution) but running both and comparing them is definitely a good idea.

The hard part is deciding what to do if your t-test shows you one thing and the Wilcoxon-Mann-Whitney test shows you another. I've got my popcorn. I'm curious to see your results.

:popcorn::popcorn:

---

### Post by ahmatti on 2009-08-19
The difference is not very big though, I think WMW has [ARE]("http://www.statistics.com/resources/glossary/a/asyreleff.php") of at least (depends on the data) 0.86 as compared to t-test. I wouldn't expect any problems with a sample size of 130 samples, if you have any meaningful results they will show up in either test!

---

### Post by ugm6hr on 2009-08-19
I am still (manually) double-checking some of the data before doing any formal analysis.

I am going to present my findings in October, so will be certain to share them here around then.

---

