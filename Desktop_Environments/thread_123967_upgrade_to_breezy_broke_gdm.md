---
title: "upgrade to breezy broke gdm?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by linuxgrrl on 2006-01-31
hi,
I upgraded from hoary to breezy last night by changing my repos and doing "apt-get upgrade" and "apt-get dist-upgrade".

Now gdm will not start.  The first thing I noticed is that gdm package had mysteriously vanished, which I fixed with "sudo apt-get install gdm."  

Now the error gdm gives is that "/etc/X11/X is not executable." I checked the permissions of that file, which are fine, but the file is actually a link to /usr/bin/XFree86, which does not exist.  
Anyway, doesn't ubuntu use xorg, not XFree86?  I tried "sudo apt-get install xorg," but it said I already have the latest version of that.  I scrolled through /usr/bin in the hopes of finding an xorg executable to point at, but either it's not there, or (more likely) I didn't recognize it.

Stupid question, but what is the executable called?  I searched my errors on the forum but didn't find anything.
thanks.

---

### Post by linuxgrrl on 2006-02-01
Okay, it turns out the answer was here:
[http://www.ubuntuforums.org/showthread.php?t=56066&highlight=%2Fetc%2FX11%2FX+executable](http://www.ubuntuforums.org/showthread.php?t=56066&highlight=%2Fetc%2FX11%2FX+executable)

---

