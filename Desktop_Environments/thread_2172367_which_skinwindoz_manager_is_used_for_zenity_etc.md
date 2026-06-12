---
title: "which skin/windoz manager is used for zenity etc?"
date: 2013-09-04
forum: Desktop Environments
---

### Post by pickarooney on 2013-09-04
I had to reinstall my system this week and since then some apps are displaying with an ugly, square grey control set. One of these is Zenity.
I'm not sure what Qt/GTK/other settings I need to modify to get these to show up with a more attractive theme.

Can anyone help?

---

### Post by tgalati4 on 2013-09-04
Can you post a screen shot?  Yes, it could be Qt, GTK, and other frameworks that are broken.  As far as I know, Zenity is based on GTK2, so at a minimum you need to make sure your gtk2 libraries are properly installed.  You are running Xubuntu 10.10, so I assume that you reinstalled the same version?  Did  you perform the updates?  10.10 is probably End-of-Life, so you need to point your repositories to "old-releases" instead of "archives".

---

### Post by pickarooney on 2013-09-05
[ATTACH=CONFIG]246045[/ATTACH]
Hopefully this is readable. I must update my profile - I'm on 12.04 currently, as I was just before updating.

---

### Post by tgalati4 on 2013-09-05
Looks like Motif widgets from the 80's!  I think you are running GTK1 as a fallback if your GTK2 libraries are messed up.  Bring up *nautilus* and do Help-->About.  What version of Gnome are you running?  Then open a terminal and run *gconf-editor* and look through the file for references to themes.  The easiest way is to use the Find function and search on **theme** and check Key Names and Key Values.

Exactly how did you perform the re-installation?  Did you wipe the partition and start fresh?  Or did you just install over your old installation?

Your system seems broken in a strange way.  One that I suspect will take a lot of time to repair.

---

### Post by pickarooney on 2013-09-06
The hard drive root partition was reformatted and reinstalled from scratch. I think I'm just missing some package or I have a conf file (from a surviving home partition) that points to something that does not exist. It's only a few applications that look like this so not a huge deal if I don't resolve it. I will try what you said tonight though and report back. Thanks.

---

### Post by pickarooney on 2013-09-06
Nautilus is version 3.4.2 but there's no mention of what GNOME version I have. 
I edited a few theme entries in the gconf-editor but maybe I need to reboot to effect the changes?

---

### Post by pickarooney on 2013-09-19
OK, found it - it's a GTK3.0 issue in XFCE.

[http://binbashblog.blogspot.fr/2011/10/manually-change-gtk3-theme-in-xubuntu.html](http://binbashblog.blogspot.fr/2011/10/manually-change-gtk3-theme-in-xubuntu.html)

---

