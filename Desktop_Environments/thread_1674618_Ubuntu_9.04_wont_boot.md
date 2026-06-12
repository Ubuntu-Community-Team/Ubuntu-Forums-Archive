---
title: "Ubuntu 9.04 wont boot"
date: 2011-01-24
forum: Desktop Environments
---

### Post by viperce on 2011-01-24
Hi i need help please...
 
My computer wont boot after i ran updates, im getting this error.
 
init: ureadahead main process (386) terminated with status 127
mountall: error while loading shared libraries: libudev.so.0: cannot open shared
object file: No such file or directory
init: mountall main process (387) terminated with status 127

---

### Post by MooPi on 2011-01-24
I believe the solution is here.[http://ubuntuforums.org/showthread.php?t=1309423]("http://ubuntuforums.org/showthread.php?t=1309423")
Possible other solution is to enter grub and use the root console to do the same as listed in link.
```
apt-get update
apt-get dist-upgrade
dpkg --configure -a
``` 
To enter grub at boot either depress Esc key or Shift key just after bois flash. I listed two options due to a change from Grub to Grub2.

---

