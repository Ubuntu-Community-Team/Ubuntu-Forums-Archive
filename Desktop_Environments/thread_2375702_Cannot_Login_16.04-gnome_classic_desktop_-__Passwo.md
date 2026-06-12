---
title: "Cannot Login 16.04-gnome classic desktop -  Password Request Looping"
date: 2017-10-26
forum: Desktop Environments
---

### Post by mark bower on 2017-10-26
System: 16.04.03,32 bit, AMD graphics card, using native video driver from install software, gnome classic desktop (gnome-session-flashback).  After installation, the login option was changed to Automatic Login in Sys>Users.

Backgrnd:  System worked flawlessly for days, best ever in function and appearance.  In process of trying different case fans, I booted with HD disconnected.  (Not sure, but may have reconnected HD in this state; versus shutting down, reconnecting HD, then rebooting)  Login problem subsequently occurred.  So system boots to Guest Session login.  After the correct passwd is entered, things appear to proceed normally, but then the same login screen reappears.  An incorrect passwd entry immediately presents a small error msg in red.

What I have tried using the virtual console (Alt-Ctl-F1):
	Removing .Xauthority and rebooting
	Removing .Xauthority plus .ICEauthority and rebooting
	Looked at permissions of /tmp (which are drwxrwrwt 15 root root and supposedly o.k.)

I see another proposed step which is to reconfigure lightdm, but choose not to do that yet pending responses to this request for help.  I also did cat .xsession-errors; the only error is “cannot connect to brltty at: 0.  In summary, something got corrupted, but it was not due to any software manipulations.

If anything said seems erudite, I am not.  Looking for very clear, complete suggestions to try.  Thanks.

---

### Post by mark bower on 2017-10-26
o.k. My 16.04.03 with gnome-classic-desktop is booting again via autologin.  This is what I did starting on the login screen:  1) Ctl-Alt-F1, 2) cd /etc/lightdm/, 3) cat lightdm.conf, 4) Alt-F7.  And the system booted.

I do not consider this solved as the resetting of the system per above makes no sense.  Just looking at a file should not change anything.  What is really peculiar is that the lightdm file does not appear as normal.  What the heck is [Seat *]?  The complete lightdm.conf file is,
```
[Seat: *]
autologin-user=mark
```

---

