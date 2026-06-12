---
title: "Gnome panel/environment load error"
date: 2009-09-22
forum: Desktop Environments
---

### Post by mullenrbock on 2009-09-22
Just recently I turned on my laptop to find this error, after months of 9.04 working fine, and me doing no tweaks to any config files:

> 
GConf Error: Failed to contact configuration server; some possible
causes are that you need to enable TCP/IP networking for ORBit, or you
have stale NFS locks due to a system crash. See
[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information.

No panels show up, only this one error, making it impossible to do anything. 

This just happened suddenly. I'm using fluxbox right now as a workaround, but I'm thinking about reinstalling entirely. It also has errors about how gnome-power-manager has been incorrectly installed, even though it's been fine for months. Anyone else have this problem? Are there any fixes?

Thanks.

---

### Post by arrange on 2009-09-22
Can you post the contents of directories *~/.gconfd/* and *~/.gconf/* and any references to *gconf* in */var/log/user.log*, for example by typing into Terminal```
ls -l ~/.gconfd/
ls -l ~/.gconf/
grep gconf /var/log/user.log
```?

---

