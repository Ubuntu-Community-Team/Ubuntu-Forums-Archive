---
title: "X won't start, cant access Bash"
date: 2005-11-28
forum: Desktop Environments
---

### Post by adamb10 on 2005-11-28
On the bootup process with GDM is about to start... it doesn't.  Xorg says it cant start and will kill X.  Well thats the problem, it won't and neither can I.  When it trys to kill itself all I get is a black screen with a _  I tried to kill it myself but nothing happens.  Hell, Ctrl-Alt-Delete to reboot doesn't work either!

---

### Post by Leif on 2005-11-28
try logging in using safe mode, then do "sudo dpkg-reconfigure xserver-xorg". if you know the correct settings, use them, otherwise, use some conservative settings, and try again.

oh, and before any of this, do a "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup". sure, it doesn't work, but it never hurts to backup

---

