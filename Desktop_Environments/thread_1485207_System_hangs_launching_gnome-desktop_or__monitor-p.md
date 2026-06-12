---
title: "System hangs launching gnome-desktop or  monitor-powersaving test"
date: 2010-05-16
forum: Desktop Environments
---

### Post by jczernia on 2010-05-16
Hi
I did update to 10.04 and now system hangs (looks like hangs but the screen is black and can't do anything else) launching gnome-desktop. I am able to log in in recovery low resolution mode 
10.04 kernel 2.6.32-22-generic (recovery mode)
 and selecting 
failsafeX mode
[FONT=Verdana] Browsing launch errors I see:
[/FONT]Fatal Server error:
server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock and start
again


(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETSTATE failed: Bad file descriptor
ddxSigGiveUp: Closing Log

When I do the Ubuntu HW tests, system hangs on monitor-powersaving test.
I am using old Toshiba laptop with 
Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Any help will be much appreciated. Thank you in advance
brgds
Jacek

---

### Post by jczernia on 2010-05-17
I found or suppose the X server issue
Running form command line
X -configure
and
X -config ...../xorg.conf.new
System hangs with black screen.
Any ideas how to debug the issue? How to get the log? And where post the log for help?
I tried to re-install core xorg but no changes.
jacek

---

