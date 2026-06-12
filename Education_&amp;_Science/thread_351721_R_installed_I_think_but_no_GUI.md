---
title: "R installed I think but no GUI"
date: 2007-02-02
forum: Education &amp; Science
---

### Post by samden on 2007-02-02
I am running Xubuntu dapper on an iMac G3.

I installed R through Synaptic by marking r-base for installation. Synaptic marked a number of  dependent packages, and I installed them all.

However R did not show up in my applications menu. I can start R in a terminal through the command line, but it only comes up in the terminal - R does not open in its own window.

Should I have selected a GUI to install for R? What file should I install for this?

---

### Post by theblackgecko on 2007-02-02
From what I know, R only runs in terminal mode on Linux. So, one simply cuts and pastes the desired code from one's favorite editor directly into the terminal.

Try cutting and pasting the following:
a <-3
b <-5
a+b
a*b

and you will see that the R terminal works.

---

### Post by akniss on 2007-02-02
> **samden said:**
> I am running Xubuntu dapper on an iMac G3.

I installed R through Synaptic by marking r-base for installation. Synaptic marked a number of  dependent packages, and I installed them all.

However R did not show up in my applications menu. I can start R in a terminal through the command line, but it only comes up in the terminal - R does not open in its own window.

Should I have selected a GUI to install for R? What file should I install for this?

R does not have a GUI.  It strictly a CLI based environment.  There are other packages that have been developed to try and put a GUI on top of R, but I don't know if any of them are in the Dapper repos.

Three such 'add-ons' are:
Rcmdr: R commander - run R as root, and install it from CRAN using the following commands (one line at a time):```
sudo R
install.packages('Rcmdr')
q()
```
A window will come up asking you to choose a mirror.  Choose one and the package should get installed.  After installation, quit R with the q() command.  You can then run R again as normal user and load the Rcmdr GUI with the command ```
R
library(Rcmdr)
```

JGR: Java GUI for R - JGR is java based, and so should be platform independent.  Google it and you should get to the home page.  I've never actually tried it.

Rkward: This one looks the most promising, but it still looks like its early in development.  Not sure if there are Dapper .debs available or not.

---

### Post by thePsychologist on 2007-02-04
R comes with it's own window which uses Tcl/Tk which can be started by the command:

R --gui=Tk

Which allows you to select mirrors, etc. not really useful in my opinion. There are some other GUIs, and aside from the ones already mentioned you can look at some other ones:

[http://www.sciviews.org/_rgui/](http://www.sciviews.org/_rgui/)

RKWard is probably the most developed, and I think it's a KDE app. Check it out. [http://rkward.sourceforge.net/](http://rkward.sourceforge.net/). There's a deb file you can download too.

---

### Post by earlycj5 on 2007-02-06
Rkward, while not complete, makes using R in Linux much easier than the command line alone and easier than Windows with the GUI provided by R for Windows.

---

### Post by awe1 on 2012-04-16
Old thread but in case someone is still googling this like I did now...

Rstudio can be downloaded from [http://rstudio.org/](http://rstudio.org/).

---

### Post by overdrank on 2012-04-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

