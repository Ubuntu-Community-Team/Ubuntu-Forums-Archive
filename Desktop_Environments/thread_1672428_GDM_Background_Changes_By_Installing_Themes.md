---
title: "GDM Background Changes By Installing Themes"
date: 2011-01-20
forum: Desktop Environments
---

### Post by adstro on 2011-01-20
I have recently installed a few new GTK themes and wallpaper packages on Maverick and I noticed that the GDM background also changed.  While I do want to change this back, right now I am more concerned with why this happened simply by installing some new GTK themes.  Can someone point me in the right direction?

---

### Post by Krytarik on 2011-01-21
To change it back, simply copy "/usr/share/applications/gnome-appearance-properties.desktop" into "/usr/share/gdm/autostart/LoginWindow", logout, change the background, log back in, and remove it again.

How that could happen obviously depends on the packages you have installed?!

---

