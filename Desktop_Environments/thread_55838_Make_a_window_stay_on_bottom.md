---
title: "Make a window stay on bottom"
date: 2005-08-10
forum: Desktop Environments
---

### Post by rwabel on 2005-08-10
I'm just wondering if it's possible to make window stay on BOTTOM instead of on TOP in GNOME?
If that's not possible in GNOME, is there a similar approach for something like that. It woul make Gimp much better to use

---

### Post by coolclassic on 2005-08-10
With KDE you can select keep below other. I imagine the same function is in gnome. Just right click on title bar and make your selection. Gimp has the same function in KDE.

---

### Post by rwabel on 2005-08-11
[QUOTE=coolclassic]With KDE you can select keep below other. I imagine the same function is in gnome. Just right click on title bar and make your selection. Gimp has the same function in KDE.[/QUOTE]
 that's the problem with gnome, there is no such feature when I right click on the title bar :-(

btw: very strange, why didn't I receive an email that someone replyed to my entry?

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=rwabel]that's the problem with gnome, there is no such feature when I right click on the title bar :-([/QUOTE]

Metacity doesn't support "Always keep below" by default. You can use [Openbox with GNOME instead](http://ubuntuforums.org/showthread.php?t=34239&highlight=openbox+gnome) and get what you want.

---

### Post by rwabel on 2005-08-11
[QUOTE=Stormy Eyes]Metacity doesn't support "Always keep below" by default. You can use [Openbox with GNOME instead](http://ubuntuforums.org/showthread.php?t=34239&highlight=openbox+gnome) and get what you want.[/QUOTE]
 ahh that's why. Thanks for the info. I've to give openbox a try. Don't understand why metacity doesn't implement such a feature. maybe they will have it in another release. I hope :-)

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=rwabel]ahh that's why. Thanks for the info. I've to give openbox a try. Don't understand why metacity doesn't implement such a feature. maybe they will have it in another release. I hope :-)[/QUOTE]

Don't count on it. Havoc Pennington, the guy who wrote Metacity, thinks that all a window manager should do is draw the frame, provide close/maximise/iconify functionality, and let you decide which desktop the window should be on. Everything else, according to him, is [crack](http://gnomedesktop.org/scr/Metacity-README.txt) and should be handled by other tools. 

If you wanted to extend Metacity instead of replacing the damned thing, try **sudo apt-get install devilspie**; it allows you to perform various actions on windows of a given type. For example, you could use Devil's Pie to make sure that Firefox always opens maximised on the fourth workspace.

---

### Post by rwabel on 2005-08-11
thanks for the tip! I've tried it out a bit, but I didn't achieve to make the main gimp window stay always below. Anyone has configs for it?

---

### Post by rwabel on 2005-08-11
I wanted that feature especially for GIMP. I've now tried the latest version from CVS and they have implemented a nice feature to dock the toolbox and stuff to the image window. That's doing the job now pretty well

---

