---
title: "can't install firefox"
date: 2005-01-06
forum: Desktop Environments
---

### Post by brk-guy on 2005-01-06
I got to the firefox site and I download the latest linux version. When I install it on ubuntu it saids it can't find some file, and I did downloaded a couple of times. 

Also where is the default location to install programs?

---

### Post by tiiim on 2005-01-06
[QUOTE=brk-guy]I got to the firefox site and I download the latest linux version. When I install it on ubuntu it saids it can't find some file, and I did downloaded a couple of times. 

Also where is the default location to install programs?[/QUOTE]
 you get firefox with Ubuntu? but if your upgraded and your on x86 machine you can upgrade to firefox thru the unofficial backport sources which will save you a lot of hassle.

If your a amd64 or powerpc user you either have to find the files yourself on apt or a debian pool somewhere or wait to march for hoary.

---

### Post by tiiim on 2005-01-06
default install programs are

/usr/bin is the excutable

/usr/games is for games


it does throw some files elsewhere but if your looking for excutables they be in there.

but the .deb system will do all the hardwork for you. you may just have to add them to the menu.

---

### Post by brk-guy on 2005-01-06
[QUOTE=tiiim]you get firefox with Ubuntu? but if your upgraded and your on x86 machine you can upgrade to firefox thru the unofficial backport sources which will save you a lot of hassle.
[/QUOTE]
How do I do that?

---

### Post by fng on 2005-01-06
Open Synaptic
Settings -> repositories
Click on the new button
Fill in the information below:

Stable Backports Branch (well-tested working software):
URI: [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu)
Distribution: warty-backports
Section(s): main universe

Save the repositories and close the repository window
Click on the big reload button in the left upper corner
Search for firefox
You should now be able to install the 1.0 version

---

### Post by wallijonn on 2005-01-06
fng,

I notice that Synatic now shows up as being upgradeable. hmmm. Seems kind of dangerous, to me.

---

### Post by fng on 2005-01-06
I'm pretty sure that has nothing to do with adding the backport repository wallijonn.

---

