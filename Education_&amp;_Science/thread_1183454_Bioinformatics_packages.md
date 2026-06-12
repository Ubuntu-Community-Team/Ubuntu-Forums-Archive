---
title: "Bioinformatics packages"
date: 2009-06-10
forum: Education &amp; Science
---

### Post by spinoza666 on 2009-06-10
Hey all,

I'm looking for a linux package that will enable me to analyze microsattelite data. Basically, I'm trying to calculate heterozygosity and allele diversity from DNA. I want to stay away from GeneMapper, and use some open-source or free software instead.

Any ideas?

---

### Post by nateperson on 2009-06-10
I ran across this paper a bit ago... 
> P.C. Sharma, A. Grover and G. Kahl, Mining microsatellites in eukaryotic genomes, Trends Biotechnol. 25 (2007), pp. 490–498
It lists a good 20 diffrent programs...  Didn't try any of the programs it talks about, and don't know if they will work for you, but it mentions linux as a "limitation" when talking about some of the different programs.

I'm sure one of them would have an install package.

---

### Post by wirporte on 2009-06-10
You might try Try Bio-linux 

[http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0](http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0)

Ubuntu based distro with pre-installed biology programs.  I've never used it, but this looks like it may be close to what you are looking for.

---

### Post by machoo02 on 2009-06-10
[Genepop on the web]("http://genepop.curtin.edu.au/") is one option, or [the command line version of Genepop]("http://kimura.univ-montp2.fr/~rousset/Genepop.htm") would also work nicely for calculating some basic population genetic info from microsats.  I'm fairly certain that there are some R packages to do what you want, and also check out [Bioconductor]("http://www.bioconductor.org/")

---

### Post by spinoza666 on 2009-06-10
> **nateperson said:**
> I ran across this paper a bit ago... 

It lists a good 20 diffrent programs...  Didn't try any of the programs it talks about, and don't know if they will work for you, but it mentions linux as a "limitation" when talking about some of the different programs.

I'm sure one of them would have an install package.

Thanx! I'll have a look at it when I get to uni tomorrow. Regretfully, no access from home.

---

### Post by spinoza666 on 2009-06-10
> **wirporte said:**
> You might try Try Bio-linux 

[http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0](http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0)

Ubuntu based distro with pre-installed biology programs.  I've never used it, but this looks like it may be close to what you are looking for.

Thank you. I've already looked into this possibility, and found that scientific distributions in general do not fit my needs. They contain way too many packages that I don't need, and a lot of the packages don't work out-of-the-box. The same packages often work better when just installing them into a vanilla linux distribution, and then I also have more control. But thanks for the tip:)

---

### Post by spinoza666 on 2009-06-10
> **machoo02 said:**
> [Genepop on the web]("http://genepop.curtin.edu.au/") is one option, or [the command line version of Genepop]("http://kimura.univ-montp2.fr/~rousset/Genepop.htm") would also work nicely for calculating some basic population genetic info from microsats.  I'm fairly certain that there are some R packages to do what you want, and also check out [Bioconductor]("http://www.bioconductor.org/")

I didn't even know Genepop was free software, but it will definitely do a lot of the stuff I need to do. R is my favorite thing in the world (next to beer perhaps), and will be doing most of stats in it, but does R really have packages that can fill in for GeneMapper? Like, show peaks for individual markers, and so on? 

Bioconductor looks interesting:)

Thanx a bunch for the tips:)

---

### Post by machoo02 on 2009-06-10
You're not going to find any free software that will run/control/basically do anything with ABI genetic analyzers.  You're stuck with GeneMapper and the rest of the ABI data collection software for talking to the maching, calling peaks, etc.  

OTOH, GeneMapper does not do any of the population level calculations that you are interested in.  It's not designed to do that...but my other suggestions are.

And for more genetics in R goodness...go [here]("http://cran.r-project.org/web/views/Genetics.html").

---

### Post by spinoza666 on 2009-06-11
> **machoo02 said:**
> You're not going to find any free software that will run/control/basically do anything with ABI genetic analyzers.  You're stuck with GeneMapper and the rest of the ABI data collection software for talking to the maching, calling peaks, etc.  

OTOH, GeneMapper does not do any of the population level calculations that you are interested in.  It's not designed to do that...but my other suggestions are.

And for more genetics in R goodness...go [here]("http://cran.r-project.org/web/views/Genetics.html").

Wow! Very good advice. I'm just learning to do microsatellite analysis for my thesis, so was a bit confused with what software exactly does what, but you just cleared everything up:)

Thanks for the advice, and your link is just what I was looking for:)

---

### Post by machoo02 on 2009-06-11
Not a problem....one of the chapters of my dissertation (which I'm trying to finish now) contains a bunch of microsatellite analyses, so it's all fresh in my mind.

Good luck with your thesis!

---

