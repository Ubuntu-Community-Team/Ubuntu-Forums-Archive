---
title: "analysis of categorical data"
date: 2009-08-24
forum: Education &amp; Science
---

### Post by tommers on 2009-08-24
From a somewhat ill-designed education experiment, I have categorical data with two between subject variables and one within subject variable.  Since it is categorical (essentially counts of answer choices on multiple choice questions), I'm looking for some chi-squared method.

I know how to generalize Pearson's chi-square for n between subject dimensions, and I know McNemar's test for a within subject factor, but how can I mix these methods?

Also, I need to be able to do post-hoc comparisons in all dimensions.

Any ideas or references?

I'd be happy to share more details as needed.

Thank you.

---

### Post by gunksta on 2009-08-24
I'm more than willing to help and I know that there are several other people here who tend to jump into statistics related questions. 

For starters, do you have any particular software choices? There are several people here (myself included) who tend to pull out R, but it's not a tool that everyone is comfortable with. If you have experience with SPSS/PSPP or Excel/Sheet these can also be perfectly reasonable choices. The latter is especially obvious if the data set is fairly small and is already in a spreadsheet.

You also seem to have a basic understanding of the chi-square and mcnemar tests which is a good start an analysis of categorical data.

If you can, post some of the data, or a table that you are trying to figure outm along with an explanation of what you are trying to do. It's a starting point at least.

---

### Post by tommers on 2009-08-24
For almost all computations and analyses, I use R.  I'm a physicist, so I don't have much formal training in statistics - and unfortunately, all the sources that I typically use don't discuss mixed designs with categorical data.

Here is a sample from the data.  All together, there are 366 subjects.  There are 4 levels of Test_no (1,2,3,4), Ans1 and Ans2 are the within subject measures, and there are 8 levels of Ans* (cor, SE, CP, CPSE, FoM, FoMSE, zero, other).

Thanks, again!

SID	Test_No	Ans1	Ans2
1	1	other	other
2	1	CPSE	CP
3	1	other	other
4	1	SE	SE
5	1	FoM	CP
6	1	FoM	CPSE
7	2	cor	cor
8	2	cor	cor
9	2	cor	cor
10	2	CPSE	CPSE
11	2	cor	cor
12	2	CPSE	cor
13	2	CPSE	cor
14	3	CP	cor
15	3	cor	cor
16	3	CP	FoM
17	3	cor	cor
18	3	cor	cor
19	3	zero	other
20	3	SE	CP
21	3	SE	FoM
22	3	CP	CP
23	4	zero	SE
24	4	CPSE	cor
25	4	SE	cor
26	4	CP	CP
27	4	SE	cor
28	4	SE	SE
29	4	CPSE	cor

I would like to be able to compare different answers within a test, and how answers are different for different tests.

---

### Post by gunksta on 2009-08-26
Late last night I took this and pulled it into R and started playing with it. I made a table with the various test runs (1-4) as rows and the ans1, ans2 as columns.

I'll put up what I did later today (I forgot to e-mail it to myself here at work).

Since you said you are familiar with R, where in the process are you running into problems?

---

### Post by tommers on 2009-08-26
It's much more of a statistics question than an R question - I don't know how to analyze categorical data from a design that mixes between and within subject factors.  

It looks like generalized estimation equations could provide a solution, but is there a more simplistic approach?  What technique would provide the most reliable inference, and yet be understandable to readers of science education journals?

---

### Post by spinoza666 on 2009-08-26
Well I should be going to bed, but can't resist giving a quick response to your query:)

If you use R, and have access to "The R Book" or something of that sort, I would look up statistical modelling and check out mixed models. I should think that would be a good place to start for some basic statistics with this kind of data, and then do tests for specific hypothesis that you're interested in.

Right, that was all. Good night!

---

### Post by spinoza666 on 2009-08-26
Argh! Forgot something.

Beware of pseudoreplication with this kind of data. Most techniques will kill your sample size, while this is the kind of thing that mixed models take care of, so check it out and see what you think.

Again I bid you farewell

---

