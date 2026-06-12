---
title: "Data manipulation."
date: 2007-03-13
forum: Education &amp; Science
---

### Post by Timtro on 2007-03-13
Hello all,

I'm somewhat new to working with raw data in linux, but it seems that it should be a lot more convenient than windows.

I'm a physicist and I often work with columns of numbers, often ordered sets. I was wondering what the best softwares to perform data manipulation are. I would be looking for things akin to Origin and/or Sigmaplot (I know this is a biologists tool :S)

Plotting routines and such aren't so important to me since I use GNUPLOT, although if anyone has a better way to do things, I'm all ears. Keep in mind though that I'm using picky, and I use GNUPLOT mostly because of the epslatex terminal, which allows me to plot graphs which will use the font of the document I'm writing.

Thanks!

---

### Post by parktownprawn on 2007-03-13
If you want a command line program - awk is pretty good at manipulating columns of data and not too hard to learn.

---

### Post by Timtro on 2007-03-13
> **parktownprawn said:**
> If you want a command line program - awk is pretty good at manipulating columns of data and not too hard to learn.

I've used awk, and perhaps for my present problem it would work, but I'm going to want to do curve fitting and applying mathematical transformations to columns. I guess like a spreadsheet.

At the moment, for what I need to do, I'm sure I could use OpenOffice spreadsheet, but my problem is that I have a bunch of text files each containing two columns, and I want to get them into one file, and then start doing some math on the columns. I can't seem to import them into the spreadsheet program like I could with, say, Excel **shudder**, or Sigmaplot.

---

### Post by parktownprawn on 2007-03-13
well when it comes to combining files, the command cat is the way to go:

to combine files:

cat file1 file2 file3 > file4

to append one file to another

cat file1 >> file2

I'm afraid i'm not too familiar with spreadsheet programs and which ones might have the capabilities you desire.

for my simple needs I prefer gnumeric to open office since it loads a lot faster (especially if you're using gnome and not kde)

---

### Post by Timtro on 2007-03-13
> **parktownprawn said:**
> well when it comes to combining files, the command cat is the way to go:

to combine files:

cat file1 file2 file3 > file4

to append one file to another

cat file1 >> file2

I'm afraid i'm not too familiar with spreadsheet programs and which ones might have the capabilities you desire.

for my simple needs I prefer gnumeric to open office since it loads a lot faster (especially if you're using gnome and not kde)

Hmmm, that could be of some help. I'll try gnumeric.

If I'm not mistaken though, cat concatenates documents, so it would put my columns end to end, right? I need them side by side. I suppose I can write a program to do this quite easily, but I know linux should have this standard capability.

Thanks so much! I greatly appreciate you taking the time to reply. Any other hints you may have are welcomed.

---

### Post by Timtro on 2007-03-13
Thanks,

The gnumeric helped for now, but I'm probably going to want something a little more science oriented. Curve fitting etc. I tried to install Scigraphica using apt-get, but something didn't go quite right, and I ended up with problems. I'm trying fityk right now.

I'm still open to suggestions from any and all.

---

### Post by jfinkels on 2007-03-13
Maybe try R? [http://www.r-project.org/](http://www.r-project.org/) I don't really know if it's good for data manipulation, but it's used for statistics and plots and stuff.

---

### Post by parktownprawn on 2007-03-13
yup cat will put them end to end - other than writing a short script i wouldn't know how to do what you want

---

### Post by akniss on 2007-03-13
> **jfinkels said:**
> Maybe try R? [http://www.r-project.org/](http://www.r-project.org/) I don't really know if it's good for data manipulation, but it's used for statistics and plots and stuff.

I typically use a combination of gnumeric / R for manipulation / plotting.  R is unparalleled for statistics and plotting power, but can be a little much for tasks such as moving columns around.  Gnumeric is perfect for the smaller tasks, and can create rather pretty plots as well.

---

### Post by ssam on 2007-03-13
for pushing around text the gnu text utils can do almost anything.

there is a basic list at [http://www.gnu.org/software/textutils/textutils.html](http://www.gnu.org/software/textutils/textutils.html)

there are the slides from a talk i saw about all the gnu core utils at [http://www.treblig.org/stuffiwrote.html](http://www.treblig.org/stuffiwrote.html)

if you want to go more advanced then i would recommend using python (though old skool people might say perl :-) ). there advanced math and scientific libraries at [http://www.scipy.org/](http://www.scipy.org/)

---

### Post by tweedledee on 2007-03-14
> **Timtro said:**
> I'm somewhat new to working with raw data in linux, but it seems that it should be a lot more convenient than windows.

Only to a point.  My experience is that data for science projects exceeds that point rather quickly.  Linux is certainly no worse than Windows, but I'm not convinced it's much better for that kind of task.

> I'm a physicist and I often work with columns of numbers, often ordered sets. I was wondering what the best softwares to perform data manipulation are. I would be looking for things akin to Origin and/or Sigmaplot (I know this is a biologists tool :S)

Being a (bio)chemist who uses several instruments that produce columns of ordered sets (usually with some miscellanous useless information thrown in), I understand your problem.  Unfortunately, I often find myself firing up my Windows virtual machine simply to use Origin.  Don't get me wrong - I have numerous other native Linux programs that can each do some function as well or better, but nothing that comes close to the total package.  Sometimes it's just easier/faster to deal with Windows and Origin than the 2-4 Linux programs I'd need for the same task.

I've actually found OpenOffice Calc to be superior as far as importing and working with data under Linux than Windows, and Gnumeric is great for certain tasks.  However, I also have a collection of custom Python scripts for simple parsing of raw data and sometimes some rearranging/trimming/baseline subtraction/etc in order to allow the spreadsheets to import cleanly and speed up the analysis.  I'd be happy to share ideas/code if you find the solutions you are investigating don't seem to be enough.

And please share how fityk works out - I've had that installed for a while in order to test it out, but keep getting distracted (the project I plan to try it for is not my highest priority).

---

### Post by in_flu_ence on 2007-03-14
Hi tweedledee,

     I am always interested in getting python to work with openoffice. Any tips or website that gives a clear tutorial? There are official documents but it seems to be too lengthy for me to just write some simple script to enhance the openoffice features.

     I just probably need some capability that VBA can do but since I have learnt some basic python and I do not really want to go and learn the changes in macro in Openoffice.

     Tips will be great. I do need some curve fitting and data manipulation tools too.

Thanks

---

### Post by Toufik on 2007-03-15
If you're a physicist, the best tool ever is ROOT developed by CERN [http://root.cern.ch/](http://root.cern.ch/) 

But maybe this is the bazooka to kill the fly :)

---

### Post by ahmatti on 2007-03-16
For me as a Matlab user the best free tool for manipulating raw data is Octave. So signal processing, plotting, curve fitting, statistics, fuzzy and neural models + own algorithms.

I use Matlab in Ubuntu in the office and Octave in Ubuntu at home. I find that almost all of my Matlab code works in Octave, except for plotting so for good quality plots I'm forced to use Matlab.

Matlab is also about 2 times faster in Ubuntu than in Windows so if you have large amounts of data linux is definetly the way to go :)

---

### Post by Timtro on 2007-03-16
> **Toufik said:**
> If you're a physicist, the best tool ever is ROOT developed by CERN [http://root.cern.ch/](http://root.cern.ch/) 

But maybe this is the bazooka to kill the fly :)


Wow! This looks impressive! I can't wait to give it a spin!

---

### Post by Timtro on 2007-03-16
> **tweedledee said:**
> Only to a point.  My experience is that data for science projects exceeds that point rather quickly.  Linux is certainly no worse than Windows, but I'm not convinced it's much better for that kind of task.



Being a (bio)chemist who uses several instruments that produce columns of ordered sets (usually with some miscellanous useless information thrown in), I understand your problem.  Unfortunately, I often find myself firing up my Windows virtual machine simply to use Origin.  Don't get me wrong - I have numerous other native Linux programs that can each do some function as well or better, but nothing that comes close to the total package.  Sometimes it's just easier/faster to deal with Windows and Origin than the 2-4 Linux programs I'd need for the same task.

I've actually found OpenOffice Calc to be superior as far as importing and working with data under Linux than Windows, and Gnumeric is great for certain tasks.  However, I also have a collection of custom Python scripts for simple parsing of raw data and sometimes some rearranging/trimming/baseline subtraction/etc in order to allow the spreadsheets to import cleanly and speed up the analysis.  I'd be happy to share ideas/code if you find the solutions you are investigating don't seem to be enough.

And please share how fityk works out - I've had that installed for a while in order to test it out, but keep getting distracted (the project I plan to try it for is not my highest priority).

Its nice to hear from someone with the same problem, but more experience. I have found Gnumeric to be useful. I have a certain stigma about spreadsheet software, but Gnumeric seems to be a might more convenient than Excel for this type of thing. That could be inexperience in Excel talking though. I still say that scientific graphs should NEVER be made in spreadsheet software ;) [-X It drives me nuts when colleagues send me Excel plots * gag *


Thanks a lot.

P.S. I will make a point of letting you know if I make any progress with fityk.

---

### Post by akniss on 2007-03-16
> **Timtro said:**
> It drives me nuts when colleagues send me Excel plots * gag *

I agree... one of the journals I regularly submit to actually still accepts Microsoft Powerpoint files for figures!!!

---

### Post by Timtro on 2007-03-16
> **ahmatti said:**
> For me as a Matlab user the best free tool for manipulating raw data is Octave. So signal processing, plotting, curve fitting, statistics, fuzzy and neural models + own algorithms.

I use Matlab in Ubuntu in the office and Octave in Ubuntu at home. I find that almost all of my Matlab code works in Octave, except for plotting so for good quality plots I'm forced to use Matlab.

Matlab is also about 2 times faster in Ubuntu than in Windows so if you have large amounts of data linux is definetly the way to go :)


I used octave for my last bit of data analysis. It was an extremely small data set (9 ordered pairs), but it was fast an convenient to get some numbers. As I already have experience in Matlab, it wasn't at all hard to write the .m file to process the data, and since I don't care about getting pro quality plots (since I use GNUPLOT), I don't need to spend money on Matlab. 

I just have to learn how to write code to read in data files, and to write out data files. With only 9 ordered pairs, the data was simply hard coded in the .m file.

Thanks for your reply.

---

### Post by tweedledee on 2007-03-17
> **in_flu_ence said:**
> Hi tweedledee,

     I am always interested in getting python to work with openoffice. Any tips or website that gives a clear tutorial? There are official documents but it seems to be too lengthy for me to just write some simple script to enhance the openoffice features.

     I just probably need some capability that VBA can do but since I have learnt some basic python and I do not really want to go and learn the changes in macro in Openoffice.

     Tips will be great. I do need some curve fitting and data manipulation tools too.

Thanks

Actually, I do all of my python processing outside of openoffice, then just import the results.  I find that easier than messing around with macros/plugins/etc.  I may have to finally break down and deal with it, though, as I have a problem that requires me to add strings (in order to save huge amounts of time), and no spreadsheet seems able to do that without a python hack.  I also think Gnumeric has better support for python scripts than OpenOffice, but I've probably spent all of 5 minutes evaluating the differences.  Basically, I find that OpenOffice is easier/faster for simple tasks and generally has better format control in the spreadsheet, but Gnumeric is much more powerful and is vastly superior/faster for graphs.  For anything requiring real data analysis, definitely use Gnumeric.

Timtro & akniss - Excel plots (especially the default settings) drive me crazy, I gave up on MS Office long before I managed to switch entirely to Linux.  I find that Gnumeric (and to some extent Calc) can be used to make solid publication-quality plots provided you don't need anything too sophisticated and you put in some effort (Calc's defaults are pretty bad, too, but at least I could change most of them).

---

### Post by hizaguchi on 2007-03-21
I use Gnumeric for all my plotting needs and just export the graphs as images to stick in my LyX files.  It makes much nicer looking plots than anything else I've used and, once you get over the learning curve, it makes plotting more complicated things fairly easy.  I just plotted a fan performance curve with 3 sets of y axes last night.  It would have taken me forever to do in Excel, but Gnumeric puts all the options in one place, so it is much more convenient to make adjustments.

---

### Post by cinnabar on 2007-03-21
There are a few applications I've used that are similar to sigmaplot/origin and produce very high quality graphs:

[Veusz]("http://home.gna.org/veusz/")- My personal favorite.  Produces very, very nice plots and is fantastic for making plots in a grid.  My only issue (and this is a near deal breaker for me) is that it can't use data in a datetime format.  Also, you can't add arrows and draw shapes on the plots.  Despite that, this is one of my favorite pieces of plotting software (including commerical programs) due to ease of use and control.

[Qtiplot]("http://soft.proindependent.com/qtiplot.html") - very powerful and has lots and lots of data fitting tools.  I've found the actually graphing to be a little clunky.  For instance, resizing images or creating a grid of plots is frustrating, IMHO.  Otherwise a very nice program.

[Kst]("http://kst.kde.org/") - A seemingly nice and frequently updated program for plotting streaming data.

There are many other programs I haven't messed with much including [Scigraphica]("http://scigraphica.sourceforge.net/"), [RLplot]("http://rlplot.sourceforge.net/"), [Grace]("http://plasma-gate.weizmann.ac.il/Grace/"), [R]("http://www.r-project.org/"), and many, many others.  

I am not a programmer but have perl to be a good language to crunch large datasets.  Other than that, I typically use spreadsheet programs (i.e., openoffice calc) to crunch smaller bits of data.  I agree that only the most basic figs should be made with spreadsheets and they should never be used for serious publication.

Good luck!

---

### Post by xadder on 2007-03-22
I use pylab, which combines powerful python programming (with numpy to take care of arrays), and matplotlib (MPL) which produces great graphics.  And with ipython one can both play around semi-interactively and write scripts at the same time. This package allows matlab-like functionality and seems more flexible to me than Octave. In the past I have  tried Grace, but that has the fatal flaw of not handling NaN and being aimed at interactive rather than scripting work. I need to do both! I just started with MPL this year, but it seems great to me.

---

### Post by slaanco on 2007-03-23
I would suggest GDL Gnu Data Language it's a free alternative to IDL, and it's heavilly used in astrophysics society for data processing, it can do the same stuff as gnuplot + you can write code in it and it has a support from NASA (there is a IDL NASA library and  since GDL is 100 % comapitible with IDL it should work also)  and many other libraries.

---

### Post by der_vegi on 2007-04-01
my favorite is qtiplot. it is very similar to origin, but i think the handling is nicer, especially for defining custom functions for curve fitting.

if you need a repository for it, try the one from my university:

[http://debian.physik.hu-berlin.de/]("http://debian.physik.hu-berlin.de/")

---

### Post by briansers on 2007-04-03
Thanks folks, this has been an extremely useful discussion.  I've just grabbed qtiplot, which works well for me since I am most familiar with Origin.  I've been looking for a program like this for a LOOONG time.

---

### Post by der_vegi on 2007-04-04
yeah, qtiplot is a good choice. :) 

they're planning the 0.9 release candidate this weekend, i'm really looking forward to it. *g

---

### Post by NikoC on 2007-04-06
I use Rlplot which is in the repos.

---

