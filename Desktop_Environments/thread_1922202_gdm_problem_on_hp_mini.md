---
title: "gdm problem on hp mini"
date: 2012-02-08
forum: Desktop Environments
---

### Post by mgermaine8 on 2012-02-08
I accidently removed gdm, and since I reinstalled it, it fails to start with the message "There already appears to be an X server running on display :0.....".  No combination of /etc/init.d/gdm restart or startx fixes this.  After a fresh reboot, I did a ps and found two gdm's running.  Here is the output:

4542 /usr/sbin/gdm
4549 /usr/bin/X
.
.
.
4853 /usr/sbin/gdm
4856 /sbin/dhclient
4917 /usr/lib/gdm/gdmopen

If I kill -2 either of the gdm's, the window manager still does not start, and I can't even get back to my F1 console. I also tried dpkg-reconfigure gdm to no avail.  Can anyone tell me how to fix my configuration?

---

### Post by searchfgold6789 on 2012-02-08
Try a ```
sudo dpkg-reconfigure xserver-xorg
```too...

---

### Post by mgermaine8 on 2012-02-08
Unfortunately that didn't help.  So gdm starts up, kicks of X, then a second later it starts again and fails because X is already running.  There must be a file somewhere that is starting gdm one time too many.  Any ideas?

---

### Post by mgermaine8 on 2012-02-09
I found out that if I kill off gdmopen, the second gdm, X11, and then the first gdm, in that order, I can then do an /etc/init.d gdm start,  and I get all four processes back again: gdm, X11, gdm, gdmopen.  And the error about the  x server already running pops up as well.  Does that mean that gdm starts the x server, and then the xserver starts gdm?  Could this be a misconfiguration of X rather than gdm?

---

### Post by mgermaine8 on 2012-02-10
I just reinstalled the operating system, and that took care of it.

---

