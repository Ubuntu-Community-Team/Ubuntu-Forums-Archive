---
title: "Updating Firefox and Open Office; deleting evolution"
date: 2005-01-08
forum: Desktop Environments
---

### Post by Athanasius on 2005-01-08
I am new to Linux in general so I am just trying to get my bearings.  

All I want to do is to remove the older versions of Firefox and OpenOffice and install the new versions.  However I am not familiar with how the files are set up on Ubuntu and don't know where the files are supposed to be installed to.  I also want to put desktop icons for those programs but I don't know how to do that either.  When I go to Application > Internet I want it to open the new version of Firefox and OpenOffice and not the old. 

I don't really need to use Evolution and I want to take that off.
 :confused:  :confused:  :confused:

---

### Post by mrosenlof on 2005-01-08
There's no real reason to remove Evolution unless you're in need of disk space.  If you don't run it, its presence is not going to hurt anything.

You can try using the Synaptic package manager to remove it.  You might however find that the ubuntu-base depends on it, and you don't want to remove that.

---

### Post by Bart Van on 2005-01-08
[QUOTE=mrosenlof]There's no real reason to remove Evolution unless you're in need of disk space.  If you don't run it, its presence is not going to hurt anything.

You can try using the Synaptic package manager to remove it.  You might however find that the ubuntu-base depends on it, and you don't want to remove that.[/QUOTE]
Might be interesting to block the Evolution-version in Synaptic (in Package menu) if it can't safely be deleted, especially on low-bandwith connections. That way you don't waste time and bandwith updating packages you don't use.
Or does this have negative side-effects a newbie like me can't think of?

---

### Post by tiiim on 2005-01-08
[QUOTE=Bart Van]Might be interesting to block the Evolution-version in Synaptic (in Package menu) if it can't safely be deleted, especially on low-bandwith connections. That way you don't waste time and bandwith updating packages you don't use.
Or does this have negative side-effects a newbie like me can't think of?[/QUOTE]
 there are several ways to update firefox (and possible Open office?)

The easy way is to either wait until Hoary (april) or if your on a PC you can get the Unbutu unofficial sources that are like half way between Warty and hoary and that site is:

ubuntu-bp.sourceforge.net/

following instructions there.

Then simply go on and update firefox that way.

---

### Post by andy_sp1ke on 2005-01-22
The best way i found to update firefox was to go to its website and download the tar file of the new version, then start up synpatic and remove the old verion. then just install the new one from the terminal as root user (or sudo), i installed it to /opt/firefox-installer . Then make a new customapllication launcher and you will find the program file easily in the directory u install to. Its very easy, one of the easiest linux programs to install i have found!! I got the latest aMSN through this way aswell. ITs just quicker!

Andy

---

### Post by macewan on 2005-01-22
I'd head over to [https://www.ubuntulinux.org/wiki/BreakMyUbuntu](https://www.ubuntulinux.org/wiki/BreakMyUbuntu) and follow instructions on adding backports to your sources.list and then grabbing firefox 1.0 that way.

---

### Post by clparker on 2005-01-23
I wrote this handy little how to on the best surefire and safeway to install Firefox 1.0 [http://www.ubuntuforums.org/showthread.php?t=1136]("http://www.ubuntuforums.org/showthread.php?t=11369")[9]("http://www.ubuntuforums.org/showthread.php?t=11369")

---

