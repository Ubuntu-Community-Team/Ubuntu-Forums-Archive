---
title: "GNOME split screen/hall of mirrors"
date: 2010-03-20
forum: Desktop Environments
---

### Post by Surlent777 on 2010-03-20
Well, it's as weird as it sounds. I was using GNOME normally, and had Chromium maximized. I restored it, and somehow this split the desktop. Windows can still maximize and cover the hole, but the desktop itself is split. Removing ~/.gconf and ~/.gconfd did nothing, nor did switching to Metacity. KDE, Fluxbox, and Enlightenment are unaffected. I'm really not sure where else to look config file wise. Any suggestions would be heartily appreciated.

[http://img715.imageshack.us/img715/4156/gnomehom.png](http://img715.imageshack.us/img715/4156/gnomehom.png) Here's a visual. Notice that my cursor is on the right side of the screen and that Places isn't selected...the menu and "explosion" on the left should not exist.

---

### Post by breel81 on 2010-03-21
Yea, I got the same problem. I thought it had something to do with changes I made to cmplz fusion. I followed instructions on how to get the snapping windows like in win7. But I undid all those changes and still have the split. Hope somebody knows the solution.

---

### Post by Surlent777 on 2010-03-21
If it's not a GConf issue, my second guess would be that it's a Nautilus config issue, seeing as Nautilus draws the Desktop, but this would be assuming that Nautilus has some settings outside of GConf. Also, while you CAN get the Aero-like effect you're after under Compiz, it's really not worth it, because it's buggy and unstable. I have tried it myself. If you're looking for a stable version of that effect, try the latest KDE, as KWin recently got some nice enhancements.

---

### Post by Surlent777 on 2010-03-21
I notice that as I'm logging out, as soon as the panels disappear and the windows disappear the wallpaper looks totally normal. I'm not sure what this means though.

---

### Post by soltanis on 2010-03-21
Whoa cool.

So does this happen every time you start a new session? Have you tried disabling compiz, logging out then logging back in?

Compiz has this really great habit of screwing things up without fail.

---

### Post by Surlent777 on 2010-03-21
I thought I had tried disabling Compiz, but after logging out just to be sure, it was back on. Annoyed, I logged out, renamed my .compiz folder, logged in, and it was fixed. That, and by some deep and spiritual magic (or possibly gconf) all my settings were still preserved. Go figure. =/ Compiz is such a jerk sometimes. Thanks for the help.

---

