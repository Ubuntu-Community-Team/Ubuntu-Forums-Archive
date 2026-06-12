---
title: "Population genetics software for time series"
date: 2010-09-17
forum: Education &amp; Science
---

### Post by spinoza666 on 2010-09-17
Hi all,

I'm having some trouble finding software for analysing microsatellite time-series data. My data set basically consists of samples taken from about 20 different islands each third year, and I'm interested in the genetic structure through time, not just year by year.

Does anyone of the esteemed ubuntu community have any good ideas? R package or otherwise?

-Atle

---

### Post by memilanuk on 2010-09-17
I'm not familiar with that kind of work, but I've seen all kinds of stuff on time-series analysis mentioned for R... might try searching their mailing list via the archives @ Gmane.org, or searching their website (might turn up in an archived copy of the R Newsletter/Journal).

HTH,

Monte

---

### Post by spinoza666 on 2010-09-18
Thanx:)

I've already tried the archives, and found a whole heap on time series, but nothing really stellar with regards to genetic structure. It seems there is a need for good software of this kind, or I've just not stumbled upon it yet.

---

### Post by tymek666 on 2010-09-18
What about STRUCTURE and BAPS? I used then to estimate presence of genetic structure.

---

### Post by spinoza666 on 2010-09-18
Hmmm I'm aware of Structure and BAPS, but do they take the spatial and temporal autocorrelation into account?

The problem is this: I have sampled several populations through several years, but there is a lack of independence due to proximity in space, migration between populations, that individuals from one generation survive into the next etc etc. What I'm looking for is a statistical method that takes this dependence among generations and populations into account, and enables me to say something about how these populations and generations affect each other through time. Eg how the genetic composition of one population affects the genetic composition of another population three years later. 

I could of course do traditional time series analysis, and for instance look at lag, but I am looking for a more tailored approach that would give me a bit more detail?

---

### Post by memilanuk on 2010-09-18
I presume you've checked with the folks in the Bioconductor project already?

---

### Post by tymek666 on 2010-09-19
I think BAPS can do spatial autocorelation, but probably not temporal. I'm rather familiar with population genetics software, but can't remind any program with temporal analysis. In phylogeography studies we use BEAST, but it's a different story.

---

### Post by spinoza666 on 2010-09-19
No, memilanuk, not checked with Bioconductor, so that might be a good idea.

And, yes, tymek666, I think you're right. I have been looking for software with the ability to do temporal analysis for quite some time now, and come up short. These forums were kinda my last resort. I guess I'll have to do regular mixed-effects or time-series modelling. But I wasn't aware that BAPS could take spatial autocorrelation into account, so I'll look into that for sure. 

Cheers

---

