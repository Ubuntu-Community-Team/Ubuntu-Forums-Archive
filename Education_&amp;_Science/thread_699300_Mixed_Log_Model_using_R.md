---
title: "Mixed Log Model using R"
date: 2008-02-17
forum: Education &amp; Science
---

### Post by carpoll on 2008-02-17
Hi All,

I am trying to run a Mixed Log Analysis on the occurrence of an epenthetic vowel (The dependent variable is categorical (Occur)). The independent variables are all categorical and it looks something like this:

Subj  Item  Occur  Placeartic  Stress Voicing	Vowel	Order	Mannerartic	Homorg
s1	14	0	3	2	1	1	2	1	0
s2	14	1	3	2	1	1	2	1	0
s3	14	0	3	2	1	1	2	1	0
s4	14	1	3	2	1	1	1	1	0


The coding model I am using is 
mlmcr <-lmer(Occur ~ (1 | Subject) + (1 | Item) * Placeart * Voicing * Stress * Vowel * Order * Mannerartic * Homorg, data = numcr)

I get an error message saying that 

“Error in lmer(Occur ~ (1 | Subject) + (1 | Item) * Placeart *  : 
  Leading minor of order 11 in downdated X'X is not positive definite”

Does anyone know what exactly the error message refers to?
Are the variables ‘Item’ and ‘Subject’ coded as ‘factors’
Thanks for your time. I’d appreciate help.

Sincerely,

Carlos

---

### Post by euler_fan on 2008-02-17
> **carpoll said:**
> Hi All,

I am trying to run a Mixed Log Analysis on the occurrence of an epenthetic vowel (The dependent variable is categorical (Occur)). The independent variables are all categorical and it looks something like this:

Subj  Item  Occur  Placeartic  Stress Voicing	Vowel	Order	Mannerartic	Homorg
s1	14	0	3	2	1	1	2	1	0
s2	14	1	3	2	1	1	2	1	0
s3	14	0	3	2	1	1	2	1	0
s4	14	1	3	2	1	1	1	1	0


The coding model I am using is 
mlmcr <-lmer(Occur ~ (1 | Subject) + (1 | Item) * Placeart * Voicing * Stress * Vowel * Order * Mannerartic * Homorg, data = numcr)

I get an error message saying that 

“Error in lmer(Occur ~ (1 | Subject) + (1 | Item) * Placeart *  : 
  Leading minor of order 11 in downdated X'X is not positive definite”

Does anyone know what exactly the error message refers to?
Are the variables ‘Item’ and ‘Subject’ coded as ‘factors’
Thanks for your time. I’d appreciate help.

Sincerely,

Carlos

I hate to make this suggestion, but you might be better off posting this to the R Help mailing list or the SIG for mixed models.

You said all your variables are categorical, so all of them should be coded as factors, otherwise (if memory serves) R will treat them as continuous and this is incorrect.

If I had to guess I would say it has to do with degeneracy in one (or more) of your variables. When it refers to X'X not being positive definite it's referring to the mathematical structure of the X'X matrix. So I would find a reference which talks about the conditions you need to satisfy for your model to be valid and start checking them.

If [this paper]("http://www.stern.nyu.edu/~wgreene/MixedLogitSOP.pdf") is discussing what you are working with it might provide a starting point.

Good luck.

---

### Post by carpoll on 2008-02-17
Thanks a lot.
I included the variables one by one until i discovered with ones were not positive definites.
The only problem remaining is that R is not reading the Item variable properly it computes all the items as it were only 1 item.

Thanks so much for your help.

Carlos

---

