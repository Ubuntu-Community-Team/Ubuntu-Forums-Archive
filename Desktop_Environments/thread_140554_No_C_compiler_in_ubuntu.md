---
title: "No C compiler in ubuntu"
date: 2006-03-06
forum: Desktop Environments
---

### Post by smyrna on 2006-03-06
I tried to install a package and of course, this distro doesn't have a C compiler!

I found an earlier thread that says to install "build-essential."

So then I tried to run Synaptic Package Manager from the System > Administration menu, and of course, nothing happens!  No error message, no dialog box, nothing.

Could somebody tell me how to install "build-essential"?  I can't run the
Synaptic Package Manager.  Login Screen Setup is another Administration
menu item I can't run either.

A command line way to install "build-essential" would be helpful.  Is there
a guide to making sure that my Ubuntu install has what you would typically
expect in a Linux environment?  A C compiler is something that is just so
basic...

Thank you.

---

### Post by knalle on 2006-03-06
```
sudo apt-get install gcc
```

---

### Post by smyrna on 2006-03-06
So I did apt-get install build-essential, but now the package I want to install
(gDesklets) gives the following error:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Could somebody clue me in on how to install this perl module?

Thank you.

---

### Post by knalle on 2006-03-06
```
sudo apt-get install libxml-parser-perl
```

---

### Post by Ramses de Norre on 2006-03-06
[http://www.ubuntuforums.org/showthread.php?t=140528]("http://www.ubuntuforums.org/showthread.php?t=140528")

---

### Post by smyrna on 2006-03-06
I get the following error:

> $ sudo apt-get install libxml-parser-perl
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxml-parser-perl


---

### Post by MichaelZ on 2006-03-06
Hello,

I use the Synaptic Package Manager to install the packages that I need. Until now it worked fine.

Best wishes,
Michael

---

### Post by knalle on 2006-03-06
[QUOTE=smyrna]I tried to install a package and of course, this distro doesn't have a C compiler!

So then I tried to run Synaptic Package Manager from the System > Administration menu, and of course, nothing happens!  No error message, no dialog box, nothing.
[/QUOTE]

how did you install ubuntu anyway?

---

### Post by smyrna on 2006-03-06
[QUOTE=knalle]how did you install ubuntu anyway?[/QUOTE]
I did the graphical install and then the windowing system completely
did not work.  I booted a Knoppix live CD (the Ubuntu live CD stopped
working after I upgraded the memory from 512mb to 1gig) and then
edited the /etc/X11/xorg.conf and changed "via" to "vesa."

Synaptic Package Manager just refuses to run on my machine
(Averatec 3200 series laptop).  Do you have any ideas why?

---

### Post by knalle on 2006-03-06
try to reinstall synaptic;

```

sudo apt-get remove synaptic
sudo dpkg --purge synaptic
sudo apt-get install synaptic

```

---

### Post by smyrna on 2006-03-06
[QUOTE=knalle]try to reinstall synaptic;

```

sudo apt-get remove synaptic
sudo dpkg --purge synaptic
sudo apt-get install synaptic

```[/QUOTE]
I reinstalled Synaptic and it still won't run...

Is there some log file that I can cut and paste here to help you diagnose the
problem?

---

### Post by knalle on 2006-03-06
really really strange, open a terminal an start synaptic as root, post any output that shows up in the shell.

```
sudo synaptic
```

---

### Post by smyrna on 2006-03-06
[QUOTE=knalle]really really strange, open a terminal an start synaptic as root, post any output that shows up in the shell.

```
sudo synaptic
```[/QUOTE]
Okay.  Now Synaptic Package Manger works. Where do I find gDesklets exactly?

I clicked on the "Search" button and it couldn't find anything.  Is there some
repository that I'm supposed to download gDesklets from?

---

### Post by knalle on 2006-03-06
[QUOTE=smyrna]Okay.  Now Synaptic Package Manger works. Where do I find gDesklets exactly?

I clicked on the "Search" button and it couldn't find anything.  Is there some
repository that I'm supposed to download gDesklets from?[/QUOTE]

yes, open synaptic settings and repositories, then add the word **multiverse** after each place you see the word **universe**. restart synaptic and try a new search

---

### Post by smyrna on 2006-03-06
[QUOTE=knalle]yes, open synaptic settings and repositories, then add the word **multiverse** after each place you see the word **universe**. restart synaptic and try a new search[/QUOTE]
Thanks knalle, I got everything working now!

---

