---
title: "Install SAS on Ubuntu"
date: 2007-12-15
forum: Education &amp; Science
---

### Post by jcfisher on 2007-12-15
Has anyone successfully installed SAS on Ubuntu?  Thus far, I've tried installing the *nix version but when I try to run it, it gives an error message related to the WORK library, and fails.

I know R is a great program.  Unfortunately, the data sets I have / need are SAS files, and I have no desire to figure out how to convert them -- SAS answers only, please.

Thanks!

Jake Fisher
St. Louis, MO

---

### Post by jcfisher on 2007-12-16
As is so often the case, I've answered my own question.  SAS doesn't automatically define a directory to use as the "WORK" library, so you have to define it yourself when you start the program.
```
$ sas -work /tmp
```
There's [more]("http://support.sas.com/kb/17/783.html") about this on the SAS support site.

I feel a bit silly posting, but hopefully this helps someone.

---

### Post by earlycj5 on 2007-12-17
I wouldn't say it's silly posting at all.

Thank you for posting that.  I can't tell you how many times I've searched for an answer, found some forum thread that has a question but no answer just a "I fixed it".

Thanks for sharing.

---

### Post by firefeather on 2007-12-17
Couple of people tried it at my school and that's probably as far as we got, if that far at all. SAS is pretty much the only real thing keeping me using Windows, so if your fix works, I'll be pretty excited!

> **jcfisher said:**
> Has anyone successfully installed SAS on Ubuntu?  Thus far, I've tried installing the *nix version but when I try to run it, it gives an error message related to the WORK library, and fails.

---

### Post by pyronaut on 2007-12-22
well .. i  have also had success install SPLUS under linux using wine. It was fu for a while although i am back to R and emacs  :)

---

### Post by jcfisher on 2007-12-23
Glad solving my own problem could be of some use.  Please note that if you do decide to install SAS, the SAS Foundation distributes a copy for *nix, which is much easier to install than trying to use the windows version and wine.

---

### Post by euler_fan on 2007-12-23
This is pretty cool to know. Now if I suddenly have to go back to SAS I won't have to scrounge up windows to do it.

On a side note, there's a package in CRAN called foreign that will convert SAS data files for use in R. Not sure if it will do the exact formats you have, but it's worth a look.

---

### Post by dirkjot on 2008-01-02
Another option, which I am using, is to install qemu and set 4Gig aside for a windows image on your harddisk.  I installed win2000 within that image and it runs SAS like a charm.  The win2000 sessions runs in a window and writes its SAS input and output files to my normal user directory via samba file sharing.  

HTH,
Dirk

---

### Post by wwvierg on 2008-01-03
> **dirkjot said:**
> Another option, which I am using, is to install qemu and set 4Gig aside for a windows image on your harddisk.  I installed win2000 within that image and it runs SAS like a charm.  The win2000 sessions runs in a window and writes its SAS input and output files to my normal user directory via samba file sharing.  

HTH,
Dirk

hi dirk:

i've been coding SAS since '75 and am about to try getting wet w/ Linux but didn't want to go the RHEL or SUSE route, hence my interest in Ubuntu and/or Debian

am planning on doing something similar, i.e., run x64 linux (and 64-bit v9.2 SAS) and do XP via a VM and run 32-bit SAS from there .. as such, can you shed a bit more light (general terms) on how you use Samba from with in your VM?

thanks in advance

bill, from sacramento

out

---

### Post by wwvierg on 2008-01-03
> **jcfisher said:**
> Glad solving my own problem could be of some use.  Please note that if you do decide to install SAS, the SAS Foundation distributes a copy for *nix, which is much easier to install than trying to use the windows version and wine.

hi jc:

other than the Temp directory issue, did the SAS install proper present any problems?

also - you mention the *nix version of SAS,  can you elaborate (i.e., there are Unix versions and Linux versions) ... i.e., which did you use?

thanks

bill, from sacramento

out

---

### Post by Zimmer on 2008-01-03
> **wwvierg said:**
> hi jc:

other than the Temp directory issue, did the SAS install proper present any problems?

also - you mention the *nix version of SAS,  can you elaborate (i.e., there are Unix versions and Linux versions) ... i.e., which did you use?

thanks

bill, from sacramento

out

I second that. It was interesting to see the Linux versions listed. I have been retired 4 years now and it is amazing to see how SAS has progressed in that time, more banking specific modules...
I bet the Linux versions are'nt 'free' to download and use, though.... pity..

---

### Post by earlycj5 on 2008-01-04
> **Zimmer said:**
> 
I bet the Linux versions are'nt 'free' to download and use, though.... pity..

Hohoho, nope!

We managed to get the university and SAS to agree to let us have our copy on the University's Site License agreement.  I'd hate to think of the cost if one were to purchase themselves.

---

### Post by jcfisher on 2008-01-11
Bill and others,

First of all, heavens no, you can't freely download SAS.  There seems to be a version of SAS specifically for Linux PCs and servers, which is the copy I requested from the university's software licensing division.

Apart from the one hitch mentioned at the beginning of this thread, I had no trouble installing SAS on my PC.  The installer is command-line based, but is fairly user-friendly and shouldn't give you any trouble.

Hope that helps,

Jake

---

### Post by Zimmer on 2008-01-12
> **jcfisher said:**
> Bill and others,


Apart from the one hitch mentioned at the beginning of this thread, I had no trouble installing SAS on my PC.  The installer is command-line based, but is fairly user-friendly and shouldn't give you any trouble.

Hope that helps,

Jake
BTW which release are you using?

---

### Post by jcfisher on 2008-01-14
9.1.3

---

### Post by useResa on 2008-01-29
I also run SAS 9.1.3 SP4 on Ubuntu Gutsy (see attachment). But until know I have only SAS Foundation installed in Linux.

In a VM (in VMware Server) I run WinXP in which I have the entire BI Server environment running. 

I also am curious how you share your datasets using Samba. When doing so are you not faced with the fact that this is cross platform (I normally use PROC CPORT and PROC CIMPORT to transfer datasets cross platform).

---

### Post by Zimmer on 2008-02-01
I would think you would need the SAS ODBC drivers to access the remote data.

If that is not successful you could experiment creating .db .dbf files of the sets which the remote clients could probably see across the network .... have no SAS    :(     so  I am unable to experiment for you. 
I do remember having to create data files on the VAX in SAS and then sending certain  flat files to a Win server for another dept who had PC SAS . They had to create the SAS datasets from the flat file...

What you do depends  on what you mean by  'sharing' the SAS datasets.  Sharing access via SAS clients or allowing clients to download the datasets ? 
The former should be accomodated by SAS products, if you can afford them ;)

---

### Post by useResa on 2008-02-01
> **Zimmer said:**
> I would think you would need the SAS ODBC drivers to access the remote data.

If that is not successful you could experiment creating .db .dbf files of the sets which the remote clients could probably see across the network .... have no SAS    :(     so  I am unable to experiment for you. 
I do remember having to create data files on the VAX in SAS and then sending certain  flat files to a Win server for another dept who had PC SAS . They had to create the SAS datasets from the flat file...
Not necessarily ... you can have SAS access files on other platforms in several ways, provided you have a SAS server running on both platforms.
But maybe this is too much of SAS on a Ubuntu Forum ;)


> **Zimmer said:**
>  What you do depends  on what you mean by  'sharing' the SAS datasets.  Sharing access via SAS clients or allowing clients to download the datasets ? 
The former should be accomodated by SAS products, if you can afford them ;)The main issue is that you can run into issues when you are trying to display a SAS dataset that is created on a Windows platform and try to open this in a Linux environment (when you simply copy the file from one location to the other).

Therefore I was curious how the sharing worked.

---

### Post by jhend2007 on 2008-06-25
Not silly at all. Thanks for giving your simple answer.

sas -work /tmp

solved my Linux SAS problem too!

You should probably recommend that this option be permanently added to 

!SASROOT/sasv9.cfg 

if possible.

Thanks again!

:guitar:

---

### Post by scholzilla on 2008-08-27
Forgive my ignorance, but my U offers SAS for windows (not linux) at a deep discount to students. I'd like to take advantage of this, but I don't/won't have windows. Do the install disks for the windows version work within ubuntu (8.04)? Is it as simple as putting them in the drive and following the cues or is there some trick to getting this to work?

thanks

---

### Post by useResa on 2008-08-27
> **scholzilla said:**
> Forgive my ignorance, but my U offers SAS for windows (not linux) at a deep discount to students. I'd like to take advantage of this, but I don't/won't have windows. Do the install disks for the windows version work within ubuntu (8.04)? Is it as simple as putting them in the drive and following the cues or is there some trick to getting this to work?
thanksNo sorry ... the Windows disks won't work in Linux.
There are specific Linux installation disks.
 
BTW: Also the license code (setinit) is platform dependend. So running a Windows license on a Linux platform will also not work.

---

### Post by mbw on 2008-09-05
Assuming you have paid for SAS and have a valid license that gets you in to their download center.... If you can get your SAS for Linux entitlement downloaded into a "SAS Software Depot" folder on a windows machine, then copy that over to an UBUNTU box, you can make it work.

Some notes for Ubuntu HH 8.04 Hardy Heron:

-Copied sas software depot over to Ubuntu

-Problems with Dash shell... make sure BASH shell is the default:

                                                                               
root@union:/bin# ls -ls /bin/sh
                            
0 lrwxrwxrwx 1 root root 4 2008-08-29 06:58 /bin/sh -> bash                    
                                                                               
- Make sure the FULL PATH of the location of your SAS install files includes NO SPACES!!!!

(This means that if you copy over the "SAS Software Depot" folder from Windows after you download it with the windows-only-SAS-download tools (Thanks, SAS) - you'll need to rename that directory to "SAS_SW_DEP" or something without spaces)

For some reason, the execute "X" bit isnt getting set on scripts that are generated....   so often I had to manually set the "x" bit (chmod +x scriptname) and "retry" the install or hand-run the scripts.

for instance, in the last lines of the setup.sh script in the root of the sw depot folder, I added the chmod +x line

# Run the command
chmod +x "$templocation/$launch" 

exec "$templocation/$launch" "$@" -startuplocation "$startuplocation" -templocat
ion "$templocation" 1>> "$logfile" 2>&1

exit $?


man this is a mess.....   

I got it working tho.  

-Matt

---

### Post by useResa on 2008-09-08
> **mbw said:**
> Assuming you have paid for SAS and have a valid license that gets you in to their download center.... If you can get your SAS for Linux entitlement downloaded into a "SAS Software Depot" folder on a windows machine, then copy that over to an UBUNTU box, you can make it work.What SAS Version are you talking about here? I thought that only as of release 9.2 the software has become available from the download center.

BTW: Thanks for posting your experiences.

---

### Post by AlfredoR on 2008-09-17
Hi everyone. I would really appreciate any help in regards
to installing SAS 9.2 in Ubuntu. I have installed the SAS deployment in
my home directory and once I ran the deployment wizard and select install application it starts running but when is installing the SAS foundation 
it gives me this error message not allowing me to continue I would appreciate any help on this. 

/bin/sh: Illegal option -p

---

### Post by Zimmer on 2008-09-17
I suggest a good long read of post #22 above ...  and trying following the tips there...

---

### Post by OldDirtyTurtle on 2008-09-22
Well, I ordered the DVD media and license for SAS 9.2 64-bit on Linux.  I should have the discs in a few days and I'll install as soon as my new laptop is ordered and shipped (come on System 76 - let's go on the Serval!).

Will report back here with details after running a few archived SAS codes.

:guitar:

---

### Post by useResa on 2008-09-23
> **OldDirtyTurtle said:**
> Will report back here with details after running a few archived SAS codes.Please do. Looking forward to feedback about the installation of SAS 9.2 in Linux

---

### Post by Rorke on 2008-10-09
I haven't used SAS since on an IBM mainframe in 1996. I really want to get into using it commercially again. Can anyone recommend a (free) method of installing a demo or tutorial on my Ubuntu box? Or is there an Open Source equivalent that the experience of which would stand up in a job interview?
Also, is SPSS better to learn - I've never used it.

---

### Post by scholzilla on 2008-10-09
I would recommend using R instead. It's free, open source, and powerful. I'm only learning SAS because I have to. If you google "R" it's the first thing that comes up.

---

### Post by Rorke on 2008-10-10
OK - I'd found 'R'.
I still need another look at it, but I got this:
'
W: Failed to fetch [http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz](http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz)  301 Moved Permanently
'

---

### Post by scholzilla on 2008-10-10
you might try another mirror for downloading. There are about a hundred.

---

### Post by akniss on 2008-10-12
> **Rorke said:**
> OK - I'd found 'R'.
I still need another look at it, but I got this:
'
W: Failed to fetch [http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz](http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz)  301 Moved Permanently
'

Just use the default Ubuntu repositories.  R is in the repos.
```
sudo apt-get install r-recommended
```

---

### Post by Prince_Andrei on 2008-10-16
Also, consider downloading the R Commander package. It is in Synaptic as r-cran-rcmdr. Once you launch R from the terminal, type "library(Rcmdr)" to load it. It's a GUI that will help you make the transition to R. You can see the script generated from the menu functions and go from there.

I, too, would like an update on how the install went with the new SAS version on 64-bit Ubuntu. There's a reasonable chance I may have to start using SAS as well.

---

### Post by sarathannapareddy on 2008-10-23
SAS Interview Q&A and Trial resumes:
SAS Interview Questions and Answers:Part1 (Behavioral Type Interview Questions) 
[http://studysas.blogspot.com/2008/08/sas-interview-questions-and.html](http://studysas.blogspot.com/2008/08/sas-interview-questions-and.html)
SAS Interview Questions: General(Part-2) 
[http://studysas.blogspot.com/2008/08/sas-interview-questions-generalpart-2.html](http://studysas.blogspot.com/2008/08/sas-interview-questions-generalpart-2.html)

SAS interview questions:Macros

[http://studysas.blogspot.com/2008/09/sas-interview-questionsmacros.html](http://studysas.blogspot.com/2008/09/sas-interview-questionsmacros.html)

SAS interview Q & A: PROC SQl and SAS GRAPH and ODS 
[http://studysas.blogspot.com/2008/09/sas-interview-q-proc-sql-and-sas-graph.html](http://studysas.blogspot.com/2008/09/sas-interview-q-proc-sql-and-sas-graph.html)

SAS Interview Questions:Base SAS 
[http://studysas.blogspot.com/2008/09/sas-interview-questionsbase-sas.html](http://studysas.blogspot.com/2008/09/sas-interview-questionsbase-sas.html)
SAS Interview Questions & Answers:Clinical trials 
[http://studysas.blogspot.com/2008/09/sas-interview-questions-answersclinical.html](http://studysas.blogspot.com/2008/09/sas-interview-questions-answersclinical.html)
SAS Interview Questions and Answers: CDISC,SDTM,ADAM etc 
[http://studysas.blogspot.com/2008/09/sas-interview-questions-and-answers.html](http://studysas.blogspot.com/2008/09/sas-interview-questions-and-answers.html)

What you should know about the ISS/ISE (ISR)
[http://studysas.blogspot.com/2008/09/what-you-should-know-about-issise-isr.html](http://studysas.blogspot.com/2008/09/what-you-should-know-about-issise-isr.html)

SAS Resumes 
[http://studysas.blogspot.com/2008/08/learn-sas-online.html](http://studysas.blogspot.com/2008/08/learn-sas-online.html)


SAS CLINICAL:
SAS in clinical trials:
[http://studysas.blogspot.com/2008/09/sas-in-clinical-trials.html](http://studysas.blogspot.com/2008/09/sas-in-clinical-trials.html)
CDISC [http://studysas.blogspot.com/2008/08/cdisc.html](http://studysas.blogspot.com/2008/08/cdisc.html)
CDISC and SAS 
[http://studysas.blogspot.com/2008/08/cdisc-and-sas-why-is-adoption-of-cdisc.html](http://studysas.blogspot.com/2008/08/cdisc-and-sas-why-is-adoption-of-cdisc.html)
List of the Domains (datasets) and the variables in it: (CDISC perspective) 
[http://studysas.blogspot.com/2008/08/list-of-variables-in-each-dataset.html](http://studysas.blogspot.com/2008/08/list-of-variables-in-each-dataset.html)

Contents of Clinical Study Report
[http://studysas.blogspot.com/2008/08/contents-of-clinical-study-report.html](http://studysas.blogspot.com/2008/08/contents-of-clinical-study-report.html)

Contents of Protocol of Clinical Trial

[http://studysas.blogspot.com/2008/08/contents-of-protocol-of-clinical-trial.html](http://studysas.blogspot.com/2008/08/contents-of-protocol-of-clinical-trial.html)

Contents of Statistical Analysis Plan (SAP)
[http://studysas.blogspot.com/2008/08/contents-of-statistical-analysis-plan.html](http://studysas.blogspot.com/2008/08/contents-of-statistical-analysis-plan.html)
TLF samples [http://studysas.blogspot.com/2008/08/tlf-samples.html](http://studysas.blogspot.com/2008/08/tlf-samples.html)
Different phases I-IV of a clinical trial 
[http://studysas.blogspot.com/2008/08/different-phases-i-iv-of-clinical-trial.html](http://studysas.blogspot.com/2008/08/different-phases-i-iv-of-clinical-trial.html)
LEARN SAS:
WHY SAS 
[http://studysas.blogspot.com/2008/08/why-sas.html](http://studysas.blogspot.com/2008/08/why-sas.html)
SAS Tutorials (Video): Free 
[http://studysas.blogspot.com/2008/08/sas-tutorials-video-free.html](http://studysas.blogspot.com/2008/08/sas-tutorials-video-free.html)
SAS free study tutorials
[http://studysas.blogspot.com/2008/09/sas-free-study-tutorials.html](http://studysas.blogspot.com/2008/09/sas-free-study-tutorials.html)
Online SAS study materials:
[http://studysas.blogspot.com/2008/09/online-study-materials.html](http://studysas.blogspot.com/2008/09/online-study-materials.html)
BASIC SAS COMMANDS 
[http://studysas.blogspot.com/2008/08/basic-sas-commands.html](http://studysas.blogspot.com/2008/08/basic-sas-commands.html)
Basic Statistical Tests Using SAS 
[http://studysas.blogspot.com/2008/08/basic-statistical-tests-using-sas.html](http://studysas.blogspot.com/2008/08/basic-statistical-tests-using-sas.html)

Learn SAS in 6 weeks:
[http://studysas.blogspot.com/2008/09/learn-sas-within-7-weeks.html](http://studysas.blogspot.com/2008/09/learn-sas-within-7-weeks.html)
POWER POINT Presentations on SAS by WIPRO/COGNIZANT,GE Capitol & SAS   [http://studysas.blogspot.com/2008/09/power-point-presentations-on-sas-by.html](http://studysas.blogspot.com/2008/09/power-point-presentations-on-sas-by.html)

FREE DOWNLOAD:
SAS ebooks: free download 
[http://studysas.blogspot.com/2008/08/sas.html](http://studysas.blogspot.com/2008/08/sas.html)



SAS Tips and Techniques:
SAS Tips and Trics 
[http://studysas.blogspot.com/2008/08/sas-tips-and-tricks-part1-httpwww4.html](http://studysas.blogspot.com/2008/08/sas-tips-and-tricks-part1-httpwww4.html)
Ten Great Reasons to Learn SQL Procedure 
[http://studysas.blogspot.com/2008/08/ten-great-reasons-to-learn-sql.html](http://studysas.blogspot.com/2008/08/ten-great-reasons-to-learn-sql.html)
SAS UNIX Commands: 
[http://studysas.blogspot.com/2008/09/sas-unix-commands.html](http://studysas.blogspot.com/2008/09/sas-unix-commands.html)

CLASS Statement
[http://studysas.blogspot.com/2008/08/class-statement.html](http://studysas.blogspot.com/2008/08/class-statement.html)
Proc SQL VS Datastep: SAS syntax
[http://studysas.blogspot.com/2008/08/proc-sql-vs-datastep-sas-syntax.html](http://studysas.blogspot.com/2008/08/proc-sql-vs-datastep-sas-syntax.html)
SAS Online Documentation: 
[http://studysas.blogspot.com/2008/08/sas-online-documentation.html](http://studysas.blogspot.com/2008/08/sas-online-documentation.html)

---

### Post by Relysis on 2008-10-26
I'm having some problems with SAS linux as well.  I have a copy of SAS 9.1.3 for linux.  I followed all the installation instructions using my license file on Ubuntu 8.04.  It installed fine with no errors.  However, when I try to run it, a white box briefly appears and then disappears.  Every time I try to run it, this window just blinks on the screen once and then nothing happens.  The installation said I have no errors, so I was thinking maybe it's a driver thing?  I'm using fglrx with an ATI mobility x300.  It works fine for everything else, I'm just clueless as to how to proceed... Any ideas?  Thanks ~

---

### Post by mali2297 on 2008-10-27
> **Relysis said:**
> I'm having some problems with SAS linux as well.  I have a copy of SAS 9.1.3 for linux.  I followed all the installation instructions using my license file on Ubuntu 8.04.  It installed fine with no errors.  However, when I try to run it, a white box briefly appears and then disappears.  Every time I try to run it, this window just blinks on the screen once and then nothing happens.  The installation said I have no errors, so I was thinking maybe it's a driver thing?  I'm using fglrx with an ATI mobility x300.  It works fine for everything else, I'm just clueless as to how to proceed... Any ideas?  Thanks ~

Have you tried disabling the desktop effects?

---

### Post by useResa on 2008-10-27
> **mali2297 said:**
> Have you tried disabling the desktop effects?IMHO SAS should also run with Desktop Effects enabled (see attachment) although I have to say that I run SAS on a laptop with an nVidia graphics card.

How do you start SAS? Do you start it from terminal?
If so, don't you get any error messages?

---

### Post by knuno on 2008-11-06
More on instalation problems:
I am trying to install SAS 9.2 on a laptop with Kubuntu 8.10 and KDE 4.1. I am running the install script (setup.sh) from the CD. It launches a graphical installer and installs a SAS version of Java. But when it proceeds to installing SAS Foundation it stops with a window asking me if I want to proceed with other modules, stop the installation or retry. If I want to retry it says that I'm supposed to get more error information and an interactive installation. But I don't, it only pops up with the same message. There is no error messages in any of the system logs, and there is no SAS install log, only a /usr/local/SAS/InstallMisc/InstallLogs directory.
I am running the install as a sasroot user, and it is able to create the /usr/local/SAS directories and some files.
I must add that I have been able to install SAS without problems on an old 512 MB PC with openSUSE. But my university "prefers" Ubuntu...

Knut

---

### Post by Relysis on 2008-11-08
Sorry for being so late in my reply.  I can't even run it in the terminal.  If I run the command 'sas' it says "command not found".  I cd to the install directory (~/sas/sas_9.1) and still nothing.  If I double click on it and select run, nothing happens.  If I select run in terminal, the terminal pops up for less than a second and disappears again.  I keep desktop effects disabled because the fglrx support is weak.  This might be a noob problem of not understanding how to run a program, but I haven't had a problem before.  Thanks ~

---

### Post by mali2297 on 2008-11-09
> **Relysis said:**
> Sorry for being so late in my reply.  I can't even run it in the terminal.  If I run the command 'sas' it says "command not found".  I cd to the install directory (~/sas/sas_9.1) and still nothing.  If I double click on it and select run, nothing happens.  If I select run in terminal, the terminal pops up for less than a second and disappears again.  I keep desktop effects disabled because the fglrx support is weak.  This might be a noob problem of not understanding how to run a program, but I haven't had a problem before.  Thanks ~

If the executable is ~/sas/sas_9.1/executable, then you can launch it from the terminal with the command
```

~/sas/sas_9.1/executable

```

---

### Post by 081103jk on 2008-11-10
&#19978;&#38754;&#25105;&#20204;&#24050;&#32463;&#31616;&#21333;&#35828;&#20102;DVD&#177;R[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#65295;RW&#30340;&#21508;&#33258;&#29305;&#28857;[**&#20809;&#30424;&#21046;&#20316;**](http://www.itd9.com/index.asp)&#65292;&#23545;&#20110;&#26222;&#36890;&#29992;&#25143;&#32780;&#35328;[**&#20809;&#30424;&#21051;&#24405;**](http://www.itd9.com/gpkl.asp)&#65292;&#36873;&#25321;&#29289;&#32654;&#20215;&#24265;&#30340;DVD-R&#27604;&#36739;&#21512;&#36866;&#65292;DVD-R&#20809;&#30424;&#19981;&#20165;&#33021;&#22815;&#20445;&#23384;&#26222;&#36890;&#25968;&#25454;&#36164;&#26009;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#65292;&#32780;&#19988;&#23427;&#21644;&#23478;&#29992;DVD&#26426;&#20860;&#23481;&#36739;&#22909;&#65292;&#22240;&#27492;&#38750;&#24120;&#36866;&#21512;&#21051;&#24405;DVD&#24433;&#30879;&#12289;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#30005;&#23376;&#29031;&#29255;&#31561;&#22810;&#23186;&#20307;&#36164;&#26009;&#65307;&#23545;&#20110;&#38656;&#35201;&#38271;&#26102;&#38388;&#25968;&#25454;&#20445;&#23384;&#30340;&#26379;&#21451;&#26469;&#35828;&#65292;DVD+R&#26159;&#19981;&#38169;&#30340;&#36873;&#25321;&#65292;DVD+R&#20809;&#30424;&#25317;&#26377;&#26356;&#22909;&#30340;&#31283;&#23450;&#24615;&#65292;&#21644;DVD&#21051;&#24405;&#26426;&#30340;&#20860;&#23481;&#24615;&#20063;&#19981;&#38169;&#65292;&#24635;&#20307;&#21051;&#24405;&#36136;&#37327;&#35201;&#22909;&#20110;DVD-R

---

### Post by useResa on 2008-11-10
> **Relysis said:**
> Sorry for being so late in my reply. I can't even run it in the terminal. If I run the command 'sas' it says "command not found". I cd to the install directory (~/sas/sas_9.1) and still nothing. If I double click on it and select run, nothing happens. If I select run in terminal, the terminal pops up for less than a second and disappears again. I keep desktop effects disabled because the fglrx support is weak. This might be a noob problem of not understanding how to run a program, but I haven't had a problem before. Thanks ~
 
First just for confirmation: Did you override the default installation directory?
My SAS 9.1 installation was placed in /usr/local/SAS/SAS_9.1.
Additionally all directories in my situation state SAS in uppercase while yours seem to be in lowercase. Is that indeed the situation?
 
To prevent confusion I will use <SAS_dir> in the commands below.
Which in your case seems to be ~/sas/sas_9.1 and in my case is /usr/local/SAS/SAS_9.1. Please enter the appropriate directory for your situation.
 
If you like to start SAS from a terminal you first need to go into the directory where you have installed SAS
```
cd <SAS_dir>
```
From there you can start SAS simply by typing
```
sas
```
 
If you like to be able to start SAS with the command "sas" you can achieve that with the following command
```
sudo ln -s <SAS/dir>/sas /usr/bin/sas
```
With this command a symbolic link is created which will allow you to start SAS from any directory with the command "sas" (without quotes).
Personally I have created a link so I can start SAS 9.1 with the command "sas91" to distinguish my personal command from the "official" command. If you like to do so as well, issue the following command instead of the previous one.
```
sudo ln -s <SAS/dir>/sas /usr/bin/sas91
```
 
I hope this information helps you to start SAS from a terminal and determine if you get any error messages.

---

### Post by OldDirtyTurtle on 2008-11-21
Well folks - I'm at a stand still.

I've been trying over the course of a couple of days to install SAS 9.2 (Linux 64-bit) from the DVD on my laptop with Intrepid 64-bit.  No go.  Here's what I've tried:

1.  Install from DVD by clicking setup.sh - failed at SAS Foundation install.
2.  Install from terminal by calling setup.sh with bash - same result.
3.  Change bash to default shell with the chsh command, install by calling setup.sh in terminal - same result.

Any ideas?  I've got to get this going.  I'm getting behind.  To be honest - I'm not making heads or tails of Matt's post (#22).

---

### Post by s3anc0l8 on 2008-12-09
That's too bad, OldDirtyTurtle.  I have been hopeful that 9.2 x64 would work on Intrepid.

Let us know if anything changes.

---

### Post by OldDirtyTurtle on 2008-12-10
Oh...  It's not over yet.  ](*,)

---

### Post by useResa on 2008-12-10
> **OldDirtyTurtle said:**
>  To be honest - I'm not making heads or tails of Matt's post (#22).
Based on this statement and your last reaction 
> **OldDirtyTurtle said:**
> Oh...  It's not over yet.  ](*,)
Let me try to explain what I make of Matt's post.

First thing he indicates that the bash should be default.
The way to check this is by opening a terminal and give the command
```
ls -ls /bin/sh
```The result should look similar as to what he indicates below this command
```
lrwxrwxrwx 1 root root 4 2008-08-29 06:58 /bin/sh -> bash                    
```Next he indicates that the path to where the software depot is copied to should include NO SPACES.

The last thing he indicates is that it seemed that execution rights may not be properly set for all script (.sh) files. The result of this being that he had to manually set the execution rights and run the scripts by hand.
The way to add execution rights to a file is done with the chmod command as he indicates
```
chmod +x /path/to/scriptfile
```Additionally he has added a line to setup.sh file, which also adds execution rights.
From my understanding the initial content was
```
# Run the command

exec "$templocation/$launch" "$@" -startuplocation "$startuplocation" -templocation "$templocation" 1>> "$logfile" 2>&1

exit $?
```What he has done is added the chmod +x command so it looks like
```
# Run the command
chmod +x "$templocation/$launch" 

exec "$templocation/$launch" "$@" -startuplocation "$startuplocation" -templocation "$templocation" 1>> "$logfile" 2>&1

exit $?
```Maybe this will help you continue your installation.

If it does not help you further, maybe you could try to PM Matt for hints?

---

### Post by OldDirtyTurtle on 2009-01-03
So I finally got SAS 9.2 Linux 64-bit installed.  No hiccups at all after a friend of mine did some tinkering with it under Intrepid.  It was indeed a bash/dash issue.

Now to run SAS.  Can't seem to get it going.  I've tried the suggestions here but still no dice.  I've tried in both the terminal and by browsing and selecting 'run in terminal' but it still won't open.  Like Relysis before me - there's a terminal 'flash' then nothing.  

This is frustrating - I really don't want to resort to running SAS in VirtualBox full time (like I am now).

---

### Post by useResa on 2009-01-04
> **OldDirtyTurtle said:**
> Now to run SAS.  Can't seem to get it going.  I've tried the suggestions here but still no dice.  I've tried in the terminalWhen you start it in terminal, what command do you give?
Do you give the command in the SAS installation directory?
If you run it, do you get any error messages?

---

### Post by OldDirtyTurtle on 2009-01-04
SAS installed by default at /usr/local/SAS/.

From the terminal, I've run 'sas' as the command at /usr/local/SAS/SASFoundation/9.2/

and I've run 'sas' the command at /usr/local/SAS/SASFoundation/9.2/sasexe/

In both cases - the reply is ```
bash: sas: command not found
```

If I browse to these locations of the 'sas' file and right-click, run in terminal, I get the brief flash of a terminal window then nothing - it is almost imperceptible, but it flashes.


> **useResa said:**
> When you start it in terminal, what command do you give?
Do you give the command in the SAS installation directory?
If you run it, do you get any error messages?

---

### Post by useResa on 2009-01-05
> **OldDirtyTurtle said:**
> I've run 'sas' the command at /usr/local/SAS/SASFoundation/9.2/AFAIK this is the directory where you should be running SAS from (I currently am still running the 9.1.3 release)

> **OldDirtyTurtle said:**
> In both cases - the reply is ```
bash: sas: command not found
```If you from a terminal cd into this directory
```
cd /usr/local/SAS/SASFoundation/9.2/
```
and you want to run SAS from there, you should give the command
```
./sas
```
Otherwise you indeed get the error as you have indicated above.

If you like to start sas by means of a command you should create a symbolic link to the /usr/bin directory. For example I create a link so that I can run SAS from any directory by giving the command: sas91

---

### Post by mörgæs on 2009-10-28
If you are thinking of SAS 9.2, here is some advice:

[http://ubuntuforums.org/showthread.php?t=1303357](http://ubuntuforums.org/showthread.php?t=1303357)

---

### Post by useResa on 2009-10-29
> **mörgæs said:**
> If you are thinking of SAS 9.2, here is some advice:

[http://ubuntuforums.org/showthread.php?t=1303357](http://ubuntuforums.org/showthread.php?t=1303357)Thanks for the tip.
I am still on 9.1.3 on my Ubuntu machine and don't know when I will switch, but always good to have such tips available. Saves a lot of time  ;)

---

### Post by mörgæs on 2009-10-29
No :-) but if you describe your problem thoroughly there is a chance that someone can help.

---

### Post by brennus on 2009-12-01
Hello,

Got SAS 9.2 and trying to install it via setup.sh. Terminal output: 

```

jonas@jonas-laptop ~/SAS_9_2_iso $ sh setup.sh
Preparing the SAS Deployment Wizard...
Launching the SAS Deployment Wizard...
jonas@jonas-laptop ~/SAS_9_2_iso $ 

```

Changed dash into bash, but it doesn't work either.
Any ideas? Thanks in advance.

---

### Post by mörgæs on 2009-12-02
What exactly is the problem? The output you show looks fine to me.

---

### Post by brennus on 2009-12-02
Well, the deployment wizard does not start. Actually, nothing starts at all. Nothing happens beside these two lines in terminal...

---

### Post by mörgæs on 2009-12-02
Have you tried ```
sudo ./setup.sh
``` ?

---

### Post by brennus on 2009-12-03
Yes, but it's the same anyway.
```

jonas@jonas-laptop ~/SAS_9_2_iso $ sudo ./setup.sh
[sudo] password for jonas: 
sudo: ./setup.sh: command not found
jonas@jonas-laptop ~/SAS_9_2_iso $ 

```

---

### Post by mörgæs on 2009-12-03
Sorry, should have been ```
sudo sh ./setup.sh
```

---

### Post by brennus on 2009-12-04
Okay, then: 
```

jonas@jonas-laptop ~/SAS_9_2_iso $ sudo sh ./setup.sh
[sudo] password for jonas: 
sh: Can't open ./setup.sh
jonas@jonas-laptop ~/SAS_9_2_iso $ 

```

EDIT:
I found the solution - copied all the files from the disk to a folder, then selected them all and in Properties set the permissions to Read & Write, as well as ticked "Allow executing file as program" box. It seems there was one more file that needed proper permissions.

---

### Post by shaunsmith_99 on 2009-12-16
Old thread but the info here is still really good! I got a copy of SAS from School and Installed it under 64 bit 9.04. I had almost every hiccup listed on this thread... Almost as bad as trying to install Adobe CS4 on Windows.... :o

    Thanks tho - BTW, for folks using SAS, where did you get it? I assume from whatever school you attend? I'm graduating and looking to apply for a PhD in stats, and so I looked at buying my own copy of SAS.... :(:(:( Suffice it to say that I'll go with R...Don't feel like being raped.

---

### Post by mbw on 2010-03-24
Wow - lots of folks wrangling with this since I last looked at this thread a few yrs ago... sorry for not posting better detail back then.... 

* Updated howto for SAS on Ubuntu - just today (3/24/2010) I accomplished an install of 64-bit SAS 9.2 (TS2MO) for Linux 64-bit native on Ubuntu 8.04 64 Bit (Hardy Heron AMD64, LTS)

Things I believe made this work:

1) A local copy of the SAS Software depot containing everything. (its ok if your depot contains windows and linux and even solaris instances, just bring the whole mess over - just make sure you have a valid linux install set in there)  I mounted my windows share containing the SWDEPOT via SMB like this:


 become root, or use SUDO if you have mount priv's that way.

 mkdir /mnt
 mount -t cifs //swdepot.windowsmachine.com/SAS92 /mnt -o
 dir_mode=0755,rw,user=windowsusername

 enter pw above.

 mkdir /sas92


cd /sas92

rsync -avr /mnt /sas92 

this copies everything over to your local directory, "/sas92" from the windows mountpoint "/mnt" - and has the added benefit of doing just an update, if you have updated your windows side SWDEPOT and want to just get the changes copied over.

my base directory of /sas92 looks like this:

# ls /sas92
autorun.inf        install_doc  product_data       sassd.txt   setup.sh       third_party
basicins.rexx      media_data   products           setup.dat   setup_vms.com  utilities
cd.id              order_data     setup.exe   setup_vms.exe
depotsummary.html  plan_files   saslogo.ico        setup.rexx  sid_files



2) A working user account on the Linux machine that is not
root, but has read access to /sas92 folder and ownership & write access to /usr/local/sas (or wherever you will be installing)

3) You must be in a graphical user environment such as gnome, kde... the SAS Deployment manager is a Java based GUI app.
Verify this by typing in your command window "xterm" - if you cant launch an X-term, there is no way you will launch the SAS installer.

4) You must have a working JAVA installation - on my ubuntu HH AMD64 this was a matter of installing the sun java packages... heres what I have installed:

# apt-show-versions | grep java
sun-java5-jre/hardy uptodate 1.5.0-22-0ubuntu0.8.04
sun-java6-bin/hardy uptodate 6-17-0ubuntu1.8.04
sun-java6-jdk/hardy uptodate 6-17-0ubuntu1.8.04
sun-java5-bin/hardy uptodate 1.5.0-22-0ubuntu0.8.04
sun-java6-jre/hardy uptodate 6-17-0ubuntu1.8.04
java-common/hardy uptodate 0.28ubuntu3
# 

5) You must have BASH installed. Not that "dash" replacement for it.  Check it this way:

# cd /bin
# ls -la | grep ash
-rwxr-xr-x  1 root root  813912 2008-05-12 11:36 bash
-rwxr-xr-x  1 root root  100856 2009-03-09 06:18 dash
lrwxrwxrwx  1 root root       4 2009-04-23 16:33 rbash -> bash
lrwxrwxrwx  1 root root       4 2009-04-23 16:33 sh -> bash

This is a correct setup - see that "dash" and "bash" are clearly
different files with different sizes. If bash is a symlink to dash, SAS wont install.

6) Your local copy of SWDEPOT may not have any spaces in the file path... if you do the /sas92 method I showed above, you should be ok.


7) Go for it:

- make sure you are logged in as non-root, and your X11 is
working, then start the sas deployment wizard with:

cd /sas92

./setup.sh

---

### Post by mörgæs on 2010-06-02
SAS 9.2 on Ubuntu 9.10:
[http://ubuntuforums.org/showthread.php?t=1494027](http://ubuntuforums.org/showthread.php?t=1494027)

---

### Post by bakinsoda on 2011-07-13
If anyone has trouble installing SAS on ubuntu, I found [these]("http://www.thejuliagroup.com/blog/?p=654") notes to resolve all my issues, from sh -> bash to the deployment window not launching (pre-reqs issue).

---

### Post by Baabel on 2012-05-22
I am trying to install SAS 9.3 on ubuntu and everything goes well until the installation itself. I get an error on every kernel 64-bit related part of the installation.  Here is the part of the log file I guess is important:
```
2012-05-23 00:49:37    InstallationTask - ${ProductHome}/utilities/bin/setuid.sh -> /usr/local/SASHome/SASFoundation/9.3/utilities/bin/setuid.sh
2012-05-23 00:49:37    Controller - An error occurred during processing:  
2012-05-23 00:49:37    Controller - There is a problem that seems to be related to the system running the install:  /usr/local/SASHome/SASFoundation/9.3/utilities/bin/setuid.sh with args  exited with non-zero return code:  2
2012-05-23 00:49:37    Controller - com.sas.tools.installs.it.InstallException
    at com.sas.tools.installs.it.tasks.RunApplicationTask.executeProcess(RunApplicationTask.java:215)
    at com.sas.tools.installs.it.tasks.RunApplicationTask.execute(RunApplicationTask.java:116)
    at com.sas.tools.installs.it.Controller.executeScript(Controller.java:2800)
    at com.sas.tools.installs.it.ExecutionThread.run(ExecutionThread.java:78)

2012-05-23 00:49:37    Controller - An error occurred during processing:  
2012-05-23 00:49:37    Controller - There is a problem that seems to be related to the system running the install:  /usr/local/SASHome/SASFoundation/9.3/utilities/bin/setuid.sh with args  exited with non-zero return code:  2
2012-05-23 00:49:37    Controller - com.sas.tools.installs.it.InstallException
    at com.sas.tools.installs.it.tasks.RunApplicationTask.executeProcess(RunApplicationTask.java:215)
    at com.sas.tools.installs.it.tasks.RunApplicationTask.execute(RunApplicationTask.java:116)
    at com.sas.tools.installs.it.Controller.executeScript(Controller.java:2800)
    at com.sas.tools.installs.it.ExecutionThread.run(ExecutionThread.java:78)
```
Im hopeless.

---

### Post by mbw on 2012-05-28
Couple of thoughts here:

- what is your shell ?  if you are using the "dash" replacement for "bash" - fix
that symlink.

- do you have the latest Java installed from Oracle?

- are you running as root

---

### Post by rajivweb on 2012-06-01
.

---

### Post by rajivweb on 2012-06-01
I had tried installing SAS on ubuntu,but can't get successful.:guitar:

---

### Post by mörgæs on 2012-06-01
If we should be able to help you, you need to provide a detailed description of what you have tried and what went wrong.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by rodhull on 2012-10-26
**mbw**'s suggestion of dash->bash fixed this for me (the setuid.sh errors surrounding the install of the threaded kernel components)

You need to run a reconfigure of the dash package, and NOT install it as /bin/sh

dpkg-reconfigure dash

All SAS/Foundation components install perfectly then...

---

### Post by MarmaladeJ on 2013-01-08
Hello, 
I am still somewhat of a linux newbie so please bear with me. 
I am attempting to install SAS 9.3 using Ubuntu 12.04 32-bit and I have attempted to follow all the directions here (not as the root user), but after I have completed all of the preliminary steps I receive an error while I am attempting to install:

user@user-linux:~$ sudo bash /home/user/SAS93/disk1/setup.sh

Error: Missing /home/user/SAS93/disk1/products/deploywiz__93340__prt__xx__sp0__1/deploywiz.ini.

This file does exist in the location that it says the file is missing, yet this error occurs every time. 

As well I have attempted to setup SAS 9.3 [following these directions]("http://www.webtolife.co.nz/content/sas-93-ubuntu-1204"), but I am still receiving the same error.  

Any help with what I might be doing incorrectly would greatly be appreciated.

---

### Post by mbw on 2013-01-14
2013 Update to installing SAS 9.2/9.3 on Ubuntu or Debian:
(see my original post #22 from 2008)


- Run the installer (setup.sh) while running as ROOT

- Make sure your system "/bin/bash" is not symlinked to
"dash" - I dont think it is enough to just start a
Bash shell... the SAS installer opens new windows, 
spawns new scripts, etc.  

- Your path to SW depot (all the install files) shall contain
no spaces

- Make sure the setup.sh script has the executable bit set

Am I forgetting anything?

-Matt

University of Washington, Seattle

---

### Post by MarmaladeJ on 2013-02-09
I didn't do anything differently than what I listed above other than update to the latest OS (ubuntu 12.10) and now everything works.
Following the link I provided earlier [SAS 9.3 install]("http://www.webtolife.co.nz/content/sas-93-ubuntu-1204") will actually get it to run. Of course I also followed the no spaces rule and I mounted the .iso file and copied all of the files to the hard drive. SAS 9.3 is now running. Thanks all.

---

### Post by rockera77 on 2013-04-19
Hi! Im trying to install SAS I was able to run the setup.sh, it seem to be doing the whole instalation but then when it is done I cant find the application anywhere. I try to access to it by terminal typing SAS but it doesnt work. Can you tell me how to access the application? or could it be that my installation didnt work?

---

### Post by mörgæs on 2013-04-19
As you can see in 
[http://ubuntuforums.org/showthread.php?t=1303357](http://ubuntuforums.org/showthread.php?t=1303357)

you have to find the executable somewhere in /usr/local/SAS/... 

At least it was the case for SAS 9,2. Are you on 9,2 or 9,3?


Good luck;[INDENT]Mörgæs;[/INDENT]

---

