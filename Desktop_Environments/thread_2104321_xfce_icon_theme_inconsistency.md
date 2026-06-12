---
title: "xfce icon theme inconsistency"
date: 2013-01-12
forum: Desktop Environments
---

### Post by jacksockboy on 2013-01-12
Hello I am running xubuntu 12.04 and I am having a very hard time getting the icon theme that I choose to be universal.  What I mean by this is that the icon for a given application is different in the menu than it is in the task bar.  The two applications that I have noticed this on are synaptic and geany.  I understand that applications that run as root need to set their icons specially so I have tried some of those techniques but I can't figure out why geany wouldn't work.  I have tried creating gtkrc, gtkrc-2.0, gtkrc-3.0, gtkrc-4.0, setting the themes through the xfce4-settings manager, using sudo xfce4-settings manager, using gtksudo xfce4-settings manager, creating a .icons folder in my home directory, creating a .icons folder in the root directory, and copying themes into /usr/share/icons.  

This picture highlights my problem.

[http://ompldr.org/vY2cxeg](http://ompldr.org/vY2cxeg)

---

### Post by Frogs Hair on 2013-01-13
You may want to check usr/share/pixmaps and usr/share/apps for inconsistent icon images. If the program uses an image from pixmaps changes will revert if the program updates.

---

### Post by jacksockboy on 2013-01-13
geany is not in /usr/share/apps but there is a geany.xpm file in /usr/share/pixmaps but I have no idea how to interpret the file.  Also what do you mean by changes will revert if the program updates?  I can't get the icon theme to be consistent even if I try and set it after an update.

---

