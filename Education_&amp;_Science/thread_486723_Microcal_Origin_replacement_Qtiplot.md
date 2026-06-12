---
title: "Microcal Origin replacement: Qtiplot"
date: 2007-06-28
forum: Education &amp; Science
---

### Post by tepegoz on 2007-06-28
Hi folks,
I was looking for a replacement of famous Microcal Origin in open source world.  I tried many programs but non of them were successful enough to be a replacement.  So I was using origin 6.0 with wine.

A few days ago, I tried qtiplot ([http://soft.proindependent.com/qtiplot.html](http://soft.proindependent.com/qtiplot.html)). Actually I tried to try this before, but the compiled packages were being sold, and  I could not compile the source (there were many dependency problems, and could not spend enough time on that).  But now, there is an evaluation version on the web page, and it is fully functional except a few simple things.  And also there is a repo for this package only : 
deb     [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons)   sarge   /
This repo has older version than on the web page.

After long trials, I found out that qtiplot is really very successful and can be a full replacement to Microcal Origin.  Fitting works perfectly and the graphics are really very qualified.  The menus are also very similar to origin.  There is also an import function for origin files, but it does not convert everything.  

So, I strongly recommend using qtiplot as a replacement of microcal origin.

---

### Post by der_vegi on 2007-11-15
By the way, the repo has now 0.9, but this version is not under 'addons sarge' but 'etch'. Just have a look at [http://debian.physik.hu-berlin.de]("http://debian.physik.hu-berlin.de"). You have to downgrade to Qt 4.2 to use it, though.

---

### Post by tepegoz on 2007-11-21
Hi,
qtiplot 0.90-rc2 is now in repos of gutsy.  Really good work.

---

### Post by wu_qso on 2008-01-21
Now I'm trying qtiplot (v0.9 on Fedora 8 ) and its curve fitting. The attached is an example but apparently wrong fittings. My Gaussian fittings lead always to straight lines, as shown in the plot. The Lorentz fitting is apparent too far away from the actual data points. Anybody else has similar problem.

---

### Post by wu_qso on 2008-01-21
The example fittings.

---

### Post by crazy ivan on 2008-07-06
This is a big problem; there is no linux tool for experimental physicists. 
Qtiplot has the windows of Origin 7.5, but it does obviously not have the maths. The fits just produce wrong results, especially the multi peaks.

And now the newest releases are not avialable as binaries for other platforms, because the developer pleas for more support. Still I recommend you all to download [the newest linux binaries]("http://soft.proindependent.com/download.html") (v 0.9.6.2 vs 0.9.3 in repos), since that version crashes way less.

Labplot is a lot more solid, but it seems to have less options. Since Origin 7.5 is not all the best in functionality aswell and it does not fully work with wine, I'm a bit desperate - having to reboot for each graph is not an option..

---

### Post by crazy ivan on 2008-07-06
Maybe this QtiPlot fork [SciDAVis]("http://scidavis.sourceforge.net/") will be better some time.. But now its just getting started.

---

### Post by jimmysheldon on 2008-11-22
Hey, thanks for pointing this out. I'm too lazy to walk into campus, and too tight to buy origin. So this is just the ticket thank you.

---

### Post by Arienn on 2011-05-12
Hi,
I'm trying to use Origin 6.0. After slight problems I managed to install wine (1.2). However, I can't open any file and the terminal reads

arienn@ubuntu:~$ wine /host/WINDOWS/system32/Origin60.exe
fixme:storage:create_storagefile Storage share mode not implemented.

I'm using Ubuntu 10.10 with Gnome 2.32.0. Any ideas what to do? They would be really appreciated.

Have a nice time,
/arienn

---

### Post by Lateralis on 2011-05-13
I was using Origin 6.0 under previous version of wine wine.  I don't currently have 6.0 installed under wine as the department has a site-wide license for Origin 8, which I use in Crossover.  So far, Origin 8.0--8.2 work fine in Origin and Wine, but there are some problems with 8.5.  

So, to your problem, it looks like you're trying to open it in a strange way.  You should be able to go to Applications -> Wine -> Programs -> Origin (or something similar) in order to find the launcher.  Programs installed under Wine are pretty well integrated into that menu.  If you really wanted to use the commandline, you should be able to go

```

$ wine  ~/.wine/drive_c/Program\ Files/<path to Origin directory and executable>

```

If you install it under Crossover, then again you get a menu item under Applications -> Windows Programs -> Origin (or something similar).  

As for SciDaVis, I've only just found out about that.  Thanks for that link.  I've been looking at programs to make plots which are of a publishable standard for sometime.  Origin is the only thing I've found which is flexible enough to do what I want and make graphs which are pretty and how I want them.  It does have its idiosyncracies, but like all things, once you've worked those out you can navigate around them.  But having something which works natively in Linux is better.

---

