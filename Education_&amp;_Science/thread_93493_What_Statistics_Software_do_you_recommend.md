---
title: "What Statistics Software do you recommend?"
date: 2005-11-22
forum: Education &amp; Science
---

### Post by MakubeX on 2005-11-22
I would like to know the softwares that you use for statistics (excluding SPSS, obviously) or statistical computations on Linux.

Thanks!

---

### Post by Wes24 on 2005-11-22
[QUOTE=MakubeX]I would like to know the softwares that you use for statistics (excluding SPSS, obviously) or statistical computations on Linux.

Thanks![/QUOTE]

Don't think that there is so much available, according to my knowledge the only still actively maintained package is pspp ([PSPP]("http://www.gnu.org/software/pspp/pspp.html")). I could be wrong however...;)

That's one of the reasons I keep dual booting with XP: I need SPSS for University.

---

### Post by Manny C on 2005-11-22
A couple notable ones. You can download and run the open-source version of S-plus, also known as "R" on linux. You will find it packaged as R-base. Someone is currently working on getting the linux version of WinBUGS operating through R. Not promising at the moment.

I believe that a linux version of SAS is available (but non-free).

You can (I have) bought Matlab and install the statistics toolkit. Ditto for Maple.

Did you have a particular software package in mind?

---

### Post by ssam on 2005-11-22
you might find some useful info here [https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by MakubeX on 2005-11-28
Thanks for the suggestions and recommendations!

---

### Post by dudus on 2005-11-29
Octave has some statistics. Not many, some. But it had cover my needs.

---

### Post by tommie74 on 2007-07-21
I have installed SPSS 11.5 under Linux using codeweavers cxoffice 6.1.0. (commercial version of wine). I used the same botlle (virtual windwos c: disk) that I installed office 2000 on. Everything seems to work allright except for the graph functions. I can can load data, analyze it, produce tables with output etc. Only producing graphs seems problematic. The install is going smoothly, asking for a serial etc.
So if you can miss graphs, SPSS seems to work allright. The more people us SPSS with cxoffice, the bigger the chance that they will start support on it.
Greetings,
Thomas.

---

### Post by akniss on 2007-07-21
> **tommie74 said:**
> I have installed SPSS 11.5 under Linux using codeweavers cxoffice 6.1.0. (commercial version of wine). I used the same botlle (virtual windwos c: disk) that I installed office 2000 on. Everything seems to work allright except for the graph functions. I can can load data, analyze it, produce tables with output etc. Only producing graphs seems problematic. The install is going smoothly, asking for a serial etc.
So if you can miss graphs, SPSS seems to work allright. The more people us SPSS with cxoffice, the bigger the chance that they will start support on it.
Greetings,
Thomas.

Thanks for the information, but is there any particular reason you posted the exact same thing in 4 diferent threads?

[http://ubuntuforums.org/showpost.php?p=3056277&postcount=7](http://ubuntuforums.org/showpost.php?p=3056277&postcount=7)
[http://ubuntuforums.org/showpost.php?p=3056249&postcount=2](http://ubuntuforums.org/showpost.php?p=3056249&postcount=2)
[http://ubuntuforums.org/showpost.php?p=3056274&postcount=3](http://ubuntuforums.org/showpost.php?p=3056274&postcount=3)
[http://ubuntuforums.org/showpost.php?p=3056276&postcount=5](http://ubuntuforums.org/showpost.php?p=3056276&postcount=5)

And while it may be true that if more people use SPSS with crossover than it will be better supported, wouldn't it be better to support a program that actually runs natively (with functioning graphing capabilities) on linux if that is the OS of choice?  Or if more people tell the makers of SPSS that they want a Linux version instead?

---

### Post by zasf on 2007-09-19
I raccomend R (package r-base). You can also find matlab for linux, if you're used to that and want to make your passage to linux easyer

---

### Post by euler_fan on 2007-09-20
I highly recommend R for anyone looking to do more "high powered" or customized work in statistics.

I've used R, SAS, and Minitab (R on both, SAS, Minitab on Windows) and while SAS can be great, I think SAS is better at set/well-defined analyses whereas R is better for custom work. R is also designed as a language/environment where the SAS macro facility left me feeling like it was an add-on. Custom scripting is much closer to the everyday in R.

---

### Post by mycotropic on 2007-09-21
I installed SAS Linux the other day and it's a monster beast creature from hell to get running as far as I can tell. I've been a SAS programmer for ~10 years and I'm actually getting a little desperate to get it working in this environment.

Oh and the instructions provided by SAS for Linux install? Every single command was incorrect using Ubuntu. All of them.

And of course it still doesn't run but I'll post an "install SAS under Ubuntu" thread as soon as I work out what the issue is.

---

### Post by machoo02 on 2007-09-21
Gotta go with R.  It may take a little time to learn, but there are plenty of references and tutorials out there to make this process a little easier.

---

### Post by docdoc on 2007-09-26
I really need SAS. I tried to install it a year ago but never got it to work. I then worked a bit with SAS in Virtualbox but eventually left Ubuntu again for XP.
I am a doctor and researcher and currently I haven't got the time to change to R. I have tried it a number of times but when things get complicated I am back in SAS.

If anyone has got SAS to work under Ubuntu I would very much like to hear how.

---

### Post by zasf on 2007-09-26
> **docdoc said:**
> If anyone has got SAS to work under Ubuntu I would very much like to hear how.

I've never tried SAS on linux, but I gave a chance to Matlab on linux. I can tell you that the user interface is really ugly and buggy compared to windows.. in my opinion it is worth a try if you want to do an easy switch from windows to linux, ie first you switch os and then you switch the programs you use. 

This will allow you to run your old programs within the new os, but in the long run it is much better to go on open source software.

---

### Post by earlycj5 on 2007-09-26
R but I do have a computer at my disposal with RHEL4 and SAS for Linux on it.

Still I prefer R where I can use it.

---

### Post by machoo02 on 2007-09-26
> **docdoc said:**
> I really need SAS. I tried to install it a year ago but never got it to work. I then worked a bit with SAS in Virtualbox but eventually left Ubuntu again for XP.
I am a doctor and researcher and currently I haven't got the time to change to R. I have tried it a number of times but when things get complicated I am back in SAS.

If anyone has got SAS to work under Ubuntu I would very much like to hear how.

Are you trying to install the Windows version of SAS?  I looked over that the [Wine AppDB]("http://appdb.winehq.org"), and although the reports are old no one seems to have had luck installing SAS through WINE.  It seems that there is a Linux version of SAS out there (see earlier posts).  Is this the version you are trying?

---

### Post by docdoc on 2007-09-27
> Originally Posted by machoo02:
Are you trying to install the Windows version of SAS? I looked over that the Wine AppDB, and although the reports are old no one seems to have had luck installing SAS through WINE. It seems that there is a Linux version of SAS out there (see earlier posts). Is this the version you are trying?

No, given the complexity of SAS, which may even give you a hard time installing it under XP, Wine is not an option.
I tried to install the SAS for Linux v9.13. The thing is that SAS only support Suse and RHEL. Maybe I'll give openSuse another try even though I prefer Ubuntu.

---

### Post by bingouk on 2007-09-28
R is superb for doing serious statistics and has thousands of exta packages for download from CRAN. There some useful frontends to the command line. I think JGR works in linux but the best for new users is RCMDR ([http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)). Not tried it for linux and use the command line anyway but it's a good way to learn the syntax.

---

### Post by machoo02 on 2007-09-28
If you do decide to switch to R, the[ R-wiki]("http://wiki.r-project.org") has a page on some [sample translations betwen SAS and R code]("http://wiki.r-project.org/rwiki/doku.php?id=getting-started:translations:sas2r") and [several other statistics programs]("http://wiki.r-project.org/rwiki/doku.php?id=getting-started:translations:translations").

---

### Post by gnuman on 2007-09-28
I just got done taking a course in SAS programming.  Although SAS is very capable of handling large data sets, my heart is with R.  I've removed the "limited student educational package discount rate" version and will now dedicate my free time to learn R. It's quite capable and efficient, IMO.

):P

---

### Post by bingouk on 2007-09-28
> **gnuman said:**
> I just got done taking a course in SAS programming.  Although SAS is very capable of handling large data sets, my heart is with R.  I've removed the "limited student educational package discount rate" version and will now dedicate my free time to learn R. It's quite capable and efficient, IMO.

):P

I agree! SAS is the default in the medical industry like S-Plus was in academia a few years ago. For me R has overtaken both and after moving from S-Plus I was shocked by how much more is available in R. I had to do a generalised partial least squares analysis recently (with a multinomial rather than continuous response and several thousand covariates). My employers had MATLAB, SAS, S-PLUS and GENSTAT. Only R could do the job with the gpls package! And if your into bioinformatics R is the ONLY option for me!

---

### Post by kstella on 2007-12-03
I find more and more reason to love the forums every time I run a search. I'm looking for statistics software, and this thread was very helpful. Thanks, guys! :)

---

### Post by plvera on 2007-12-04
I also highly recommend R. Although the learning curve can be steep, the results are definitely worth it.

Check out the main web page and the help newsgroups.

[http://www.r-project.org/](http://www.r-project.org/)

There are plenty of manuals online, but I recomend getting:

Introductory Statistics with R, Dalgaard, P.  (2002)
The R Book, Crawley, M.J. (2007)

Good luck!

---

### Post by zasf on 2007-12-10
If you want to learn basic time series analysis and get started with R, I would reccomend [Time Series Analysis with R - Part I]("www.statoek.wiso.uni-goettingen.de/veranstaltungen/zeitreihen/sommer03/ts_r_intro.pdf -")

Matteo

---

### Post by subs on 2007-12-11
this was intriguing...

---

### Post by Klipt on 2007-12-16
Also check out the [R/SPlus-Python Interface](http://www.omegahat.org/RSPython/index.html) which lets you call R functions from Python! There are some [statistical packages for Python](http://www.astro.cornell.edu/staff/loredo/statpy/) but currently much more limited than R.

---

### Post by dirkjot on 2008-01-29
I have SAS successfully working in a Qemu box.  This is very easy to set up and works well.  Qemu is a full emulator, which allows you to boot up windows inside a window on linux.  It works very well and is very fast (if you install kqemu, which is not in gutsy yet, as far as I know, but easy to install nonetheless).  Tip: After setting things up, use the VNC interface over the standard SDL one.

I installed windows 2000 inside my qemu  2Gig fake harddisk and then installed SAS into it without any problems.  SAS works like a charm.  I have also installed SPSS so I now have all my stats programs available.   With some simple setup, you can share documents between the windows and unix environment.  

hope this helps,
Dirk

[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

---

### Post by homeriq5 on 2008-01-30
There is indeed a version of SAS 9.1.3 that is available for linux, however it is not free unless it is licensed by your company/university.  I was able to pick up a free copy of the linux version of SAS 9.1.3 today from my school and had it installed with only a few minor problems.  The setup went relatively smoothly, but when I tried to invoke SAS in the terminal following installation it gave me an error message about not being able to write to the "Work" folder and was thus not able to open.  I googled the error message and found a solution online which involved changing the location of the work folder to a location where I had read/write permissions.  The interface itself is similar to that of the windows version, but for some reason the program editor, log, output, explorer, etc were all contained in separate windows instead within one SAS window.  So far, I think the windows version is a lot easier to use

---

### Post by earlycj5 on 2008-01-30
I've been using SAS on my openSUSE laptop lately, but not directly on it.

We have SAS 9.1 on our main Sun machine on campus that hosts our e-mail, etc.

You can easily ssh in.
```

%ssh -X user@host.host.whatever

```

Allow your X server to allow the connection from the remote host (type this on your local machine).
```

%xhost+

```

Doing this and using knetworkattach to attach to my remote account the work is pretty much seamless.

---

### Post by TimMills on 2008-02-09
I use R too, and recommend it (and Ubuntu, LaTeX, etc) to any of my fellow PhD students who will listen.

I had one mild problem installing extra packages in R - the command in R to install packages doesn't work if you are running R as a normal user (you don't have permissions).

If a package is in the repositories, no problem - Symantec is my friend.

If it's not in the repositories, the R command to install packages is

> install.packages("...")

entered during an R session.

But if you want to install a package on the system (not just in your home directory), you need super-user privileges.  So rather than starting R the normal way:

$ R

you need to start it as an administrator:

$ sudo R

Then you run install.packages(), exit R, re-enter as a normal user, and all is well.

Also, I'd add Harald Baayen's book *Analysing Linguistic Data:  A practical introduction to statistics* - almost out, but available here as a draft:  [http://www.ualberta.ca/~baayen/publications/BaayenCUPstats.pdf]("http://www.ualberta.ca/~baayen/publications/BaayenCUPstats.pdf")

It's written for linguists, with worked examples available as an R package, and every step explained (including exact commands) in the text.

---

### Post by knattlhuber on 2008-02-16
> **docdoc said:**
> I really need SAS. I tried to install it a year ago but never got it to work. I then worked a bit with SAS in Virtualbox but eventually left Ubuntu again for XP.
I am a doctor and researcher and currently I haven't got the time to change to R. I have tried it a number of times but when things get complicated I am back in SAS.

If anyone has got SAS to work under Ubuntu I would very much like to hear how.

I managed to install SAS 9.1.3 way back in 2005 on an older Ubuntu version. After fixing some errors in the license file, it installed without any major problems.
However, the usability of the Linux version was so poor that I exchanged it for the Windows version within a week. E.g. the editor wouldn't do highlighting or drag&drop, carriage returns didn't work. It was all very weird. A friend of mine, who also uses SAS under Ubuntu, said that because of that he uses Vim to write/edit his syntax and then pipes the file to SAS.

---

### Post by knattlhuber on 2008-02-16
Another stats package that should be mentioned in this thread is Stata. There is a Linux version of Stata available.

While Stata is not as powerful as R or SAS, it's IMO better than SPSS and it should satisfy the needs of the average biostatistician/epidemiologist. Stata has a quite strong user community that provides a lot of extra commands/tools. It might be worth giving it a try if SAS won't install and R is too complex.

Having said that, I haven't tried Stata on Ubuntu yet. I still run my analyses on Stata for Mac OSX..

---

### Post by earlycj5 on 2008-02-16
> **knattlhuber said:**
> Another stats package that should be mentioned in this thread is Stata. There is a Linux version of Stata available.

While Stata is not as powerful as R or SAS, it's IMO better than SPSS and it should satisfy the needs of the average biostatistician/epidemiologist. Stata has a quite strong user community that provides a lot of extra commands/tools. It might be worth giving it a try if SAS won't install and R is too complex.

Having said that, I haven't tried Stata on Ubuntu yet. I still run my analyses on Stata for Mac OSX..

Interesting, never used Stata, when I was involved in teaching epidemiology we taught the class using R.

---

### Post by gah789 on 2008-03-24
Stata works fine under several flavours of Linux that I have tried it on - including Ubuntu & OpenSuse.  The structure of the program - with extensions provided by ado files, etc - means that it is only necessary for the developers to get the core compiler/interpreter right and the rest can be left to individual modules.  I use it under Windows & Mac OS-X as well and haven't come across major problems switching programs from one implementation to another.

I gave up using SAS - and previously SPSS - because of its cost and inflexibility.  The only reason to use either of them now would be if one had to process massive amounts of data or, in the case of SAS, for complex data manipulation.  But under Linux with lots of RAM and/or multiiple processors it is possible to use the SE or MP versions of Stata for relatively large datasets.

R can probably do anything that Stata can do and more, but I find that it is a world of its own and switching from SAS is likely to be horribly slow, whereas the introductory guides to Stata are quite good and the transition is relatively painless.

---

### Post by pape on 2008-03-28
I've mostly use Stata, which I think is an excellent tool available for both Windows and Linux. The only problems with it are that it is commercial, and they annoyingly make different Stata versions incompatible with each other, keeping people in an expensive upgrade cycle (It can be 'found' from the interwebs as well...) . 

Once I find the time, I will definitely learn R, but will probably remain dependent on Stata for a long time.

Also note that for doing econometrics, there is gretl, an open source package, which does most of the basic stuff (ie undergraduate econometrics).

[http://gretl.sourceforge.net/](http://gretl.sourceforge.net/)

---

### Post by Zimmer on 2008-03-28
[http://ubuntuforums.org/showthread.php?t=641448](http://ubuntuforums.org/showthread.php?t=641448)
see post #2
SAS doesn't automatically define a directory to use as the "WORK" library, so you have to define it yourself when you start the program.

---

### Post by LexLuthor08 on 2008-10-15
I really need spss. It's the standard software for my field and I need to be able to receive and share its data format with colleagues.

But I tried several versions in wine and nothing seems to work (or it works but without any output graphs, which makes it pretty much useless to me).

The linux version of spss 16.0 is missing the most important statistic analysis functions. 
I also tried the linux clone "pspp" which is also missing the same functions.

I need to run "repeated measures" (anova with within-subject factors) as simple as possible. Is that so much to ask for?

---

### Post by knattlhuber on 2008-10-15
It's hard for me to believe that you shouldn't be able to do a two-way ANOVA with SPSS. Stats functions shouldn't differ by OS version. You could try doing it as a random-effects model with observations nested in subjects...

Stata is a more powerful yet easier to use package and doesn't cost as much as SPSS. But if you really really can't do without it, you could run SPSS in Virtualbox or VMware (which would require of course a WinXP/Vista license).

BTW, the SPSS file format shouldn't be an obstacle if you want to use a another stats package. SPSS can export into most data file formats. R can read SPSS files (using the 'foreign' library) and export into whatever format you wish.

---

### Post by XxX_VLAD_XxX on 2008-11-14
OK  maybe you can help me, I install R or so i think, I did this:

sudo apt-get install r-base

It did installed it, then I tried to run it

~$ r

it said I neede to install another package so I did

sudo apt-get insttall littler

it did install it, but where?  I can't run it, I tried again
~$ r

but nothig happend, not an error message or get my terminal back...   what you thing is wrong, cause I can't find r-base in Synaptics

---

### Post by knattlhuber on 2008-11-14
Haha.. happened to me before, too. Try

```
R
```

:)

---

### Post by gunksta on 2008-11-16
> **LexLuthor08 said:**
> I really need spss. It's the standard software for my field and I need to be able to receive and share its data format with colleagues.

But I tried several versions in wine and nothing seems to work (or it works but without any output graphs, which makes it pretty much useless to me).

The linux version of spss 16.0 is missing the most important statistic analysis functions. 
I also tried the linux clone "pspp" which is also missing the same functions.

I need to run "repeated measures" (anova with within-subject factors) as simple as possible. Is that so much to ask for?


Let me start by saying that I completely understand and share your frustration. SPSS is a standard in many industries. There are some options in the world of Linux. SPSS 16+ for example is available on the Linux platform. I just looked at the specs sheet available at:

[http://www.spss.com/media/collateral/S17SPC-0908lr.pdf](http://www.spss.com/media/collateral/S17SPC-0908lr.pdf)

I do not see any feature specific differences between the Windows, Mac and Linux versions of SPSS. ANOVA is certainly a basic test, and should be available. If it's not, I would call the SPSS people and make them give you a non-borked version of the software. That software is expensive. If you or your employer paid for it (out the nose) make them support it.

Off the top of my head, I think PSPP can do what you want, but I think to get the specific test you want, you may have to write the syntax, because the GUI may not fully support what you need, yet.

Finally, I know R can do this. But, R has a rather steep learning curve. Seriously, give yourself a week before you declare it useless. It took me a solid week of learning and reading before I really started to become comfortable with it. It DOES make sense and it is incredibly powerful, once you get used to it. Now, here's the deal. It's compatibility with SPSS may or may not be adequate for you. Do you need to read/write data, or do you need to use exinsting SPSS syntax? R can read in any data set (that I have encountered) that is saved in the .sav format file. But, R can NOT read or use SPSS syntax. If you just need to open up a pile of data, you can use R. If you need to run an analysis written by someone else, R is not the tool you need.

Good luck!

---

### Post by sarahjohn on 2008-11-17
Most statistical packages should perform all basic- to intermediate-level statistical analyses. I am familiar with The SAS System, SPSS, and S-Plus.

---

### Post by mariashaun on 2008-11-19
1. Introductory courses that assume no software background and 
      do some "hand-holding" for certain packages
   2. Courses that do not require software
   3. Courses that require general purpose software like SAS, 
      SPSS, etc.
   4. Courses that require specialized software
   5. Courses that use R

I highly recommend R for anyone looking to do more "high powered" or customized work in statistics.

---

### Post by gunksta on 2008-11-20
I like statistics a little too much, and I tend to be a little promiscuous in my software choices. I'll randomly use a tool for a project, just so I can learn how to use it better. That being said, each tool has a niche. I believe that knowing several tools fairly well makes me a better analyst than being a walking guru with any single tool.

For example, I LOVE how easy it is to import .csv data into R. By comparison, SPSS/PSPP are completely brain dead. I don't want to waste my time typing in all of the value labels. Example. I have a field with the answers of "Yes" and "No". If my text file has "Yes" and "No" in the field, R understands that this is a categorical field with two values. In SPSS/PSPP, Yes and No have . . . . meaning. I must recode them (yeah for sed!) into ones and fives. Then, once the data is imported, I must define a label so that 1 = Yes and 5 = No.

It's annoying. My example minimizes the problem, because it would take me about 5 seconds. But, when I have 117 fields in a data set, some with 8 - 9 label values, it becomes annoying. I don't like wasting my time typing labels, when I could be answering questions for my boss. When the dataset has lots of value labels, R makes my life easier.

Some complain that R is not very good with large datasets. I myself have not found this to be the case, but I rarely use R for datasets in excess of a few thousand rows. In the social sciences, that's a fairly large dataset, unless you have direct access to government records. When people are worried about the RAM constraints with R, I often recommend using a database system to handle the sorting, and let R access the information through the database. If you're really hurting, the database could be run on a physically separate machine, which would help minimize the amount of RAM needed.

I always tell people to learn lots of tools. You'll be happier.

---

### Post by iQuizzle on 2008-12-16
i think most have already been mentioned.

- i've heard great things about **R**, but never used it.
- **IDL** has something written for just about everything
- **python** can do anything, but you might have to hunt around for
the modules you want. (my swiss army knife as a scientist)
- **octave** (a lot like matlab)
- **SAS**, never used it but my dad loves it
- of course **open office** for generic spreadsheet stuff

---

### Post by euler_fan on 2008-12-19
R hands down. It has, for those interested in taking the time to learn to use it well, far more horsepower than most systems designed to only do what was "built in" and has as standard features much of what statisticians need on a day to day basis. Assuming, of course, if you're doing anything terribly fancy or with huge datasets you're willing to go the extra mile it takes to use R efficiently either by packaging up your software with bits of C, C++, or FORTRAN/using a database interface package.

SAS, aside from being expensive, requires a completely different language to write macros.

---

### Post by grantbuntu on 2009-07-23
A new open source option that has only recently become available is SOFA Statistics ([http://www.sofastatistics.com](http://www.sofastatistics.com)).  The emphasis is on ease of use, learn as you go, and beautiful output.  It is not aimed at the same niche as R, SAS or SPSS but it should be useful for many users and purposes. [Disclosure - I am the lead developer].  SOFA is cross-platform and will work anywhere Python will run.  The deb and Windows packages can be found at sourceforge ([https://sourceforge.net/projects/sofastatistics/](https://sourceforge.net/projects/sofastatistics/)).  SOFA Statistics allows the user to connect directly to (as opposed to import) MySQL, SQLite, MS Access, and MS SQL Server, and data can be imported from csv or MS Excel.  In addition to nested tables with row and col %'s, sd, mean, median etc there are Independent and Paired t-tests, Mann Whitney U, Wilcoxon Signed Ranks, Pearson's Chi Square, one-way ANOVAs, Kruskal Wallis H, Spearman's and Pearson's R. In addition to the GUI interface, processes can be automated using Python - whether from exported scripts or manually crafted ones.  SOFA Statistics is released under the AGPL and is under active development.

---

### Post by gunksta on 2009-07-24
**grantbuntu:** I have to tell you that this looks very very very interesting. I'll be honest. I love the oddball mixture of R and Postgres that I have running at work and at home. I've got it tweaked down to where it really works for me. But, the learning curve was a bit steep and emacs is not universally loved (for the life of me I don't understand why).

Although I am also excited by the progress I see being made in PSPP, your program is clearly aimed a niche that is not always well served. It looks incredibly easy to use, yet provides access to an underlying API for more advanced users. Better yet, the fact that Python is the underlying language makes it accessible to Linux programmers who don't necessarily want to learn yet another language for a specific tool.

I noticed in the FAQ that postgres support is coming. Thank you.

I have a few questions for you that I don't see answered on the FAQ  / website.

[LIST=1]
[*]What is your process for statistical validation? In other words, if I ask for a weighted mean, how do I KNOW I've gotten the right answer? I know R and other tools use the NIST data sets to test for accuracy.
[*]How does it handle large data sets? I was VERY pleased to see that you are enabling/encouraging users to use databases for data management. To me, this implies that large datasets are OK.
[*]Will this be available in the repos for Ubuntu 9.10?
[*]What is your business plan for this software. The website is awfully professional and the program appears to be pretty mature. This doesn't look like a fresh out-of-the-oven project that you started working on last week to scratch an itch. This looks pretty professional (this is intended as a compliment, nothing more/nothing less).
[/LIST]

I didn't see this until 12:30 or so tonight. I will definitely be installing this application soon, so I can play around with it in more detail. I'd also love to be able to integrate this with R,     but I realize you probably have plenty of requests right now.

Oh goody! A new toy.

---

### Post by ugm6hr on 2009-07-24
> **grantbuntu said:**
> A new open source option that has only recently become available is SOFA Statistics ([http://www.sofastatistics.com](http://www.sofastatistics.com)).  The emphasis is on ease of use, learn as you go, and beautiful output.  It is not aimed at the same niche as R, SAS or SPSS but it should be useful for many users and purposes. [Disclosure - I am the lead developer].

I am also very impressed by the brief tour of your website.

When the graph production (for inclusion in posters / reports etc) becomes available, I will make a lot of use of this, I'm sure.  Nevertheless, I'll give it a whirl in the near future.

Have you considered starting a new discussion thread for this?  I would anticipate a reasonable amount of interest here.

---

### Post by ahmatti on 2009-07-24
@grantbuntu,
Very nice looking software, I will give this a try when I get back to work in a few weeks. This might be something that I can use in my teaching instead of SPSS in some basic courses.

 If you do decide to add statistical tests to the package I would welcome mixed effect models, that have become somewhat of a standard in animal science and ethology and have replaced plain ANOVA. Also the R interface for them is quite difficult at times..

---

### Post by ugm6hr on 2009-07-29
I have just installed and briefly tried sofastatistics.

Unfortunately, it doesn't behave well on a low resolution Netbook screen (which I prefer to use for almost all computing tasks these days), so I'll have to give it a go on my main laptop some other day.

---

### Post by rewyllys on 2009-07-29
> **grantbuntu said:**
> A new open source option that has only recently become available is SOFA Statistics ([http://www.sofastatistics.com](http://www.sofastatistics.com)).  The emphasis is on ease of use, learn as you go, and beautiful output.  It is not aimed at the same niche as R, SAS or SPSS but it should be useful for many users and purposes. [Disclosure - I am the lead developer].  SOFA is cross-platform and will work anywhere Python will run.  The deb and Windows packages can be found at sourceforge ([https://sourceforge.net/projects/sofastatistics/](https://sourceforge.net/projects/sofastatistics/)).  SOFA Statistics allows the user to connect directly to (as opposed to import) MySQL, SQLite, MS Access, and MS SQL Server, and data can be imported from csv or MS Excel.  In addition to nested tables with row and col %'s, sd, mean, median etc there are Independent and Paired t-tests, Mann Whitney U, Wilcoxon Signed Ranks, Pearson's Chi Square, one-way ANOVAs, Kruskal Wallis H, Spearman's and Pearson's R. In addition to the GUI interface, processes can be automated using Python - whether from exported scripts or manually crafted ones.  SOFA Statistics is released under the AGPL and is under active development.

Very interesting and impressive!  That's my reaction to your video demonstration, which I just watched.

I taught basic statistics at the university level for 31 years till retiring 6 years ago.  I'd have loved to have SOFA Statistics for my students (and myself) to use; and I'll be recommending it to some colleagues who are still actively teaching and researching.

---

### Post by grantbuntu on 2009-07-31
@gunksta - thanks very much for the positive feedback.  

Re: postgresql, I might have a look at that in a week or so.  The Python support seems good and I have a pretty standard approach going now for each database engine plugin.

Re: statistical validation, I have started building a unit testing framework but that is still at its very early stages.  Clearly, that will need to be extensive (and visible to the community) before the 1.0 release.  I will definitely look at using NIST datasets as part of that ([http://www.itl.nist.gov/div898/strd/general/main.html](http://www.itl.nist.gov/div898/strd/general/main.html)).

Re: large datasets, I expect the only limit will be Python, the database in question, and user hardware.  With the report tables, for example, the data is gathered by a series of SQL statements.  The program is then only tasked with displaying it.  I put a limit on the number of cells you could have in a useful table.  I set it quite high so no-one should bump into it unless they make a mistake and select an inappropriate variable e.g. phone number ;-).

Re: Ubuntu repos, that is a great idea.  But I would want to wait until everything is stable enough.  Development is still rapid and I love the freedom to fix mistakes and improve (break) APIs.  The project code is hosted at Launchpad so I expect to pursue the Ubuntu repo path later on.

Re: business plan.  The plan is to provide a permanently open source core (see Open-Core Licensing ([http://blogs.the451group.com/opensource/2008/09/01/andrew-lampitt-defines-open-core-licensing/](http://blogs.the451group.com/opensource/2008/09/01/andrew-lampitt-defines-open-core-licensing/)). This core may even expand over time as my proprietary addons (none at present) move into the core and more advanced add-ons are created.  The independence of the underlying Python code from the GUI is the key to allowing report automation.  The fact that everything is displayed in HTML, even internally, implies corporate intranet and internet possibilities, which is probably where an income stream can be found.

Having said all that, I am motivated by two other things.

1) To make a product that I want to use myself in my work as an analyst.  Unlike proprietary products I have worked with before, I love the ability to fix any problems I find and make my working experience more pleasant.  I smoothed off several rough edges in the latest 0.8.4 release for example ([https://sourceforge.net/projects/sofastatistics/files/sofastatistics/sofa_0.8.4-1_all.deb/download](https://sourceforge.net/projects/sofastatistics/files/sofastatistics/sofa_0.8.4-1_all.deb/download)) - see if you notice any differences. You can cheat by reading [http://www.sofastatistics.com/blog/?p=97](http://www.sofastatistics.com/blog/?p=97)

2) To provide a gift to the world (Open Source 101).  I would be delighted if school students, business analysts etc in places as far flung as Ghana, Scotland, Bolivia, Germany etc were using my program and benefiting from it.

If you find any bugs, please report them on the SOFA Statistics Launchpad site. The more the merrier.  Details here - [http://www.sofastatistics.com/blog/?p=92](http://www.sofastatistics.com/blog/?p=92)

---

### Post by grantbuntu on 2009-07-31
> **rewyllys said:**
> Very interesting and impressive!  That's my reaction to your video demonstration, which I just watched.

I taught basic statistics at the university level for 31 years till retiring 6 years ago.  I'd have loved to have SOFA Statistics for my students (and myself) to use; and I'll be recommending it to some colleagues who are still actively teaching and researching.

@rewyllys - I would really appreciate input from people with your sort of background as I further develop SOFA Statistics.  I will set up a project-specific bulletin board once the project gains a little more momentum. The area I am most keen on extending will seek to address two issues:

1) which test should I use?  Is my data normal enough?  What does normal even mean?  Can the program show me at the point of my decision making based on my actual data with mini-charts, quick subsidiary analyses, and other helpful visualisations?  This is an area I will want lots of feedback on.  The technology is readily available to do wonderful things in this area :-).

2) what do the results mean?  Statistical significance is one factor, but what about the oomph of the effect?  Is the difference being measured clinically/ economically/ etc significant. A statistics program can't tell me the answer but it can encourage me to ask the question and provide supporting information beyond p values etc. What are some of the next steps I should take e.g. Pearson's Chi Square was significant but which interactions were important?

Finally, if you like the program, please feel free to review it at [https://sourceforge.net/projects/sofastatistics/](https://sourceforge.net/projects/sofastatistics/).  There are no reviews yet and that would be really good.  NB to test the best available release (0.8.4) which I released last night [http://www.sofastatistics.com/downloads.php](http://www.sofastatistics.com/downloads.php).

---

### Post by grantbuntu on 2009-07-31
@ugm6hr - I am hoping to use Raphael ([http://raphaeljs.com/](http://raphaeljs.com/)) for the output charting but a lot depends on what is available and when.  See [http://groups.google.com/group/raphaeljs/browse_thread/thread/ef1341b0ad26de16](http://groups.google.com/group/raphaeljs/browse_thread/thread/ef1341b0ad26de16)

Re: netbooks, I understand the issue but it may take me a while to resolve it.  I am sometimes trying to cram a lot into one screen.

---

### Post by neobux on 2009-08-01
If you want a good answer to this question, you need to be specific about your needs. Be sure to tell which of the following factors are important to you:   

[LIST=1]
[*]Ease of learning
[*]Quality of help files
[*]Extensibility/programmability
[*]Data entry and validation
[*]Data manipulation
[/LIST]

---

### Post by ahmatti on 2009-08-03
> **grantbuntu said:**
> @ugm6hr - I am hoping to use Raphael ([http://raphaeljs.com/](http://raphaeljs.com/)) for the output charting but a lot depends on what is available and when.  See [http://groups.google.com/group/raphaeljs/browse_thread/thread/ef1341b0ad26de16](http://groups.google.com/group/raphaeljs/browse_thread/thread/ef1341b0ad26de16)


Just curious: Any specific reason for not using matplotlib [http://matplotlib.sourceforge.net/?](http://matplotlib.sourceforge.net/?)

---

### Post by grantbuntu on 2009-08-03
At this stage, I intend to use Matplotlib for the auxiliary graphing and RaphaelJS for the final output graphing.

By auxiliary graphing, I mean all the smaller charts and visualisations that help a user select the appropriate test.  E.g. the charts showing if a distribution if adequately normal.

By output graphing I mean presentation-ready output e.g. the findings.  The emphasis for final output is on bling or eye candy, albeit not at the expense of accuracy.

In [Candy, Community, Comfort, Credibility etc]("http://www.sofastatistics.com/blog/?p=64") I explain some of the philosophy behind SOFA Statistics and the niche I am aiming for.

---

### Post by mdshaver on 2009-08-12
Sofa does look very nice but may not be sufficient for many users desiring more complex analyses. On the other hand, R, may present too large of a learning curve for some. In these instances, a nice SPSS alternative is OpenStat. 

[http://statpages.org/miller/openstat/](http://statpages.org/miller/openstat/)

It's pretty much updated monthly and has a huge array of statistical procedures with ample documentation available. I believe it is maintained by one man but it is very nice. However, it does need to be installed through Wine to use current versions. But it does run perfectly through Wine. The graphs are not very pretty but other software would be better suited for that function anyways.

---

### Post by sdbrogan on 2009-08-13
Last time I checked, OpenStat's regression routine gave wrong answers on some reference data from NIST.
[http://ubuntuforums.org/showpost.php?p=7195429&postcount=15](http://ubuntuforums.org/showpost.php?p=7195429&postcount=15)
I think R is pretty much the only fully-fledged, general-purpose, free statistical software available at the moment.

---

### Post by gunksta on 2009-08-14
I would really like to see SOFA and PSPP both grow into mature statistical environments for Linux. 

R, SOFA and PSPP are each unique projects and will make Linux an even _more_ appropriate environment for research and data analysis.

I would love to try out SOFA right now, but it looks like I would have to upgrade wxwidgets. I run a couple of programs that depend on this toolkit. I tend to be a little gun-shy about upgrading base level libraries and toolkits. I'll compile and install bleeding edge programs. If they break, so be it. But, I don't like to mess with the lower-level stuff unless it is absolutely necessary.

Right now I'm waiting for Karmic to get stable enough to justify an upgrade. Once I do that, I think I'll be able to compile SOFA with the default wxwidgets (correct me if I am wrong on this). I would love to help get SOFA into the Ubuntu repos in time for Karmic+1. With the current rate of improvement, SOFA should an advanced tool by then. If I can find the time to help,  I might even get to learn more Python!

---

### Post by samden on 2009-09-13
There's a new plugin for running R from Gedit now, really simple and functional. I'd recommend you check it out if you use R and want a basic GUI that does exactly what you want cleanly, without having to learn another piece of software (as you can continue to use Gedit).
[http://sourceforge.net/projects/rgedit/]("http://sourceforge.net/projects/rgedit/")

---

### Post by KegHead on 2010-07-16
Hi!

Any simple to use stat pkg for a novice?

Thanks!

KegHead

---

### Post by earlycj5 on 2010-07-16
> **KegHead said:**
> Hi!

Any simple to use stat pkg for a novice?

Thanks!

KegHead

Well, even though this is a double post, I'll reply. I'd suggest reading through this thread where various suggestions have been bandied about and picking one.

SOFA would be near the top of my list...

---

### Post by KegHead on 2010-07-17
thanks1

I'll try the pkg.

KegHead

---

### Post by Iurie on 2011-06-21
Undoubtedly, the best statistical software is R! In addition, it's free!
[How to install R and some grafical user interfaces for R (R, JGR and Deducer) in Ubuntu/Linux]("http://realshared.com/2011/how-to-install-r-jgr-and-deducer-in-ubuntu-10-04.htm").
[An Ubuntu/Linux live CD with R and some grafical user interfaces for R (R Commander, JGR, Deducer, Rattle, RKWard, RStudio) preinstalled]("http://realshared.com/2011/statistical-r-ubuntu-live-cd.htm").

---

