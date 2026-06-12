---
title: "xfce4 or gdm not using configured Virtual desktop in xorg.conf"
date: 2007-01-21
forum: Desktop Environments
---

### Post by ardya on 2007-01-21
Hi...I'm using xubuntu based on ubuntu 6.10. I'm using xfce4 desktop running from gdm. I have a couple issues I can't find definitive answers for, or resolutions to.

First, I can't seem to cycle through the various supported modes in xorg.conf, though I CAN use every mode in xfce's display settings.

Second, I have a Virtual line set in xorg.conf for the default color depth xorg uses, but it seems to be ignored, by what, or why, I don't know. X.0.log shows nothing wrong.

I know the hardware can handle the Virtual, and supported modes in xorg.conf as I've had a functioning X system using this hardware, and have had working Virtual 1600 1200, using resolutions like 1600x1200, 1280x1024, 1024x768, 640x480.

I don't know if there's something about gdm or xfce4 as shipped w/xubuntu that prevents the Virtual from being used. I tried Windowmaker and I did get the Virtual desktop, but couldn't cycle the resolutions. The default resolution was the one thats listed first in xorg.conf for the default color depth, 1280x1024.

I'm at a loss where to go from here....

---

### Post by ardya on 2007-01-21
Seems xorg was built in some manner that causes a bug that seems to prevent ctrl alt +/- switching. As for xfce ignoring the Virtual setting in xorg.conf, I'll simply use something else.

UPDATE: Not only does xfce ignore Virtual desktop, gnome does too. Virtual desktop does work when using windowmaker and fluxbox.

So why does xfce and gnome behave like this, and is there a fix?

---

### Post by mousehole on 2008-02-07
hi i'm experiencing the same problems on Gutsy, with **Virtual ** settings like (Virtual 2048 1440). i'm had gnome + gdm.
gdm - ignores settings listed under section Screen / Display from xorg.conf
xdm, wdm, kdm - works fine

...
Section "Screen"
        ...
        Defaultdepth    24
        SubSection "Display"
                Modes           "1440x900@60"
                Virtual         2048 1440
        EndSubSection
EndSection
...

---

### Post by mousehole on 2008-02-07
btw startx from terminal (as root and regular user), will set up desktop correctly.

---

