---
title: "Graphical CVS client for gnome?"
date: 2005-03-10
forum: Desktop Environments
---

### Post by v79 on 2005-03-10
Can anyone recommend a graphical CVS program for the Gnome desktop. I've been using Cervisia, which is very nice granted, but is a KDE application and all that that entails...


On a related note, i want to start writing some gnome documentation for a program I use called alexandria. Can anyone point me in the direction of a good howto for writing Gnome documentation. And while you are at it, send it to the Gnome developers too... I've got Gnome 2.10 and the documentation refers to Gnome 2.6!

Ta

LJD

---

### Post by bigzak on 2005-03-10
[QUOTE=v79]Can anyone recommend a graphical CVS program for the Gnome desktop. I've been using Cervisia, which is very nice granted, but is a KDE application and all that that entails...


On a related note, i want to start writing some gnome documentation for a program I use called alexandria. Can anyone point me in the direction of a good howto for writing Gnome documentation. And while you are at it, send it to the Gnome developers too... I've got Gnome 2.10 and the documentation refers to Gnome 2.6!

Ta

LJD[/QUOTE]
 LinCVS is pretty good, although it's not specifically for Gnome. In fact, it's designed to integrate with ROX, but works standalone too. It supports some cool features include graphically representing the revision history of files, with branches and revisions etc. and lets you easy select any two versions for diff/merge/whatever.

---

### Post by nobodysbusiness on 2005-04-16
I've spent a few hours in the last couple of days trying out different CVS GUIs, and Cervisia is the best one that I've found. I didn't like lincvs or tkcvs, and all the Nautilus scripts were at least a year and a half old, so I don't know if they'll work properly. As far as I know, Cervisia is the best option.

---

### Post by bpilgrim1979 on 2005-05-04
You might take a look at the platform-neutral Java client SmartCVS:

[http://www.smartcvs.com/smartcvs/screenshots.html](http://www.smartcvs.com/smartcvs/screenshots.html)

The "foundation" version is free and there is a similar SmartSVN in the works.

---

### Post by bonifacio on 2005-05-04
gcvs is a gtk base client similar to its wincvs sibling in the windows world.

---

### Post by mambru on 2006-04-20
I'm new to ubuntu. I've been trying to use all the softwares you have previously recommend (cervisia, lincvs and gcvs), but I haven't be able to do it because Synaptics, which is supposed to let me easily install them, doesn't find them. I've already checked the "show disabled software sources" option at Settings/Repositories/Settings and checked all the "Software Sources" on the list... I understand I have all the breezy sources availables for ubuntu. If you can recommend a better sourcelist, that'b great.

I also tried downloading the gcvs deb file from ubuntu, but didn't have good luck either, due to some dependecies problems with libglib and libgtk (I have the 2.0 version, and the 1.2.0 one is required).

I appreciate your help. Thanks in advance.

---

### Post by aouie on 2006-06-15
Dapper (Ubuntu 6.06) has cervisia, gcvs, tkcvs and lincvs modules available. (I haven't tried lincvs as it is changing to non-free crossvc.)
Sincerely,
Aouie

---

### Post by gkearney on 2006-07-25
> **aouie said:**
> Dapper (Ubuntu 6.06) has cervisia, gcvs, tkcvs and lincvs modules available. (I haven't tried lincvs as it is changing to non-free crossvc.)
Sincerely,
Aouie

I am unable to find any of these clients. Where are they and how do you install them?

Greg Kearney

---

### Post by tjombka on 2008-02-10
sudo apt-get install cervisia

---

