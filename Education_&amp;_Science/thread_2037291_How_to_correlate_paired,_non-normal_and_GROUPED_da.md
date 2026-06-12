---
title: "How to correlate paired, non-normal and GROUPED data?"
date: 2012-08-04
forum: Education &amp; Science
---

### Post by Cubytus on 2012-08-04
Hi, community, 

I'm trying to solve this issue using free software on Mac OS X and Ubuntu, namely PSPP (SPSS-compatible), Gnumeric, LibreOffice, [SOFA statistics]("http://www.sofastatistics.com"), and of course, R, although I would like to avoid the latter since it is not interactive and may have trouble importing very large CSV files.

[INDENT][COLOR="silver"]Optional note: **group1** to n are individuals, **data1** to 4 are a timing measure on different trials, **dataA** is an manual ability assessment made for each individual. Timings were classified according to a unique method, and two hypothesis are tested: 1 -wether there is a link between the motor assessment and the timing observed, and 2- has the classification used for timing measure a valid operational background? Data is taken from a sub-clinical and borderline population, and as such can't be divided further[/COLOR][/INDENT]

I've read the relevant chapters in 3 excellent manuals (Scherrer, *Biostatistique*, 1984; Sokal & Rohlf, *Biometry*, 1995, Legendre & Legendre, *Numerical Ecology*, 1998), but the case I'm about to expose doesn't seem to appear there. My background is in neurosciences with only one elementary statistics course, so please excuse my ignorance there as I try to explain the problem without unnecessary details.

The experimental situation is as such (shortened to keep this post readable):
```

Group1
data1   dataA
data2
data3
data4

Group2
data1   dataA
data2
data3
data4

Group3
...
```
**data1** to **data4** are continuous variables, with a *n* around 1600 (24 in each **group**. First issue is this variable isn't normally distributed (not even close, either inside each group, or across groups), no matter which transformation is applied to them. Therefore, I can only use non-parametrics statistics there.

**dataA** is an discrete variable. *n1* is different from *nA*.

**data1** to **data4** are paired to **dataA**, respectively, in each group. For this experiment and to simplify the model, **Group1**, **Group2**, **Group3** are independant. **Data1** to **data4** are not the same order of magnitude as *dataA*.

To eliminate the different order-of-magnitude between the data, I though about categorizing it. At first, this was intended to make a Chi-square test feasible, but using only 5 categories (arbitrary number), 92%+ of data was in category 1. I can't remove outliers since they may be the most meaningful, biologically speaking. I then tried to find a way to make an appropriate number of classes and assimilated the concept to that of "bins" in histograms. As Sturge's and Yule's rules are supposedly quite inaccurate for large *n*, I found a paper that supposedly describes the ideal number of bins to use (equal width), but I just couldn't understand it (too many formulas I don't understand, and that chains up):
Birgé & Rozenholc (2006), ESAIM: Probability and Statistics, HOW MANY BINS SHOULD BE PUT IN A REGULAR HISTOGRAM [DOI: 10.1051/ps:2006001]

From what I understood from the three manuals, I could use either the Wilcoxon rank-sum test pr the sign test. As much as I want to compare **data1** to **data4** with **dataA** across all groups, I want to make sure possible links between **data1** to **data4** from each group are accounted for and do not "contaminate" inter-group results. 

Of course, this would be much easier if I could simply replace **data1** to **data4** with their mean, but since data is highly non-normally distributed, I think this would increase type II error - that **data1** to **data4** have no relationship to **dataA** in group1, although they would.


***
A friend of mine suggested I answer the hypotheses using a 2-step process, but fell short of time to explain it further: 1- is there a link between data1 to 4 and dataA? 2- How link (if any) between data1 to 4 is NOT explained by the test?

Considering my limited knowledge of statistics, I know non-parametric tests such as the *sign test* and *Wilcoxon signed-ranks test* allow for different *n* in each column, and that these test require reordering. As such, how can I make sure ***data1*** to **data4** from ***group1*** are not compared to **dataA** from **group2**, for example?

---

### Post by gunksta on 2012-08-08
Is there any way you can put up a subset of your data? Trying to imagine your data AND think about what you are trying to do is a bit much.

IF you can't put up some actual data, could you put up some disguised data that may be meaningless but will at least help someone visualize how all this fits together?

---

### Post by Cubytus on 2012-08-08
Fine, replace the "code" snippet with this one:

data1 to data4 are, in turn, °cCG, °cCD, LatCG, LatCD, PA-CG, PA-CD, CPC (CG), CPC (CD). Value is decimal with typically a wide range.
For CPC,CG and CPC,CD, value is a numerically coded category. No hierarchy is assumed, and is one of the goals of this research.

DataA is, in turn, Count 1 and Count 2, then Total. Value is an integer between 0 and 9 for Count 1 and Count 2, and from 0 to 18 for Total. These values are ordered.

Group1 is numerically coded 101302, Group 2 is 101303, and so on, until there are 275 groups. Each first 5 digits in the group number makes up an even-higher super-group. Here, 101302 and 101303 are members of the same 10130 super-group. Not every super-group feature a complete pair, and my supervisor wouldn't help me setting appart the two actual classes of super-groups that are supposed to exist. So, I (wrongly) assume independance of sub-groups (6-digits).

This is a slightly modified excerpt from the actual file.

```

	°c. CG	°c. CD	Lat CG	LatCD	PA-CG	PA-CD	CPC (CG)CPC, CD	Count 1	Count 2	Total
101302		1,68		1606		9,17		2	0	2	2
		0,67		1436		12,87		2			
	3,42		1958		7,83		2				
	11,12		1140		9,37		2				
		1,24		1158		9,68		2			
		0,81		1268		10,22		2			
	5,66		1082		46,49		2				
	4,18		1200		5,84		2				
		2,46		702		13,43		2			
		0,01		1476		6,55		2			
	10,20		810		9,02		2				
					4,09		0				
		3,35		674		4,71		2			
		10,67		362		13,93		2			
	6,13		1370		7,91		2				
		2,30		374		6,49		2			
	5,14		1574		5,91		2				
		5,09		398		11,86		2			
	8,36		978		10,20		2				
		2,19		1044		8,42		2			
	8,16		1440		7,91		2				
	3,86		1486		9,64		2				
		1,52		866		7,46		2			
	2,71		1158		5,94		2				
	°c. CG	°c. CD					CPC (CG)CPC, CD			
101303		2,70		898		5,79		2	1	3	4
		3,19		1010		9,01		2			
	8,73		490		3,89		2				
	0,42		1258		4,20		2				
		1,24		852		4,59		2			
		1,21		950		9,89		2			
	8,53		400		9,35		2				
	3,15		1242		16,69		2				
		2,15		998		5,29		2			
		5,11		890		6,09		2			
	2,03		914		3,99		2				
	4,18		908		6,32		2				
		0,53		580		7,22		2			
		2,41		986		7,89		2			
	1,43		1036		5,91		2				
		1,03		954		10,94		2			
	11,84		714		4,71		2				
		2,81		732		7,79		2			
	3,39		1116		6,66		2				
		0,26		884		12,51		2			
	4,44		1232		8,58		2				
	2,54		1262		5,05		2				
		6,26		870		0,75		2			
	0,46		1134		4,56		2				
	°c. CG	°c. CD					CPC (CG)CPC, CD			
101502		7,66		448		11,83		2	4	1	5
		5,01		492		12,41		2			
	0,61		612		6,04		2				
	1,47		902		16,96		2				
		4,07		518		11,84		2			
		6,61		560		9,58		2			
	2,20		578		14,79		2				
	1,04		548		3,51		1				
		2,93		594		3,19		2			
		1,84		896		8,95		1			
	2,44		742		14,07		2				
					7,50		0				
		0,29		536		18,13		2			
		0,15		856		25,09		2			
	2,47		506		0,24		2				
		2,78		748		6,63		1			
	2,47		706		9,89		2				
		1,97		626		10,06		1			
	3,82		654		7,01		1				
		0,12		724		7,02		1			
					7,10		0				
					24,67		0				
		5,53		650		24,58		1			
	5,94		614		8,13		2				


```

The following is a categorization attempt for °cCG, °cCD, LatCG, LatCD, PA-CG, PA-CD, in 5 categories. Corresponding numerical data being highly non-normal, an overwhelming majority falls within the "1" category, which has probably no sense.

```
°			Lat			PA-C	
	1			2			1
	1			2			1
1			3			1	
2			1			1	
	1			1			1
	1			1			1
1			1			1	
1			1			1	
	1			1			1
	1			2			1
2			1			1	
						1	
	1			1			1
	2			1			1
1			1			1	
	1			1			1
1			2			1	
	1			1			1
1			1			1	
	1			1			1
1			2			1	
1			2			1	
	1			1			1
1			1			1	
							
	1			1			1
	1			1			1
2			1			1	
1			1			1	
	1			1			1
	1			1			1
2			1			1	
1			1			1	
	1			1			1
	1			1			1
1			1			1	
1			1			1	
	1			1			1
	1			1			1
1			1			1	
	1			1			1
2			1			1	
	1			1			1
1			1			1	
	1			1			1
1			1			1	
1			1			1	
	1			1			
1			1			1	
							
	1			1			1
	1			1			1
1			1			1	
1			1			1	
	1			1			1
	1			1			1
1			1			1	
1			1			1	
	1			1			1
	1			1			1
1			1			1	
						1	
	1			1			1
	1			1			1
1			1				
	1			1			1
1			1			1	
	1			1			1
1			1			1	
	1			1			1
						1	
						1	
	1			1			1
1			1			1	

```

---

### Post by SeijiSensei on 2012-08-09
Perhaps you should look into analysis of variance with paired comparisons.  From a cursory review of your request, that sounds like what you're looking for.  Most any decent textbook on psychological statistics should give you some ideas.

---

### Post by Cubytus on 2012-08-23
Actually, analysis of variance requires to have all-continuous variables. It cannot use discrete variables, can it?

---

