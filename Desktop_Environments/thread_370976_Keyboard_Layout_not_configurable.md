---
title: "Keyboard Layout not configurable"
date: 2007-02-26
forum: Desktop Environments
---

### Post by Metallinut on 2007-02-26
I recently installed kubuntu-desktop over my Gnome installation.  (Edgy 6.10)  When I got in, I noticed my Windows key wasn't acting as Super.  In Gnome I was able to choose my keyboard layout in system preferences.  I was told that I can do the same in the Regional & Language settings in KDE's system settings.  However, when I go there, the drop down list that should contain all the selectable keyboard layouts is completely empty! 

What's going on?  Am I missing an installation file or something?

---

### Post by amanita on 2007-02-26
Absolutely the same problem here. On my desktop PC and KDE I am able to change layout to any language I want but the same thing in KDE on my  laptop I am not able to do and Keyboard Layout utility is not working for me. In Gnome there isn't problem at all :(

---

### Post by j.miller565 on 2007-02-28
I´m having the same problem. Can anyone help us?

---

### Post by Metallinut on 2007-02-28
Big Bump for this one guys.

I wound up reinstalling, straight from a kubuntu live CD.  6.10.  When booted to the Live CD, the regional & language settings -> keyboard layout worked.  I saw a bunch of layouts listed that I could choose from.

Now that I've installed Kubuntu, I went to those same settings, and gonzo.  Gone again.  What the heck is going on?

---

### Post by Metallinut on 2007-03-01
Hey guys, I got help from khedron on another thread.

Check to see if /usr/share/X11/xkb is empty.  If it is, you want to run:
```
sudo cp -a /etc/X11/xkb /usr/share/X11
```
To copy the contents over.  After I did that, all the keyboard layouts were listed.

Hurrah!

---

