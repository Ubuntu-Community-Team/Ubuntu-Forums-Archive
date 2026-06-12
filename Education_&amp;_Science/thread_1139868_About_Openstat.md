---
title: "About Openstat"
date: 2009-04-27
forum: Education &amp; Science
---

### Post by satimis on 2009-04-27
Hi folks,

Just came across;

Openstat
[http://www.statpages.org/miller/openstat/](http://www.statpages.org/miller/openstat/)

It is for Windows.  I don't have Windows box here only Unix and Linux boxes.  As the author mentioned there that I can run OpenStat on wine.  

However I expect to know whether I need X to run OpenStat?  Because I'm going to test it on a virtual machine.  All the guests are running either on Debian 5.0 (Lenny)-minimal installation OR on Ubuntu 8.04-minimal installation WITHOUT X.  If X is needed then I'll install it before adding OpenStat.  Please advise.  TIA


A further thought, can I run OpenStat remotely on a workstation on LAN via ssh?  If YES then can I left out installing X on the guest where OpenStat is installed.  Thanks


B.R.
satimis

---

### Post by gunksta on 2009-04-28
You will definitely need X. You will also need to install Wine, which has a dependency on the necessary libraries, so you don't need to do a separate installation.

---

### Post by satimis on 2009-04-28
> **gunksta said:**
> You will definitely need X. You will also need to install Wine, which has a dependency on the necessary libraries, so you don't need to do a separate installation.

Noted and thanks


B.R.
satimis

---

### Post by satimis on 2009-08-24
Hi folks,

OpenStat running on wine

Has any folk tried OpenStat;
[http://statpages.org/miller/openstat/](http://statpages.org/miller/openstat/)

I have been searching around to increase the size of its console and bigger font size without result. Advice would be appreciated. TIA


B.R.
satimis

---

### Post by sdbrogan on 2009-08-24
I had a quick look at it; found it gave the wrong answer to some test data :
[http://ubuntuforums.org/showthread.php?p=7195429#post7195429](http://ubuntuforums.org/showthread.php?p=7195429#post7195429)

---

### Post by satimis on 2009-08-24
> **sdbrogan said:**
> I had a quick look at it; found it gave the wrong answer to some test data :
[http://ubuntuforums.org/showthread.php?p=7195429#post7195429](http://ubuntuforums.org/showthread.php?p=7195429#post7195429)
Hi sdbrogan,


Thanks for your advice.  

I just started learning this program.  I can give up and start PSPP or R-project.  OpenStat is running on a guest OS of a KVM virtual machine.  I can install PSPP and R-project on other guest OS.

What will be your comment on PSPP and R-project.  Which of them will be easier to learn.  Statistical computing is new to me.  TIA


B.R.
satimis

---

### Post by sdbrogan on 2009-08-24
PSPP has a simple graphical user interface & will therefore be easier to get started with, it is accurate, & it can also deal easily with huge data sets; on the other hand its functionality is quite limited at the moment.
R is described as a statistically-orientated programming environment - it's more difficult at first.  Not really, really difficult: e.g. to do a t-test you'd type [FONT="Courier New"]t.test(x,y)[/FONT].  You can also install R Commander, a GUI which creates commands when you use buttons, menus, &c., & so is a easier way to learn.  R is extensible through an enormous range of packages, & the chances are you'll find someone's written one for whatever application you might need.  It's good for simulation too, which is fun when you're learning statistics.
If you just need to run a few simple tests occasionally, & they're available on PSPP, then that's the better one for you.  If you want to get into more advanced stuff at some point then start learning R now.
Also there's Gretl, which is billed as being for econometrics & time series, but has a decent range of standard tests; & the spreadsheet Gnumeric, which has some basic but accurate statistical functions (in fact they come from R).

---

### Post by satimis on 2009-08-25
> **sdbrogan said:**
> PSPP has a simple graphical user interface & will therefore be easier to get started with, it is accurate, & it can also deal easily with huge data sets; on the other hand its functionality is quite limited at the moment.
R is described as a statistically-orientated programming environment - it's more difficult at first.  Not really, really difficult: e.g. to do a t-test you'd type [FONT="Courier New"]t.test(x,y)[/FONT].  You can also install R Commander, a GUI which creates commands when you use buttons, menus, &c., & so is a easier way to learn.  R is extensible through an enormous range of packages, & the chances are you'll find someone's written one for whatever application you might need.  It's good for simulation too, which is fun when you're learning statistics.
If you just need to run a few simple tests occasionally, & they're available on PSPP, then that's the better one for you.  If you want to get into more advanced stuff at some point then start learning R now.
Also there's Gretl, which is billed as being for econometrics & time series, but has a decent range of standard tests; & the spreadsheet Gnumeric, which has some basic but accurate statistical functions (in fact they come from R).
Hi sdbrogan,

Thanks for your advice.

I found PSPP on repo

$ apt-cache search pspp```

pspp - Statistical analysis tool
psutils - A collection of PostScript document handling utilities

```

But I can't find R-project

$ apt-cache search R-project```

r-cran-qtl - GNU R package for genetic marker linkage analysis
r-cran-rggobi - GNU R package for the GGobi data visualization system
sgml2x - generic formatter for SGML/XML documents using DSSSL stylesheets
foiltex - a collection of LaTeX files for making foils and slides

```

Any advice.


B.R.
satimis

---

### Post by sdbrogan on 2009-08-25
The package is r-base.  If I remember right that also pulls down r-recommended, which you'll want too.

---

### Post by satimis on 2009-08-25
> **sdbrogan said:**
> The package is r-base.  If I remember right that also pulls down r-recommended, which you'll want too.

Hi sdbrogan,


$ apt-cache search r-base | grep r-base```

courier-base - Courier mail server - base system
dcgui - Direct Connect Graphical client (GTK+) (peer-based file-sharing)
dh-consoledata - debhelper-based script to help packaging console data files
ganeti - Cluster-based virtualization management software
inkscape - vector-based drawing program
liblodo0 - Networked server for robots and sensors - laser-based odometry library
r-base - GNU R statistical computing language and environment
r-base-core - GNU R core of statistical computing language and environment
r-base-core-dbg - GNU R debug symbols for statistical comp. language and environment
r-base-core-ra - 'ra' variant of GNU R core of statistical computing language and environment
r-base-dev - GNU R installation of auxiliary GNU R packages
r-base-html - GNU R html docs for statistical computing system functions
r-base-latex - GNU R LaTeX docs for statistical computing system functions
synfig - vector-based 2D animation renderer
synfigstudio - vector-based 2D animation package (graphical user interface)
vectoroids - vector-based rock-shooting

```

I suppose I need ```

r-base - GNU R statistical computing language and environment
r-base-core - GNU R core of statistical computing language and environment
r-base-core-dbg - GNU R debug symbols for statistical comp. language and environment
r-base-core-ra - 'ra' variant of GNU R core of statistical computing language and environment
r-base-dev - GNU R installation of auxiliary GNU R packages
r-base-html - GNU R html docs for statistical computing system functions
r-base-latex - GNU R LaTeX docs for statistical computing system functions

```

B.R.
satimis

---

### Post by sdbrogan on 2009-08-25
I think r-base is a metapackage, or whatever they call it, that fetches the others

---

### Post by spinoza666 on 2009-08-25
Go to this site for installation instructions:

[http://cran.r-project.org/]("http://cran.r-project.org/")

And if you want a good editor, check out JGR:

[http://jgr.markushelbig.org/JGR.html]("http://jgr.markushelbig.org/JGR.html")

Those sites are good starting points for R, and you should definitely get yourself this manual from the CRAN website:

"An Introduction to R"

When you advance, and have some data to analyze, get yourself "The R Book" by Michael J. Crawley. And you might also consider using Emacs as an editor if you end up using R a lot. If so check this out:

[http://ess.r-project.org/]("http://ess.r-project.org/")

Anyway, R is in my view the best that's out there. If you plan on doing a lot of advanced statistics at least.

---

### Post by satimis on 2009-08-30
> **sdbrogan said:**
> I think r-base is a metapackage, or whatever they call it, that fetches the others
Hi sdbrogan,

Yes, you're right.  "aptitude install r-base" fetched other packages.  R is now running on VM17 (a guest on the KVM box).  Only command input is available without GUI.


B.R.
satimis

---

### Post by satimis on 2009-08-30
Hi spinoza666,

Thanks for your advice.

> **spinoza666 said:**
> Go to this site for installation instructions:

[http://cran.r-project.org/]("http://cran.r-project.org/")

I'm prepared to make another test installing R from the package download on its website on VM18 (a guest on a KVM box) later when I have time.

> 
And if you want a good editor, check out JGR:

[http://jgr.markushelbig.org/JGR.html]("http://jgr.markushelbig.org/JGR.html")

What is the difference btw JGR and Emacs?  I'm running "nano" editor.  Is JGR available on repo?  If YES what is the package name.

Others noted with thanks

B.R.
satimis

---

### Post by spinoza666 on 2009-09-09
Hey sorry for the late reply. 


Emacs is a general purpose editor, that has a 'mode' for R called ESS. You use a lot of Control and Alt shortcuts to do just about anything, and this mode has R related commands that makes scripting R very efficient. It's a bit more time consuming to learn, but when you get the hang of it, it's worth it.

JGR is an editor made for R. Simpler to learn, but does not nearly have the capability of Emacs.

Emacs has modes for LaTex and nearly any programming language known to man, so if you use any of the above a lot, I would go for R, if not use JGR. 

JGR is installed from within R, as is explained on the website I listed.

Okay?

---

### Post by chirag9 on 2011-08-05
hie,
Im using openstat for multiple regression.
I need some help about howmany minimum observations are required to get the analysis window??

---

