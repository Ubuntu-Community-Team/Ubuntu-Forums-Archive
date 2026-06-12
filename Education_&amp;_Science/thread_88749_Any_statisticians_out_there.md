---
title: "Any statisticians out there?"
date: 2005-11-11
forum: Education &amp; Science
---

### Post by akniss on 2005-11-11
I'm pretty new to ubuntu (and Linux).  I have been using the statistical program R for some time now, and in fact it is the program that really got me interested in open source and prompted my switch away from windows.  my question is this... 
Are there any ubuntu users who know of a good R code editor?  I really liked Tinn-R for windows, but it doesn't look like there is a Linux version of this program.  I've recently tried Rcmdr, and wasn't too impressed.  I would also be interested if someone has had experience using Tinn-R under linux with WINE or other similar workarounds.  Any help would be greatly appreciated.

to head off the inevitable question, I've already searched google and the R-help lists, and no really exciting finds.  (that's where I first heard of Rcommander)

---

### Post by david_finlayson on 2005-11-11
Emacs has one of the best R environments available:

[http://ess.r-project.org/](http://ess.r-project.org/)

You're going to hate it for at least a month...something happens after a few weeks though. Your fingers "memorize" the keystrokes. You won't be able to type without emacs after that.

David

---

### Post by akniss on 2006-02-08
So after much searching, I've found that Kate text editor has a great environment for using R.  It has some basic R Script highlighting, and you can invoke a terminal window from within Kate.  Also, it has a 'Project' sidebar that I use to save data text files, spreadsheets, and related .R files.  It works bettern than anything I've found in Windows or Ubuntu.  Thought I'd post this in case it helps anyone else.  

I did give ESS in emacs a go for a while, but never really got hooked.  Someone who is already reasonably proficient in emacs would probably love it, but its a little too un-intuitive for me personally.

---

### Post by towsonu2003 on 2006-02-08
[QUOTE=akniss]I'm pretty new to ubuntu (and Linux).  I have been using the statistical program R for some time now[/QUOTE]
sorry to post kinda off topic but, do you know of a nice newbie friendly R howto / tutorial that will get me started from the beginning? And, (being a foreigner to R), does it have a gui frontend-kinda window (like in spss)? 

I am very, very very sick of spss and its stupid "your license does not include the help section, so screw you"-like messages. Especially bc. this error comes up in my department's computer grrr 
-thanks in advance :)

---

### Post by david_finlayson on 2006-02-08
R is pretty close to S/S-plus. Your math library no doubt has several books on S (that's where I picked them up). For the most part they apply to R.  I've noticed that newer editions often include R directly. There is also a nice tutorial included with the html documentation.

(use synaptic to instal r-doc-html first)

from R:

> help.start()

Click "An introduction to R."

---

### Post by akniss on 2006-02-08
[QUOTE=towsonu2003]sorry to post kinda off topic but, do you know of a nice newbie friendly R howto / tutorial that will get me started from the beginning? And, (being a foreigner to R), does it have a gui frontend-kinda window (like in spss)? 

I am very, very very sick of spss and its stupid "your license does not include the help section, so screw you"-like messages. Especially bc. this error comes up in my department's computer grrr 
-thanks in advance :)[/QUOTE]

The R project website has links to lots of good references.  If you go to:
[http://www.r-project.org/](http://www.r-project.org/)
there will be links under Documentation in the left pane.  Lots of good stuff there.  The best for beginners found by following the  Manuals  link and then An Introduction to R.  It is available as HTML, PDF, or in print, if you desire.  If you really want to get the meat of how to use R, the best book is Modern Applied Statistics with S (often referred to as MASS).  It can be found here:
[http://www.stats.ox.ac.uk/pub/MASS4/](http://www.stats.ox.ac.uk/pub/MASS4/)

Two other books that I have found very useful:
[http://staff.pubhealth.ku.dk/~pd/ISwR.html](http://staff.pubhealth.ku.dk/~pd/ISwR.html)
[http://cm.bell-labs.com/cm/ms/departments/sia/NLME/MEMSS/](http://cm.bell-labs.com/cm/ms/departments/sia/NLME/MEMSS/)

But without a doubt, the only way to learn R, S, SAS, SPSS, Minitab, etc is by doing.  Install it and try it out.  Work through the simple examples in the Introduction to R from the R site.  Play with it, yell at it, and give up a few times.  Eventually you'll find that you are so much more efficient than you were with SPSS that it will have been worth all the pulling out of hair and gnashing of teeth.
Good luck!

---

### Post by towsonu2003 on 2006-02-08
thanks so much! very helpful links, especially the books. I love it when the book is downloadable (not in these cases though). I should do the same with my soon-to-be (boring) thesis.

---

### Post by wouterommeslag on 2006-03-15
Hello,

I'm a economics student at EHSAL, Brussels. For a paper I need a user-friendly statistics tool. I understand that R is a command-line program, for me that's not quite an option. I can't invest very precious time in learning how to use the software. I have to hand in the complete paper in a few weeks.

 I would like an SPSS / Excel like look. 

What do I need?

Several distributions like Normal, Binomial, Poisson, T-distribution etc
Some intervals (Z-insterval and T-interval)
Tests (One way ANOVA, Z-test, Smirnov,.. )

Help is very much appreciated! 

For further details, you can mail me: [email]wouter.ommeslag@student.ehsal.be[/email]

Thanks a lot,
Wouter

---

### Post by towsonu2003 on 2006-03-15
[QUOTE=wouterommeslag]Hello,

I'm a economics student at EHSAL, Brussels. For a paper I need a user-friendly statistics tool. I understand that R is a command-line program, for me that's not quite an option. I can't invest very precious time in learning how to use the software. I have to hand in the complete paper in a few weeks.

 I would like an SPSS / Excel like look. 

What do I need?

Several distributions like Normal, Binomial, Poisson, T-distribution etc
Some intervals (Z-insterval and T-interval)
Tests (One way ANOVA, Z-test, Smirnov,.. )

Help is very much appreciated! 

For further details, you can mail me: [email]wouter.ommeslag@student.ehsal.be[/email]

Thanks a lot,
Wouter[/QUOTE]
You could try out R with tk interface for starters. I think you run R, then type library(Rcmdr) and play around with the window it throws you in... The developers of R are old-fashioned unix geeks who are not very friendly to gui improvements imo. R itself, on the other hand, looks like much more powerful than SPSS. Well, I can't use R nevertheless, without better gui. Your choice. 

You could also try how gnome's spreadsheet program (forgot its name, part of gnome office) and openoffice calc (along with 000-stats package -just google it) will meet your needs. 

I could not find a statistics program to my needs and hence running SPSS under qemu (check out the forum for qemu howtos). it's slow, but it runs ok.

---

### Post by akniss on 2006-03-15
[QUOTE=wouterommeslag]Hello,

 I would like an SPSS / Excel like look. 

Several distributions like Normal, Binomial, Poisson, T-distribution etc
Some intervals (Z-insterval and T-interval)
Tests (One way ANOVA, Z-test, Smirnov,.. )
[/QUOTE]

It sounds like gnumeric should do most of what you need, although I'm not sure how it handles the various distributions.
```
sudo apt-get install gnumeric
```

Gnumeric is an Excel clone. However, when it comes to performing statistical analyses CORRECTLY, it far outperforms Excel.  I use gnumeric for all my data entry needs, as it exports well to plain text for use in SAS or R.  

I know its not something you want to hear, but if you will be doing much in the way of statistics in the future, it would really be worth your time to learn one of the CLI programs, of which R is the best in my opinion.  However, if all you need are simple statistics (ANOVA, t tests, descriptive statistics) gnumeric performs quite well and might be all you need, and will hopefully get you through this particular time-crunch.

---

### Post by akniss on 2006-03-15
If this project is the only stats you plan on doing, you might also consider borrowing a TI-83 graphing calculator from someone...

---

### Post by wouterommeslag on 2006-03-16
Thanks for the help. I installed the gnumeric package with success. 

Now, I got my stock rates from euronext.com and imported them in gnumeric. I used the formula log10 to calculate the logaritmic return. From those I calculated  max, min, mean, median, modus etc. 
So far, so good

Next Issue: I want to draw a histogram. How do I do that? I don't have frequencies, just the stock close. In Col A the date, In Col B the close rate, and in Col C the log of Col B

Tanks in andvance

---

### Post by Kyle- on 2006-03-16
There's a great freeware program out there called SalStat.  Google it. 

There's a Linux version written in Python, but I haven't had much luck with it.  Instead, you should download the Windows .exe file and run it under WINE.  

It's a great program for day to day stuff and it's free.  I especially like it becasue it does U tests and has a very easy to use interface.

By the way, has anyone had any luck getting SPSS to run under WINE or CrossOver Office?  I still have to boot to Windows to use SPSS for some fancier stuff.

---

### Post by towsonu2003 on 2006-03-16
[QUOTE=Kyle-]
By the way, has anyone had any luck getting SPSS to run under WINE or CrossOver Office?  I still have to boot to Windows to use SPSS for some fancier stuff.[/QUOTE]
I've filed a bug with wine, but don't think it will work out. I use qemu for SPSS so I don't have to boot one after the other... works slow, but works.

---

### Post by Steve1961 on 2006-03-16
I've been looking for an SPSS equivalent without much luck.  This programme seems to be moving in the right direction but it's still some way off:

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)

---

### Post by harnadem on 2006-03-16
I do a lot of statistical analysis and can offer two solutions that may help.  First, I run an older dos-version of SPSS (SPSS-PC) under xdosemu.  I really like the configurable data entry module that was lost in the later windows-version.  The older program runs the vast majority of my stats the same as the newer version.  There is another program you can try, called Linostat ([http://www.statpages.org/miller/openstat/LinOStat.htm]("http://www.statpages.org/miller/openstat/LinOStat.htm")) that is very similar to SPSS.  I tried running the preliminary version some years ago on a Redhat system and it didn't work.  However, the newer versions (and there have been several) may be better now.

I would love to be able to learn R but the learning curve seems steep.  Usually, I don't have a month to tinker around and need to use something right away.  I believe that BMDP also has an unix (linux?) version, but I don't believe that it is free ware.  Also, I think that Statistica released a linux version, and it really looked nice.  Again, however, I don't believe that it was freeware.

Good luck!  If you find something that works better, please post it for the rest of us.

---

### Post by Peter41az on 2006-03-16
Just out of curiosity.. have you looked at Aibo?

[http://www.iofreak.com/RCodeEditor.html](http://www.iofreak.com/RCodeEditor.html)

---

### Post by Steve1961 on 2006-03-16
[QUOTE=harnadem]I do a lot of statistical analysis and can offer two solutions that may help.  First, I run an older dos-version of SPSS (SPSS-PC) under xdosemu.  I really like the configurable data entry module that was lost in the later windows-version.  The older program runs the vast majority of my stats the same as the newer version.  There is another program you can try, called Linostat ([http://www.statpages.org/miller/openstat/LinOStat.htm]("http://www.statpages.org/miller/openstat/LinOStat.htm")) that is very similar to SPSS.  I tried running the preliminary version some years ago on a Redhat system and it didn't work.  However, the newer versions (and there have been several) may be better now.

I would love to be able to learn R but the learning curve seems steep.  Usually, I don't have a month to tinker around and need to use something right away.  I believe that BMDP also has an unix (linux?) version, but I don't believe that it is free ware.  Also, I think that Statistica released a linux version, and it really looked nice.  Again, however, I don't believe that it was freeware.

Good luck!  If you find something that works better, please post it for the rest of us.[/QUOTE]


Linostat looks interesting.  I'll give it a try and let you know.

---

### Post by akniss on 2006-03-16
[QUOTE=Peter41az]Just out of curiosity.. have you looked at Aibo?

[http://www.iofreak.com/RCodeEditor.html](http://www.iofreak.com/RCodeEditor.html)[/QUOTE]

I haven't checked it out.  anywhere you know of that we could get some screenshots.  it looks like its windows only... for windows it really is tough to beat Tinn-R for R script editing.

---

### Post by akniss on 2006-03-16
[QUOTE=wouterommeslag]Thanks for the help. I installed the gnumeric package with success. 

Now, I got my stock rates from euronext.com and imported them in gnumeric. I used the formula log10 to calculate the logaritmic return. From those I calculated  max, min, mean, median, modus etc. 
So far, so good

Next Issue: I want to draw a histogram. How do I do that? I don't have frequencies, just the stock close. In Col A the date, In Col B the close rate, and in Col C the log of Col B

Tanks in andvance[/QUOTE]


Histograms are made in gnumeric nearly identically as in Excel.  Select the column of interest, choose Tools > Statistical Analysis > Histogram...  from there you can sort through some options such as defining your bins and where to save the new information.  It will then (by default) create a new sheet with the bins and frequencies.  You can then select this data and create a column chart and your histogram is done!  The chart wizard is a little different from Excel and takes some getting used to, but it doesn't take more than a few minutes to get to where you can change the things you need to to make a proper histogram (like setting the axis titles and the gap between columns to 0%).

---

### Post by nanotube on 2006-03-17
for what it's worth... if you go to r-project.org, click on "manuals" in the sidebar, then click on "contributed documentation", you will see a lot of good howtos for R. my favorites are the "r for beginners" here: [http://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf](http://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf)
and the "econometrics in r" here: [http://cran.r-project.org/doc/contrib/Farnsworth-EconometricsInR.pdf](http://cran.r-project.org/doc/contrib/Farnsworth-EconometricsInR.pdf)

these two will really give you a good understanding of how to do just about anything in R.

---

### Post by wouterommeslag on 2006-03-18
I downloaded the SalStat and with Wine, It just works fine! Thanks to all for your helpful contributions!

---

### Post by dilidon on 2006-06-12
[QUOTE=wouterommeslag]I downloaded the SalStat and with Wine, It just works fine! Thanks to all for your helpful contributions![/QUOTE]
I'm also looking for smth that can do, for example, multinomial logit regressions and similar. However, after the kind suggestions in this thread I came to this last one, and I noticed that you're using SalStat with Wine, like Kyle recommended earlier.
I'm about to give SalStat a try, but I wanted to ask if you tried to use it without wine as well, or you just went for the Windows version?

PS. Does anyone have any other suggestion regarding programs that can do statistical analysis with categorical variables? (Most of the suggestions and also other discussions seem to be about economics and similar, which, I would imagine, make much more use of interval-ratio variables than social sciences - my case - do).

---

### Post by wouterommeslag on 2006-06-13
I tried with wine first. I needed SalStat for a paper so I had no time to experiment with linux dependencies. 

In the end, I mostly used OpenOffice Calc

I used the scatter in OpenOffice to draw a LinReg 
. Very easy: just scatter your data. Then you double click the chart. In the top menu you click insert --> statistics Tou can draw all kinds of regression (liniar, exponential, power etc etc) 

I tried to draw a histogram and a normald distribution in one chart, but that's not (yet) possible in OO.O

With the function TINV I calculated my confidence interval and T-test (the old fashioned way ;) )

---

### Post by nashjc on 2006-07-03
For information, Minitab 12 Student Edition installs fine under Wine for Dapper (0.9.9), though you need (no prizes for guessing I found out the hard way) you also need msttcorefonts.

Minitab 14 SE (that is currently distributed) doesn't make it properly. I haven't found out why.

Also for info, gnumeric drew on R code for the statistical distributions. Then Jody Goldberg found some improvements which are now back in R. A genuine good example of open source.

There are rudimentary test files for gnumeric, and to get folk to try them they are in .xls form. Anyone interested in contributing to such tests should contact me off list (nashjc _at_ 
uottawa.ca).

Now must go try SalStat and linostat.

JN

---

### Post by akniss on 2006-07-05
[QUOTE=nashjc]
Also for info, gnumeric drew on R code for the statistical distributions. Then Jody Goldberg found some improvements which are now back in R. A genuine good example of open source.

There are rudimentary test files for gnumeric, and to get folk to try them they are in .xls form. Anyone interested in contributing to such tests should contact me off list (nashjc _at_ 
uottawa.ca).
[/QUOTE]

Thanks for the great info nashjc.  Do you happen to know anything about the R plugin for gnumeric (RGnumeric)?  I have seen an older site about it, but nothing recent and it seems its no longer being developed.

---

### Post by nashjc on 2006-07-22
I too have been wondering about RGnumeric. I don't know Duncan Temple-Lang, but he is in an environment with lots of action on R. 

The issue may be that it really isn't worth putting too much effort into the interface when both sides are changing all the time, given that there are other approaches that are far more powerful. For example, a project just getting going within the Govt of Canada called ITERATION is using PostGresQL to do the data warehousing and plans to use R for stats and visualization. And it is an open source project. The purpose is to allow aggregation and processing of government expenditure information across departments, a constant issue for bureaucrats, and many countries have had several failed tries with big-money projects. This one seems to be a grass roots operation that is already starting to get the actual users involved in the development.

As a practical tool, make sure you know how to use read.csv in R and ssconvert tool from gnumeric. I find I can move back and forth simply by having a terminal screen open to do the back and forth.

JN

---

### Post by ssavelan on 2007-03-07
Way after the fact perhaps..  I have not yet read this whole thread.  

I am all about getting my Ubuntu to R-SAGE-OO together nicely.  I am trying the relatively simple task of plotting a Histogram that i could pop over to excel for; but, I am hoping to persist and do something cool with R.

I look forward to meeting statisticians on the forum here.  I'm studying in a Biostats/Epidemiology path mostly, but am interested in all sorts. 

stUbunstatistica!

The latest distro...

:guitar:

---

### Post by Lise on 2007-04-07
> **nashjc said:**
> I too have been wondering about RGnumeric. I don't know Duncan Temple-Lang, but he is in an environment with lots of action on R. 

The issue may be that it really isn't worth putting too much effort into the interface when both sides are changing all the time, given that there are other approaches that are far more powerful. For example, a project just getting going within the Govt of Canada called ITERATION is using PostGresQL to do the data warehousing and plans to use R for stats and visualization. And it is an open source project. The purpose is to allow aggregation and processing of government expenditure information across departments, a constant issue for bureaucrats, and many 
countries have had several failed tries with big-money projects. This one seems to be a grass roots operation that is already starting to get the actual users involved in the development.

As a practical tool, make sure you know how to use read.csv in R and ssconvert tool from gnumeric. I find I can move back and forth simply by having a terminal screen open to do the back and forth.

JN

Hi,

I am working with Edgy and I was troubleshooting with the installation of the RGnumeric -plugin. In fact it is the installation of gnumeric from source that failed.When I typed the command "./configure" I got this:
```

Configuration:

        Source code location:   .
        Compiler:               gcc
        Compiler flags:         -g -O2 -DG_DISABLE_DEPRECATED -DPANGO_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_MULTIHEAD_SAFE -DGTK_DISABLE_DEPRECATED -DLIBGLADE_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -DBONOBO_DISABLE_DEPRECATED -DBONOBO_UI_DISABLE_DEPRECATED  -Wall -Wmissing-prototypes  -Wsign-compare -Wpointer-arith -Wnested-externs -Wchar-subscripts -Wwrite-strings -Wdeclaration-after-statement -Wnested-externs -Wmissing-noreturn -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wno-pointer-sign
        Floating point type:    double

        UI:                     Gnome

        Perl Support:           no (failed to compile test program)
        Python Support:         unable to find Python.h

        GDA support:            NO.  libgda problem
        GNOME-DB support:       no
        Psiconv support:        missing dependencies




```

Somebody who can solve this problem

grtz
Annelies

---

### Post by nanotube on 2007-04-07
> **Lise said:**
> Hi,

I am working with Edgy and I was troubleshooting with the installation of the RGnumeric -plugin. In fact it is the installation of gnumeric from source that failed.When I typed the command "./configure" I got this:
```

Configuration:

        Source code location:   .
        Compiler:               gcc
        Compiler flags:         -g -O2 -DG_DISABLE_DEPRECATED -DPANGO_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_MULTIHEAD_SAFE -DGTK_DISABLE_DEPRECATED -DLIBGLADE_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -DBONOBO_DISABLE_DEPRECATED -DBONOBO_UI_DISABLE_DEPRECATED  -Wall -Wmissing-prototypes  -Wsign-compare -Wpointer-arith -Wnested-externs -Wchar-subscripts -Wwrite-strings -Wdeclaration-after-statement -Wnested-externs -Wmissing-noreturn -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wno-pointer-sign
        Floating point type:    double

        UI:                     Gnome

        Perl Support:           no (failed to compile test program)
        Python Support:         unable to find Python.h

        GDA support:            NO.  libgda problem
        GNOME-DB support:       no
        Psiconv support:        missing dependencies




```

Somebody who can solve this problem

grtz
Annelies

well, my guess is that you are missing some development libraries. probably things like python-dev, perl-dev, etc. so you just have to track them down and apt-get them.

but why are you compiling gnumeric itself from source, anyway? repositories version not good enough?

---

### Post by nashjc on 2007-04-15
Sorry that this is VERY late -- I"ve been fighting neck-high alligators for some months.

Getting Gnumeric to run from source in Ubuntu is very difficult (impossible??). The problem seems to be that Ubuntu has moved or renamed some libraries to get some other things to work. 

As someone very interested in having latest Gnumeric for testing, I tried very hard, got flamed by the developers, offered to pay money and got someone to come and sit with me -- he said it would take only 5 mins, but went away and never billed me after 5 hours. 

Finally I got everything to work just fine by setting up a VM Ware machine with plain Debian Testing and letting JHBuild run for several hours.  I recommend this approach for building from source and leaving the aggregation to the Ubuntu folk for everyday software.

JN

---

### Post by Lise on 2007-04-17
Hi,

Now I have installed the perl and python -dev plugins, so I had this message. I have also read the README and installed the needed packages (also libgda2-dev...)
```

Configuration:

        Source code location:   .
        Compiler:               gcc
        Compiler flags:         -g -O2  -Wall -Wmissing-prototypes  -Wsign-compare -Wpointer-arith -Wnested-externs -Wchar-subscripts -Wwrite-strings -Wdeclaration-after-statement -Wnested-externs -Wmissing-noreturn -Wstrict-prototypes -Wmissing-prototypes -Wmissing-format-attribute -Wmissing-declarations -Wno-pointer-sign
        Floating point type:    double

        UI:                     Gnome

        Perl Support:           yes (using perl)
        Python Support:         yes (using python)

        GDA support:            NO.  libgda problem
        GNOME-DB support:       no
        Psiconv support:        missing dependencies


```

---

### Post by earlycj5 on 2007-04-18
Wow, I'm surprised, no one's mentioned Rkward yet.  I use Tin-R when booted into my windows partition but much prefer Rkward.  It's in the repositories.

Cheers!

---

### Post by _Poincare on 2007-07-24
R is a pain in the a$$ to even TRY and begin to master. My department had several meetings over SPSS-like software for Linux/BSD and we settled on two dedicated windoze machines since the available software for Linux is just not user-friendly or is junk. Sadly, this seems to be the best solution until open source people get their heads out of the sand and realize what people need.

---

### Post by UbuWu on 2007-07-24
> **_Poincare said:**
> R is a pain in the a$$ to even TRY and begin to master. My department had several meetings over SPSS-like software for Linux/BSD and we settled on two dedicated windoze machines since the available software for Linux is just not user-friendly or is junk. Sadly, this seems to be the best solution until open source people get their heads out of the sand and realize what people need.

Did you try rkward? It is very similar to spss and you don't have to learn R to use it.

---

### Post by akniss on 2007-07-24
> **_Poincare said:**
> R is a pain in the a$$ to even TRY and begin to master. My department had several meetings over SPSS-like software for Linux/BSD and we settled on two dedicated windoze machines since the available software for Linux is just not user-friendly or is junk. Sadly, this seems to be the best solution until open source people get their heads out of the sand and realize what people need.

 I don't speak German.  Over the last few days, I have glanced at a German to English dictionary, and I have heard people speak German.  German seems to be an extremely difficult language to learn after studying it for almost 3 hours.  When will the Germans get their heads out of the sand and realize what people need?

You are correct that R is difficult to learn.  However, I take offense to your comment that open source people need to "get their heads out of the sand and realize what people need."  R is EXACTLY what many people need.  There are many people who NEED the power and extensibility that a program like R (or SAS or STATA) provide.  

Just because it is more difficult to learn than a dumbed down point and click interface like SPSS, doesn't mean that R is in any way inferior.  It is this mentality that brings approximately 10 students per year into my office who want me to tell them how to interpret the multivariate analysis that they have just conducted in SPSS, without any knowledge about what the analysis is or what it is supposed to do.  The 'ease' of SPSS leads most often to one thing: a meaningless statistical analysis that was 'easy' to do.

Don't get me wrong, I realize that for many people SPSS is the best balance of power and ease of use.  There are many things that SPSS does well, and for its intended audience it is usually a great program.  But don't tell us that just because you are too lazy to learn the R language that it is not "what people need."

---

### Post by nanotube on 2007-07-24
> **akniss said:**
> I don't speak German.  Over the last few days, I have glanced at a German to English dictionary, and I have heard people speak German.  German seems to be an extremely difficult language to learn after studying it for almost 3 hours.  When will the Germans get their heads out of the sand and realize what people need?

You are correct that R is difficult to learn.  However, I take offense to you comment that open source people need to "get their heads out of the sand and realize what people need."  R is EXACTLY what many people need.  There are many people who NEED the power and extensibility that a program like R (or SAS or STATA) provide.  

Just because it is more difficult to learn than a dumbed down point and click interface like SPSS, doesn't mean that R is in any way inferior.  It is this mentality that brings approximately 10 students per year into my office who want me to tell them how to interpret the multivariate analysis that they have just conducted in SPSS, without any knowledge about what the analysis is or what it is supposed to do.  The 'ease' of SPSS leads most often to one thing: a meaningless statistical analysis that was 'easy' to do.

Don't get me wrong, I realize that for many people SPSS is the best balance of power and ease of use.  There are many things that SPSS does well, and for its intended audience it is usually a great program.  But don't tell us that just because you are too lazy to learn the R language that it is not "what people need."

right on. =D> :)

---

### Post by _Poincare on 2007-07-26
You're missing the point. Open source software will not be adopted by large departments, organizations, what-have-ye until it is easy to use and somewhat on par with equivilent software. R is no where near as efficient in this perspective because it requires users to master a non-intuitive interface and essentially does not give users results out-of-the-box.  

If you take offense, then get off your pedestal and operate with the people who need to perform well in environments which are not cumbersome and difficult to learn.

Re your students who come to you with misunderstandings about multi-variate analysis... talk to your TAs or whomever is teaching them. Obviously there is a problem in that area.

---

### Post by nanotube on 2007-07-26
> **_Poincare said:**
> You're missing the point. Open source software will not be adopted by large departments, organizations, what-have-ye until it is easy to use and somewhat on par with equivilent software. R is no where near as efficient in this perspective because it requires users to master a non-intuitive interface and essentially does not give users results out-of-the-box.  

If you take offense, then get off your pedestal and operate with the people who need to perform well in environments which are not cumbersome and difficult to learn.

Re your students who come to you with misunderstandings about multi-variate analysis... talk to your TAs or whomever is teaching them. Obviously there is a problem in that area.

the point is that R does not aim to be an SPSS replacement, but rather a SAS or Stata replacement. it is a full-fledged programming language. Stata and SAS have good market share not because they are easy (SAS is certainly very far from being user friendly), but because they are powerful and flexible.

---

### Post by euler_fan on 2007-07-26
> **akniss said:**
> I'm pretty new to ubuntu (and Linux).  I have been using the statistical program R for some time now, and in fact it is the program that really got me interested in open source and prompted my switch away from windows.  my question is this... 
Are there any ubuntu users who know of a good R code editor?  I really liked Tinn-R for windows, but it doesn't look like there is a Linux version of this program.  I've recently tried Rcmdr, and wasn't too impressed.  I would also be interested if someone has had experience using Tinn-R under linux with WINE or other similar workarounds.  Any help would be greatly appreciated.

to head off the inevitable question, I've already searched google and the R-help lists, and no really exciting finds.  (that's where I first heard of Rcommander)

EMACS with ESS if you work with it frequently (say, as a job).

I use mine regularly (couple of times per month) interactively, but am getting more and more into scripts, in which case I would say Cream (which is built on VIM) which is a nice text editor with syntax highlighting. Then you just source it into R when you feel like it. The best part is you don't have to spend the month learning EMACS. :)
 
That said, I may still switch over to EMACS myself since I'm going to be doing a fair bit of debugging and sending a script into R without working in the terminal could be handy.

---

### Post by euler_fan on 2007-07-26
> **akniss said:**
> I don't speak German.  Over the last few days, I have glanced at a German to English dictionary, and I have heard people speak German.  German seems to be an extremely difficult language to learn after studying it for almost 3 hours.  When will the Germans get their heads out of the sand and realize what people need?

You are correct that R is difficult to learn.  However, I take offense to your comment that open source people need to "get their heads out of the sand and realize what people need."  R is EXACTLY what many people need.  There are many people who NEED the power and extensibility that a program like R (or SAS or STATA) provide.  

Just because it is more difficult to learn than a dumbed down point and click interface like SPSS, doesn't mean that R is in any way inferior.  It is this mentality that brings approximately 10 students per year into my office who want me to tell them how to interpret the multivariate analysis that they have just conducted in SPSS, without any knowledge about what the analysis is or what it is supposed to do.  The 'ease' of SPSS leads most often to one thing: a meaningless statistical analysis that was 'easy' to do.

Don't get me wrong, I realize that for many people SPSS is the best balance of power and ease of use.  There are many things that SPSS does well, and for its intended audience it is usually a great program.  But don't tell us that just because you are too lazy to learn the R language that it is not "what people need."

+1

SPSS is certainly great at doing the things it does correctly (but I'm skeptical about any system that tries to make statistics too easy to do--even front ends for R), but try making SPSS sample from a truncated Cauchy distribution over a non-polygonal region for use in Metropolis-Hastings MCMC and you'll see a situation where R is superior :)

---

### Post by dugh on 2007-08-13
> **UbuWu said:**
> Did you try rkward? It is very similar to spss and you don't have to learn R to use it.

The ubuntu rkward package is broken.  It gives an error about an undefined symbol.

Apparently it was fixed in Debian 4 months ago, but we haven't seen it make its way to Ubuntu (at least not Feisty).  
[http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg98845.html](http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg98845.html)
Ubuntu seems to only update software that is very very popular (like firefox) or else central to the os (like python libraries).  They haven't even updated Mozilla Thunderbird (1.5, current version is 2.0 or so) or the hplip software that you need to print correctly to hp printers.

I'm trying JGR, but it's "data editor" is a very poor substitute for the spreadsheet editors in other tools like openoffice or spss.
Someone is working on an R extension for openoffice, but it is still very early in development.

---

### Post by spooner on 2007-08-15
Wel, anyway going back to the very first question... Tinn-R runs fine under wine. You have to install R again (for wine) and also firefox (wine) if you want to view the html help file.
I've been having a problem getting the extra packages to install because it appears the R uses a command line call to unzip the files and then just copies the directories into the library folder. But you can browes using nautilus, thunar, etc to the temp folder and do this manually. Then restart R call "link.html.update()" and this gets around the problem. Haven't figured how to enable zip for wine cmd yet!!!.
I agree that Tinn-R is great. It takes R from a good stats program to a very easily scriptable matlab alternative that is free!

---

### Post by ahmatti on 2007-10-22
> **euler_fan said:**
> EMACS with ESS if you work with it frequently (say, as a job).

I use mine regularly (couple of times per month) interactively, but am getting more and more into scripts, in which case I would say Cream (which is built on VIM) which is a nice text editor with syntax highlighting. Then you just source it into R when you feel like it. The best part is you don't have to spend the month learning EMACS. :)
 
That said, I may still switch over to EMACS myself since I'm going to be doing a fair bit of debugging and sending a script into R without working in the terminal could be handy.

I have to say that ESS is the best option for me! After some experience with using kate, rkward and JGR I find that ESS is the most productive,

I have also been very hesitant to learn Emacs and ESS reading from the forums that it takes a month to learn. That not true at all!! [COLOR="Navy"]I find that you can use it pretty well after few hours of training[/COLOR], and it **really pays of to read the emacs tutorial (In emacs menus: help->tutorial) and the ess docs**. 

Sending lines, sections or paragraphs directly to R with a couple of key strokes is really handy and when you don't recall all the shortcuts straight away you can just use the menus.

Also I find the emacs and ess refcards very usefull :)
[http://refcards.com/docs/gildeas/gnu-emacs/emacs-refcard-a4.pdf](http://refcards.com/docs/gildeas/gnu-emacs/emacs-refcard-a4.pdf)
[http://ess.r-project.org/refcard.pdf](http://ess.r-project.org/refcard.pdf)

---

### Post by zasf on 2007-12-10
> **towsonu2003 said:**
> sorry to post kinda off topic but, do you know of a nice newbie friendly R howto / tutorial that will get me started from the beginning? And, (being a foreigner to R), does it have a gui frontend-kinda window (like in spss)?

see comment #23 and #24 on this other [thread ]("http://ubuntuforums.org/showpost.php?p=3925315&postcount=24")

---

