---
title: "Kernel Panic"
date: 2005-12-22
forum: General Help
---

### Post by bigblop on 2005-12-22
I was told that it should be possible to move ubuntu to another machine (installed Ubuntu on disk A that I have now put in another machine with winXP on the primary disk).

I have sucessfully made the grub menu work so I can choose between Ubuntu and winXP.

But when I boot Ubuntu I get this error:

Starting Ubuntu...
pivot_root: no such file or directory
/sbin/init: 428: cannot open dev/console: no such file
kernel panic - not synching: attempted to kill init.


Is there a solution so I don't need to reinstall?

---

### Post by BathroomNinja on 2005-12-22
It looks like it's not seeing the image correctly.

Tell me exactly what you did.  Did you simply remove the HD from computer 1, and put it inside computer 2?  If so, your /etc/fstab may now be invalid.  While the HD was in Computer 1, was it the ONLY drive?  And now it's the secondary?   If so, I'm pretty sure it's an fstab problem.



EDIT- I really suck sometimes.

---

