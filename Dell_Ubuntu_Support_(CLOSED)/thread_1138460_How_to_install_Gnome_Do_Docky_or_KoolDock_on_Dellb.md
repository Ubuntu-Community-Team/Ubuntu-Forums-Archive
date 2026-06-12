---
title: "How to install Gnome Do Docky or KoolDock on Dellbuntu (LPIA)"
date: 2009-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-04-26
Hi,
i am looking some launch bar/dock for my dell mini. AVN, SimDock, KoolDock-they all have some problems on dell´s mini 9 Ubuntu LPIA (or they need Compiz, or are KDE...)

I tried KoolDock 0.3 (it is in synaptic)-i like it, but i can not launch any programm (see picture-i hope some one can guide me to fix it)

GNOME Do docky turn very nice to be-but in Synaptic is old version-so, docky is not there, but i am not even sure if i need something like that-Kooldock seems just nice. Does anyone knows how/and which version to install to make docky working? I want it to be in Synaptic, so i can easily deinstall it-i am newbie so i do not know how to deinstall programms whitout synaptic.

SimDock is too buggy...

Thanks.

---

### Post by vickoxy on 2009-04-26
no one uses some dock in dell´s ubuntu?

---

### Post by vickoxy on 2009-04-26
So, i went to gnome-do pages, i added to synaptic their repositories-but the version i get of gnome-do is 0.6. I need a gnome-do 0.8 to activate docky. To activate docky i need to activate "metacity compositing manager" (how danger for me as newbie all that can be?)
So, i can download and manually install 0.8-but how to complete remove it if it is not working fine? I do not know terminal commands well-so if anyone can guide me to set it right, i´ll appreciate it.

I found here some instructions:
[http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12](http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12)

---

### Post by vickoxy on 2009-04-27
Ok, little report: i activated "metacity compositing manager" and installed Avant Window Navigator from synaptic. It was shown properly, although it won´t automatically hide every time (have to go over him with mice cursor). But, i uninstalled it, and adapted one control panel and use it as Launch Bar/Dock. Why? The system works fine (not slowly as with Compiz-compiz works fine if you install full version of Ubuntu, but with Dellbuntu LPIA not so smooth), but there are some glitches (few milisec) if you switch the tabs or open some applications. AWN Looks beautiful, but i prefer the mini 9 Ubuntu system to be fast and flawless, even less beautiful. 

But if you prefer to have nice dock/launch bar, you can go with AWN....

---

### Post by vickoxy on 2009-04-27
Sorry for putting these post on several threads, but maybe others will find it usable. 

I succeeded to make KoolDock working just fine in Dell´s Ubuntu 8.04 (lpia).
First: from synaptic you can download only KoolDock 0.3-no good...it won´t work. 

1) Find then on line KoolDock 0.4.6. and download it
2) install KDEbase (it will install 34 Packages with more than 70 MB... i didn´t notice any change in my system-hope just that this downloads are not fatal)
[http://lists.kde.org/?l=kde-announce-apps&m=119053945506482&w=2](http://lists.kde.org/?l=kde-announce-apps&m=119053945506482&w=2)
3) Doobleclick on your KoolDock (you can previously install from synaptic 0.3 if you want....) and installation will go automatically

So, that was it. Panel and KoolDock are fastest Launchers for Metacity LPIA Ubuntu 8.04-you don´t have to activate compositing metacity. There are some issues-fonts looks ugly-so better do not show them. But the panel is quick, installation of new apps is easy (just drag and drop), and transparency works fine (sometimes there are some glitches...but nothing serious).

P.S. I didn´t figure how to add folders and documents on KoolDock, so if anyone find solution...

---

### Post by 666porcondissaum on 2009-05-21
Gnome Do 0.8.1 + Docky in Hardy Heron 8.04:

Enable the repository shown in the site below:

[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

Update and Reboot. Doesn't matter if Gnome 0.6* is installed or not. (Maybe if isn't you'll need to do so... I really don't know). Thks!

---

