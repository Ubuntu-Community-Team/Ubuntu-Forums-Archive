---
title: "SPSS for Linux or other software supporting ANOVA"
date: 2011-10-24
forum: Education &amp; Science
---

### Post by Geebsie on 2011-10-24
Right, so basically my university's got a license for SPSS (SPSS 19), but they either won't upload the Linux version or don't have the license (if it's possible to get the Windows/OS X license without getting the Linux one). I'm about to start running some ANOVAs, and PSPP doesn't support that, which is rather inconvenient for me. I haven't actually tried running it in Wine, but a lot of people are saying that it really doesn't work very well (or at all for that matter). Does anyone know if there's a difference between Windows, OS X and Linux licenses for SPSS, or are the IT guys at my uni just too lazy to upload the Linux version? If there is only a single license, I assume that the activation key will work on a Linux version. So, if yes, how would I go about getting a (free) Linux version of SPSS 19 without the help of my university?

Lastly, I have thought about learning R and tried it briefly, but I've found it generally a bit too awkward and time-consuming, especially when I'm swamped in papers to read/write. So I was wondering if there is any other statistical software that supports basic things like t-tests, non-parametric stats, correlation coefficients and ANOVAs.

Any help would be much appreciated!

---

### Post by nickleboyblue on 2011-10-24
I installed SPSS in Ubuntu using wine, but it didn't work all the way...  It is possible to get it up, running, and working under wine, but some people have issues with it while others do not.  See [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=23401&iTestingId=63381") for notes on how one person got it working under wine.

To see how to install the linux version, look [here]("http://users.ox.ac.uk/~richardc/guides/SPSSforLinux.html").

Essentially, SPSS is not particularly Linux-friendly, so I wouldn't expect much.  I actually installed Windows 7 so I could access it, but have since removed it.  If ever I need to run statistical analysis, I use R or PSPP, but usually R has all the facilities I need to run whatever tests I need to run.

Just FYI, a lot of the statistical tests you run in SPSS are actually subsets of the same test.  It takes a solid understanding of what test is really just a pseudonym for another test in order to effectively run statistical analysis using R.  R is it's own programming language and requires a lot of technical savvy, but it is definitely worth the effort because you will be able to use it inside of PHP or Python as well.

---

### Post by SeijiSensei on 2011-10-24
Our friends at the GNU organization have sponsored an open-source (GPL) version of SPSS called [PSPP]("http://www.gnu.org/software/pspp/").  I used it recently when I needed to run some crosstabs and regressions on survey data for the first time in years.  I certainly wasn't about to buy an SPSS license for the purpose, but a visit to Wikipedia's [page]("http://en.wikipedia.org/wiki/List_of_statistical_packages") on statistical software took me to PSPP.

I'll also mention another excellent piece of open-source statistical software, GNU's [gretl]("http://www.gnu.org/software/gretl/").  It covers the waterfront when it comes to estimation using linear and nonlinear techniques.

Both PSPP and gretl are available in the Ubuntu repositories.

---

### Post by gunksta on 2011-10-24
I'm fairly certain that PSPP does offer one-way ANOVA and recent versions of SPSS are very easy to install and use on Linux. I have SPSS, PSPP, R and a few other things installed on this system. PSPP is easier than SPSS to install since it is in the repos, but SPSS isn't exactly hard. Here's a basic outline.

1 - Go to IBM's website and download the installer for the SPSS trial (linux version). Download and install. You'll need to drop down to the command line and run the installer as root. Once you start the installation, its graphical and easy. SPSS is a java application but you don't necessarily need java pre-installed. As part of its ridiculously large download, SPSS comes with its own java.

2 - AFAIK, an SPSS license is an SPSS license. You don't need a separate license per OS. You can only use one copy of SPSS at a time, but they don't give a darn which OS yo use. I'm the only linux user in my office and I use it more or less surreptitiously. I can't just stand to use Windows.

3. Use your school's license to turn the trial version in to a full-fledged or student version or whatever your license is good for.

There are lots of ways to slice and dice data. R is fantastic, but there is a learning curve. Depending on what you are trying to do, spreadsheets are not necessarily a bad thing. SPSS / PSPP are yet another option(s).

Let me know if you run into any problems installing SPSS.

---

### Post by earlycj5 on 2011-10-24
There's another option as well.

SOFA, [http://www.sofastatistics.com/wiki/doku.php?id=help:anova](http://www.sofastatistics.com/wiki/doku.php?id=help:anova)

---

### Post by gunksta on 2011-10-25
I completely forgot to mention SOFA. It is young but it is, in many ways, a better SPSS. Both SPSS and PSPP use "SPSS syntax" which many people think is a pretty horrible language. (Yes, I am one of these people.)

SOFA is built on python. I haven't looked at the code, so I don't know how the author is doing things internally, but it has to be easier to program against than SPSS. And, if you use the GUI, it actively tries to help you use the correct test. SPSS is powerful but for the uninitiated / sloppy it is also really easy to point and click your way into a nonsense analysis. 

If you really fall in love with python, I have been watching a thing called [PANDAS]("http://pandas.sourceforge.net/") which looks pretty cool. It is a pythonic spin on R's data.frames.

Lots of options. . . .

---

### Post by rewyllys on 2011-10-25
> **Geebsie said:**
> . . . . Lastly, I have thought about learning R and tried it briefly, but I've found it generally a bit too awkward and time-consuming, especially when I'm swamped in papers to read/write. . . .
As an aid to learning R, I've found Rob Kabacoff's *R in Action* very helpful.  Here's a URL about it:
[http://www.manning.com/kabacoff/](http://www.manning.com/kabacoff/)

---

### Post by Geebsie on 2011-10-26
Thank you all very much. As I mentioned in my OP, PSPP doesn't support two-way ANOVAS, which I'll need, so PSPP isn't really an option.

I've whined to the IT department requesting SPSS (again), but I might have a look at SOFA. I'll definitely have a look at R, as well. Knowing R seems worth it just for the e-peen factor, but it probably looks good on a CV as well, so it's definitely appealing (this in addition to obvious pragmatic reasons :p). 

Again, thanks a lot for your replies; really appreciate all your effort!

---

### Post by gunksta on 2011-10-26
Good luck. I think you should download the trial version of SPSS and then use your university's license to keep it beyond the initial trial period. I agree, you should definitely learn R as well. Don't know what you are studying but in some areas of study R has become the standard. In others, SPSS still rules supreme. If you learn both now, you will be better prepared for the future.

---

### Post by SeijiSensei on 2011-10-26
> **Geebsie said:**
> Thank you all very much. As I mentioned in my OP, PSPP doesn't support two-way ANOVAS, which I'll need, so PSPP isn't really an option.

Regression with zero/one dummy variables for the treatments and their interactions is mathematically equivalent to ANOVA.  You can test changes in explained variance by adding the items stepwise and calculating the appropriate F-tests.  The dummy coefficients themselves measure the effects.

---

### Post by jkpeck on 2011-10-26
For Python lovers, SPSS Statistics has an extensive Python interface that you can program against, although you still have to issue standard Statistics commands to run procedures.  You can find out about this here ([www.ibm.com/developerworks/spssdevcentral](www.ibm.com/developerworks/spssdevcentral)).

As for two-way ANOVA, it is mathematically equivalent to linear regression with dummy variables, but hypothesis testing is much more conveniently done with the ANOVA-related procedures for factor or use the GLM procedure, which understands factors.

---

### Post by beew on 2011-10-26
> **SeijiSensei said:**
> Regression with zero/one dummy variables for the treatments and their interactions is mathematically equivalent to ANOVA.  You can test changes in explained variance by adding the items stepwise and calculating the appropriate F-tests.  The dummy coefficients themselves measure the effects.

PSPP doesn't do logistic regression either. If it did it would be making a huge inroad as this is the only thing that many social science researchers ever use!

Opps, sorry misread your post, yes you are right, the independent variables are 0/1 dummy variables.

---

### Post by Migure on 2011-10-27
> **Geebsie said:**
> Thank you all very much. As I mentioned in my OP, PSPP doesn't support two-way ANOVAS, which I'll need, so PSPP isn't really an option.

I've whined to the IT department requesting SPSS (again), but I might have a look at SOFA. I'll definitely have a look at R, as well. Knowing R seems worth it just for the e-peen factor, but it probably looks good on a CV as well, so it's definitely appealing (this in addition to obvious pragmatic reasons :p). 

Again, thanks a lot for your replies; really appreciate all your effort!
Just for information:  In the latest PSPP (you will need to download a very recent version) two-way ANOVA is implemented.  You can find it in the GLM command.

The PSPP/SPSS language is indeed horrible.  That is why PSPP has a GUI.   GUIs are also horrible - all of them.  PSPP exists in order to provide rehabiliation for people who have are addicted to SPSS.  If you have no such addiction, then R is a better choice, unless you are dealing with datasets which run into tens of millions of observations in which case R will not cope, but PSPP will.

Whatever you do, I would recommend avoiding SPSS.  With that, you will get the worst of both worlds, AND you will have to prostitute yourself to the proprietary software underworld.

Also, please don't get confused between "implemented" and "supported".  Nothing is "supported" in any software unless you have an explicit support contract.

---

### Post by Migure on 2011-10-27
> **beew said:**
> PSPP doesn't do logistic regression either. If it did it would be making a huge inroad as this is the only thing that many social science researchers ever use!

Indeed PSPP doesn't have logistic regression right now.  The good thing about free software, such as PSPP, is that if it lacks something that you want, you have the means and permission to fix it.

If logistic regression is important to you, why not implement it yourself and send a patch to the developers for inclusion in the next release?    I'm sure they'd welcome your contribution.

---

### Post by SeijiSensei on 2011-10-27
> **Migure said:**
> If logistic regression is important to you, why not implement it yourself and send a patch to the developers for inclusion in the next release?    I'm sure they'd welcome your contribution.

Don't bother; just use [gretl]("http://www.gnu.org/software/gretl/").  It does dichotomous and ordered probit and logit and many other nonlinear maximum-likelihood techniques as well.

---

### Post by bryncoles on 2011-10-27
Install R, and then ```
install.package(Rcmdr,dep=T)
```

Then, launch R commander with the command ```
library(Rcmdr)
```  That'll give you a servicable GUI to use in R, which should make things easier if you're following this route.

---

### Post by beew on 2011-10-27
> **Migure said:**
> Indeed PSPP doesn't have logistic regression right now.  The good thing about free software, such as PSPP, is that if it lacks something that you want, you have the means and permission to fix it.

If logistic regression is important to you, why not implement it yourself and send a patch to the developers for inclusion in the next release?    I'm sure they'd welcome your contribution.

I don't use SPSS or PSPP, I use R and Stata on Linux.  

I am just saying that PSPP will be able really give SPSS a run of its money if it has logistic regression since many social scientists type use only logistic regression and hardly anything else and these are the primary users of SPSS (as the name of the Software implies). And why do you assume that all users who want it would be able to create it? Most users of SPSS are not programers.

BTW, it is not so simple to make a logistic regression module for pspp, it has been on their to do list for years, if it is simple it would have been done. I think the issue is not just that they have to implement the said module, but have to do it in such a way that the output would be exactly like SPSS, that is the hard part. Otherwise all standard stat packages can handle that.  I am actually having s lot of doubts about the value of PSPP, wasting all that resources to reverse engineer SPSS  while they can be  put to better use, and even in the best case scenario it would still inevitably be years behind.

---

### Post by Kehribar on 2012-08-15
Hi Everyone,

I just wanted to point out to fellow Ubuntu users and those interested in SPSS in the linux environment that SPSS 17 works fine within Virtual Box installed on Ubuntu 11.04.

It's a bit slowish, but it gets the job done.

Previously I had tried it in Wine but that had problems.

E. Z.

---

### Post by kimberlite on 2012-08-15
> **Geebsie said:**
> 
Lastly, I have thought about learning R and tried it briefly, but I've found it generally a bit too awkward and time-consuming, especially when I'm swamped in papers to read/write. 

If you or someone else is going to learn R, [RStudio]("http://rstudio.org/") may help you out in the very first steps. It is not a GUI like RCommander, but an integrated development environment (IDE) for R.

---

### Post by PGScooter on 2012-08-15
> **kimberlite said:**
> If you or someone else is going to learn R, [RStudio]("http://rstudio.org/") may help you out in the very first steps. It is not a GUI like RCommander, but an integrated development environment (IDE) for R.

+1

And I think it will help you after your very first steps also. Many experienced R users use it.

---

### Post by gunksta on 2012-08-21
> **Kehribar said:**
> Hi Everyone,

I just wanted to point out to fellow Ubuntu users and those interested in SPSS in the linux environment that SPSS 17 works fine within Virtual Box installed on Ubuntu 11.04.

It's a bit slowish, but it gets the job done.

Previously I had tried it in Wine but that had problems.

E. Z.

Generally - It is better to start a new thread, rather than using a long-dead thread from late 2011.

In other news - modern versions of SPSS run just fine on Linux thanks to Java. You don't need Wine or Virtualbox. Even better, the license keys are interchangeable. My employer purchased SPSS for me. I didn't ask them to buy a Linux specific key but when I went to install, I tried it on my Linux machine first. I downloaded the evaluation version, to make sure it worked as expected on Linux and then entered the license key so I could keep it.

Wine / Virtualbox are great for programs / services that can't be accessed any other way, but there's no reason to do that with SPSS.

Note - New versions of SPSS are actually called PASW thanks to IBM.

---

### Post by kimberlite on 2012-08-24
> **gunksta said:**
> 
Note - New versions of SPSS are actually called PASW thanks to IBM.
It is "[IBM SPSS Statistics]("http://www-01.ibm.com/software/analytics/spss/downloads.html")" again ...

---

