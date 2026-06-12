---
title: "Launch a script in xterm globally when users login to Gnome"
date: 2009-04-29
forum: General Help
---

### Post by GreenTentacle on 2009-04-29
Hi,

I have a script that I am trying to place so that when someone logs into the system it launches an x-term window that launches my script after logging into Gnome.

I have been searching the internet for the past 2 days and I'm a little confused, I have tried many suggested solutions, but none seemed to have worked.

Currently running Jaunty 9.04

Any help would be much appreciated!

Thanks.

-GT

---

### Post by GreenTentacle on 2009-04-29
-Bump

Thanks :)

---

### Post by Brandon Williams on 2009-04-29
Try adding the command you want to run to /etc/X11/Xsession.d/99x11-common_start immediately before the 'exec $STARTUP' line. Make sure that you background your command so that the exec $STARTUP line will still run.

---

### Post by GreenTentacle on 2009-04-30
Thanks! Will try it now :)

GT

---

