---
title: "A New Octave GUI??"
date: 2009-02-12
forum: Education &amp; Science
---

### Post by mattycoze on 2009-02-12
I've been trying to find a good alternative to SPSS (since it's what I use at university but alot of the time I need to do some statistics @ home). As far as I know GNU R and Octave are the best contenders for the sort of statistical analysis I'm trying to do. I've installed the back-ends but I'm really struggling with getting a GUI to work properly with the 3.0.1 version  of Octave on the Ubuntu repository (which is slightly out of date... the current version is 3.0.3). 
I was wondering if anyone could help me by recommending a repository with the most current version of Octave AND a GUI that will work with it :P

Please HELP!

---

### Post by cb951303 on 2009-02-12
I can't help you with that, but have you tried scilab? It has a GUI oob.

---

### Post by gunksta on 2009-02-12
It depends on what you are trying to do.  Octave is usually compared to Matlab, not SPSS.

Disclaimer: I have never used Octave.

Octave does have support for some basic statistical functions. The [Octave Manual]("http://www.network-theory.co.uk/docs/octave3/octave_229.html") has more information. Octave itself does not provide a GUI. It is a command-line program. There is however an interesting project called [QT-Octave]("http://qtoctave.wordpress.com/what-is-qtoctave/") which appears to be an attempt of creating a matlab like interface on top of Octave. If you need to work with numerical analysis only, this could be a good solution for you. Octave 3.0.1 and qtoctave 0.7.4 are both in the Ubuntu repos, making them easy to install.

Unless you are an engineer or are otherwise dealing with matrices only, Octave may be a little limiting, especially when compared to a tool such as SPSS. Fortunately, there are other options! If you search this forum you can find plenty of threads discussing the pros and cons of the software I am about to suggest:

Format: Title,            License,           Notes

[LIST=1]
[*][R]("http://www.r-project.org/"),                OSS,                The 800 pound gorilla of open-source statistics
[*][PSPP]("http://www.gnu.org/software/pspp/"),           OSS,                 Incomplete but excellent clone of SPSS
[*]SPSS,          Proprietary,      Available for Linux too!
[*]SAS,            Proprietary,      The "other"  proprietary stats package.
[*]Stata,          Proprietary,       Ask someone else. I don't know nothing about it.
[/LIST]

I've included links to R and PSPP. You can find the others on your own. R and PSPP are BOTH excellent pieces of software. Without knowing what you want to do, I can't really recommend one over the other. R is probably the most advanced, comprehensive statistics package ever created. It is also probably over-kill for a highschool or under-grad level stats course. PSPP comes with a user friendly GUI, but is not a complete product. SPSS currently provides more functionality than PSPP. 

If you are a student, SPSS will sell you a version of SPSS that runs on Linux for a very "reasonable" price compared to the commercial version. As long as your data sets are fairly small, this will probably get you through a stats class. As an added benefit, the SPSS syntax you learn will work on PSPP, provided the functionality has been implemented in the latter.

I've never used SAS or Stata but I know there are threads here that discuss installing them on Ubuntu. I assume that with effort they can be made to run effectively. People seem to like them, but I don't know much about them one way or the other.

Look this over and tell us what you need to do and how much computer / programming experience you have and I can try to give you a more definite recommendation. You might also consider renaming this thread. There are other people in this forum with experience doing statistical analysis. Getting their input could be beneficial.

---

### Post by ahmatti on 2009-02-18
> **mattycoze said:**
> I've been trying to find a good alternative to SPSS (since it's what I use at university but alot of the time I need to do some statistics @ home). As far as I know GNU R and Octave are the best contenders for the sort of statistical analysis I'm trying to do. 


If you are looking for replacement for SPSS, then R is most likely what you want to use. R has functions for all statistics that you can think of and can handle factors etc. whereas Octave has very limited statistical functionality. 

R has also better plotting features and the learning curve for R and octave is similar, so if you have no experience from either one go with R. 
The reason I can think of using Octave over R is if you are used to MATLAB or do a lot of matrix algebra. 

Some GUI options for R:
RKWard [http://rkward.sourceforge.net/](http://rkward.sourceforge.net/)
RCMDR [http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)

Then there is ESS ([http://ess.r-project.org/](http://ess.r-project.org/)) that lets you run R from Emacs, its really powerful but I don't know if you can really call it a GUI...

---

