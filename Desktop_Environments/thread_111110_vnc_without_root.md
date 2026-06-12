---
title: "vnc without root"
date: 2006-01-01
forum: Desktop Environments
---

### Post by marks_linux on 2006-01-01
For some reason I can only connect to my ubuntu server (running headless) when I start vncserver using sudo.

This means that when I use vncviewer fomr my other ubuntu box I end up with a root session. Is there any way to make it so I can log in as a normal user?

As said the server is headless and really I want the vncviewer session to present me with a login screen. I've followed various how-tos and can't get much further.

---

### Post by zoiks on 2006-01-01
Do you get any error messages or anything in vnc's log files when you enter something like "vncserver :3" at the command prompt (as a regular user)?  Do the logs contain any authentication errors when you attempt to connect?  (You should of course set up a password when you first run vncserver.)  I would think unless you have a firewall issue, vncserver shouldn't have a problem opening up a port at 59xx.

Of course I haven't done this in ubuntu, just other distro's, so maybe ubuntu is set up differently.

---

### Post by marks_linux on 2006-01-01
No errors in the log. Yep I created a password when setting up vncserver and am asked for this whenever I connect.  When started non root when I connect I get a grey GUi screen with a X for a pointer. when I start vncserver with sudo when conecting I go straight to a a GUI desktop complete with menus,mouse etc. again no login screen.

I've read so many set up guides I've lost the plot. the last I've followed is [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638)

And as far as I can tell be setup matches this how-to.

M

---

### Post by pharcyde on 2006-01-01
It sounds like the x session for your non-root server is not setup properly.  You can try copying your .vnc folder from the /root directory to your ~ dir.  After that try starting vnc server as your non-root account.

You can also look at the configuration differences between the files in those directories and see if you see anything out of place.

You could also post your startx file from the .vnc directory here and see if anyone sees a problem.

---

