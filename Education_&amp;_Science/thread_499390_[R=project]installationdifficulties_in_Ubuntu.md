---
title: "[R=project]installationdifficulties in Ubuntu"
date: 2007-07-12
forum: Education &amp; Science
---

### Post by Schoappied on 2007-07-12
Hey,

I try to install R-project, a statistical program. But I have need some help for the installation:

This is the installwiki for Debian [http://wiki.r-project.org/rwiki/doku.php?id=getting-started:installation:debian]("http://wiki.r-project.org/rwiki/doku.php?id=getting-started:installation:debian")

The 'aptitude' commands are fine, but the problems start with this:

[quote=wiki]

install.packages()

 For all other packages that are not provided as Debian packages, you can normally use install.packages() as it is described elsewhere. By default these packages are not installed in the same place as Debian packages, but are still installed in system-wide directory, where you need appropriate privileges. If you do not have these privileges, you can specify different location, say in your home, via lib argument. 

install.packages("abind", lib = "~/R/library")[/quote]

I do not know these commands. How can I run them on Ubuntu?

I hope you can help me :confused: :) !

---

### Post by Voynix on 2007-07-12
Hi,

You can install the packages in many different ways (manually, the R-terminal or synaptic). 
[LIST=1]
[*]Launch R as a normal user by typing in the terminal: ```
R
``` or as admin ```
sudo R
```. As a normal user the packages will be installed in a local folder in your home directory. It is a safe (and probably) good option.
[*]Type in the R terminal the following: ```
 install.packages()

``` Select the mirror and then choose the libraries to install.[/LIST]You can also have a look at the packages on the repos (look for libraries in synaptic beginning with "r-cran") and install as normal. 

You should give[ R Commander]("http://www.google.co.uk/search?hl=en&q=how+to+launch+R&btnG=Search&meta=") a try. It is in the repos and will provide you with a nice gui to work with R commands. 

Voynix

---

### Post by euler_fan on 2007-07-12
I've never had any luck getting R to install anything without being run under sudo. Then again, i also like letting R handle its own packages and not worrying about where to put them all.

If you need to install from source tar.gz's the man page for install.packages() has all the necessary information. Just make sure to tell it to not go look on line, especially if you are installing something not in the native R repos.

---

### Post by Schoappied on 2007-07-13
I did the aptitude commands..

aptitude install r-base-core
aptitude install r-base-html r-doc-pdf
aptitude install r-cran-abind

I add this line to my sourcelist... 
deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) feisty/

with this mirror:
[http://cran-mirror.cs.uu.nl/](http://cran-mirror.cs.uu.nl/)

Installed all the r-cran packages in my synaptic...

But I get this:
irk@dirk-desktop:~$ R

R version 2.5.1 (2007-06-27)
Copyright (C) 2007 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

Or is this the beginning of the program?
:confused:

---

### Post by akniss on 2007-07-13
That is indeed the beginning of the program.  R is completely command line driven, and does not come with a point and click interface.  Several add-on packages have been developed in order to put a GUI on top of R... RKward and JGR are the two that seem to show the most promise.
```
a<-"Hello R!"
print(a)
```

---

### Post by Schoappied on 2007-07-13
> **akniss said:**
> That is indeed the beginning of the program.  R is completely command line driven, and does not come with a point and click interface.  Several add-on packages have been developed in order to put a GUI on top of R... RKward and JGR are the two that seem to show the most promise.
```
a<-"Hello R!"
print(a)
```

Ok, thanks for your reply! :)
But what you're mean with that code and how I have to use it... not very clear for a starter....

---

### Post by vanadium on 2007-07-13
R indeed is a command line program that lives in your console after you typed R at the bash prompt. Nevertheless, it will pop up nice publication quality graphics on your desktop if you ask it to. On the R-cran website, you will find links to various third party documentation, including very nice, less than 100 pages introductory documents. You should pick at least one of these and study it carefully. Then it will all get clear. The initial effort if having to start of with commands and syntax will pay of with much more power and more speedy less error prone work from your part.

---

### Post by Schoappied on 2007-07-13
> **vanadium said:**
> R indeed is a command line program that lives in your console after you typed R at the bash prompt. Nevertheless, it will pop up nice publication quality graphics on your desktop if you ask it to. On the R-cran website, you will find links to various third party documentation, including very nice, less than 100 pages introductory documents. You should pick at least one of these and study it carefully. Then it will all get clear. The initial effort if having to start of with commands and syntax will pay of with much more power and more speedy less error prone work from your part.

Why should I use R instead of SPSS... ?
What makes R better?

---

### Post by akniss on 2007-07-13
> **Schoappied said:**
> Why should I use R instead of SPSS... ?
What makes R better?

Honestly, if SPSS does everything you need, and you know how to use it, and you don't mind paying for it, and you are happy with Windows, there is absolutely no compelling reason to use R instead.  We certainly can't help you much in making this decision.  You have to use what works best for you given your own needs and preferences.  

*My own personal experience:* I started doing statistics with SAS, which also is very much driven by scripting rather than point-and-click.  The major weakness of SAS is graphing/plotting results.  I started using R so that I could use a single program for data analysis and graphics.  If it were not for the graphics capabilities of R, I would have had no real reason to switch, since SAS makes a linux version, and I am at a university that provides a license for the program.  However, after making the switch, here are my thoughts about R:
[LIST]
[*]Free - I can install it on my work computer and personal computers at no charge
[*]Powerful - both for data analysis and publication quality figures
[*]Respected - you will not find another statistical program held in such high regard among statisticians
[*]Difficult learning curve - takes a massive investment of time on the front end to learn how to use, but is well worth it for someone doing many types of data analysis for publication
[/LIST]

---

### Post by euler_fan on 2007-07-13
> **Schoappied said:**
> Why should I use R instead of SPSS... ?
What makes R better?

My $0.02 . . . 

I've used SAS, R, and Minitab (not SPSS, admittedly . . . ), and in my experience the thing to do is identify what you need your system to do and then go find a piece of software that can do those things and put in whatever effort it takes to learn it.

If you want point and click, then SAS/INSIGHT or Minitab or SPSS makes sense. Even some of the gui front ends for R can do a certain amount of the basics any more and grow more capable with each release.

If you or some critical audience (like a thesis advisor or the management) doesn't trust a non-commercial solution, R might not be for you.

But, if like me, you are starting to find out that you want/need a custom solution (for instance, MCMC from a truncated distribution with a nasty geometry), well, then I'm afraid that you're well outside the realm of what at least Minitab or to my knowledge most (all?) gui front ends are designed to handle. Which is not to say the software could not hypothetically be made to do it, just that you'll have to get into scripting/macros which is where SAS, R, FORTRAN, etc, come into the picture.

A similar argument works for repeated analyses. If I had to do the same analysis 100 times per day on 100 datasets, I'd be writing a Perl script to implement an R script or using Python . . . anything so that I could feed in data in the right format and go do something else. Why do yourself 100 times what you can automate once? If SPSS has that kind of capability and can do it in an intelligent way, fine. But from personal experience, R and its attendant add-on packages give you some amazing capabilities in this regard. Plus, code reuse is a beautiful thing :)

---

### Post by Schoappied on 2007-07-14
Thanks for the advise guys!
I think I'm keep using SPSS (in November there will come a linux version I heard)..
But I've installed R now and hope I wil learn it in the coming two years....
My first aim is to learn to work with LaTeX.....

Thanks again!

---

