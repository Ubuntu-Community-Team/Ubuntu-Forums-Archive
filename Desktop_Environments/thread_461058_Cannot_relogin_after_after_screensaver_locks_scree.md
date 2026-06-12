---
title: "Cannot relogin after after screensaver locks screen"
date: 2007-06-01
forum: Desktop Environments
---

### Post by caliskan on 2007-06-01
I have Ubutu 6.06.  All packages are kept up to date.  The screensaver is fixed to the "blank" option and configured to lock the screen after 10 minutes.  My problem is that, about 30% of the time,  if I leave work and try to relogin the next morning, the login prompt will not appear.  I can see the mouse pointer moving around in a completyely dark screen, and the computer is not frozen.  At this point, I can switch to console 1 through CTRL+ALT+F1 and restart GDM with "/etc/init.d/gdm restart", but this is not desirable because I loose all my open applications.

If the screen remains locked for a brief time only (up to one hour) the problem rarely, if at all, occurs.

Is there any way to force the locked screen login prompt to appear?  Any other possible solution to this problem?

---

### Post by caliskan on 2007-06-25
I found a solution to my own problem.  First I switch to console 1 (CTRL+ALT+F1), then login as root, and then execute command "killall gnome-screensaver."  This kills the offfending gnome screensaver program and returns the user to the desktop upon switching back to the GUI console (CTRL+ALT+F7).

---

