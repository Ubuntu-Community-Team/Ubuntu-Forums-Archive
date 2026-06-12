---
title: "xubuntu mounting broke"
date: 2006-12-04
forum: Desktop Environments
---

### Post by guruofquality on 2006-12-04
My auto-mounting/hotplug mounting randomly broke in xfce. I really dont know what I did. 

I tried to completely remove xfce and reinstall all the packages (this did not work). I can use gnome-volume-manager, except gnome-volume-manager doesnt put the mount icons on the desktop or in the Thunar panel (making ejecting usb sticks no-fun). There has to be something i can do short of reinstalling the OS from scratch. 

Does anybody know the name of the package that actually controls the auto-mounting in xubuntu? I could try reinstalling that or compiling it from source, anything really.

---

### Post by ajgreeny on 2006-12-04
Try reinstalling all of xubuntu-desktop if you didn't do it that way last time.  If you just looked for xfce packages by name you may have missed something.

---

### Post by guruofquality on 2006-12-04
> **ajgreeny said:**
> Try reinstalling all of xubuntu-desktop if you didn't do it that way last time.  If you just looked for xfce packages by name you may have missed something.

I installed xubuntu-desktop this time. It installed more packages but auto mounting is still broken. :( 

Lookin around mounting solutions...can ivman make the desktop icons with the eject options?

---

### Post by ajgreeny on 2006-12-04
What about pmount?  Could this be the problem?

---

### Post by guruofquality on 2006-12-04
pumount and pmount work just fine as user. I wonder if there is some issue with a library path (bound to happen with fresh installs) 

I have been trying to figure out what binaries are run when an automount occurs and maybe see some debug errors on the command line. I also checked various logs for these kind of errors, but maybe im lookin at the wrong logs?

---

### Post by naelphin on 2006-12-23
I have this problem too. It stopped automounting in xubuntu 6.06. It even dosen't show up in the desktop/thundar. Ivman/gnome-volume don't help either.

---

