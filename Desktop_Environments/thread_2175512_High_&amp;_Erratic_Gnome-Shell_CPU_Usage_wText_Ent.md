---
title: "High &amp; Erratic Gnome-Shell CPU Usage w/Text Entry Issues"
date: 2013-09-19
forum: Desktop Environments
---

### Post by buzzingrobot on 2013-09-19
I've begun to see high and rapidly changing CPU usage from /usr/bin/gnome-shell on an Ubuntu Gnome installation.  This is 13.04 that's been upgraded to 3.8 via the gnome3-team/gnome3/ubuntu raring PPA.  I haven't added anything from staging.

With htop running in a terminal, and no other open applications, gnome-shell CPU usage bounces erratically every few seconds in a range from a single digit to above 100%, with stops in between.

Eventually, this is accompanied by very slow and sputtering text input, in any app.  E.g., I enter a string of characters on the keyboard.  They do not appear on screen.  A few seconds later, the entire string appears.  It's as if the characters are being buffered.

Rebooting seems to be a temporary fix to the text input issue, but not gnome-shell's CPU usage.

This is on a ThinkPad W530, 32 gigs, using Ivy Bridge Intel video. Gnome-Shell is 3.8.3.

---

### Post by odd-oddied on 2014-02-01
Same thing here. Ubuntu 13.10, Gnome-shell 3.8. Thinkpad X200t, intel video.
It's not text-inputs that get laggy - every input (keyboard / mouse / touchscreen) lags. Sometimes mouse clicks doesn't work because i clicked during the high CPU jump moment. When I grap a window and move it across the screen it's obvious that whole system freezes (including that moving window) every ~second or so for few miliseconds. Restarting gnome-shell via ALT+F2: r or logging-out solves problem for some time.

Anyone else has this problem?

---

