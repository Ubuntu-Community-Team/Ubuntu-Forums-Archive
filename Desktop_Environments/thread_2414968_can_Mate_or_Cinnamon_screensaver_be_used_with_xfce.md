---
title: "can Mate or Cinnamon screensaver be used with xfce4?"
date: 2019-03-18
forum: Desktop Environments
---

### Post by antitna on 2019-03-18
Hello all,

I just installed the latest Ubuntu Studio.  It gave me Xfce version 4.12.  So I go to Ubuntu menu | Software, and I search for "screensaver", and I find screen savers that describe themselves as being for Mate, Cinnamon, UKUI, X11, etc. But I don't find any XFCE screensaver.  

So my question is, how can a Mate or Cinnamon screensaver be compatible with XFCE?  What is the significance of this?  Does my XFCE desktop have to run a Mate emulator in order to use the Mate screensaver?

Thanks!

---

### Post by Dennis N on 2019-03-18
Xubuntu 18.04 and I presume Ubuntu Studio (also uses xfce4 desktop) by default use Light Locker which provides only a blank screen and not graphical screensavers. If you want graphical screensavers as in Mate screensaver, you would install xscreensaver and the related screensaver packages. There is no real difference in how xscreensaver and Mate screensaver look and function.

To have a full set of screensavers, you need to install:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

You wil need to add xscreensaver to startup applications. The command is **xscreensaver -nosplash** Also disable light locker in startup applications (where it is listed as 'Screen Locker').

---

