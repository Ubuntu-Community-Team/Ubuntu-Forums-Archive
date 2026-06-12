---
title: "kscreensaver shifted vertically"
date: 2005-12-13
forum: Desktop Environments
---

### Post by NutMonkey on 2005-12-13
I have some problems with the KDE screensaver.  The main one is that the screensavers that I can get to run are shifted up so that they only cover the top third of the screen, the bottom 2/3 is black.  I see this on both my work PC and my home PC (which are different hardware).  I'm currently seeing this in KDE 3.5 but also saw it in 3.4.

I'm not opposed to using xscreensaver, but how do I configure the "Lock Session" button to run xscreensaver instead of kde screensaver?

---

### Post by staticx0085 on 2005-12-13
I had the same problem, but from another thread ([http://ubuntuforums.org/showthread.php?t=81288](http://ubuntuforums.org/showthread.php?t=81288)) I installed the package xorg-driver-fglrx using apt-get and it fixed the vertical shift problem.  The OpenGL screensavers were very choppy after this, but that may be a result of my video card drivers (or lack of).

-Ken

---

### Post by NutMonkey on 2005-12-14
Thanks for the reply.  I don't have an ATI card (i865) so that doesn't help me though.  But I did find the kscreensaver-xsaver package which lets me use the xscreensavers through kscreensaver, and those seem to work ok.

---

