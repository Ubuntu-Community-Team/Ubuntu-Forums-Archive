---
title: "Update manager crashes"
date: 2005-10-18
forum: Desktop Environments
---

### Post by silux on 2005-10-18
When trying to run the ubuntu update manager I get the following error ouput on crash (had to run through command line, it would be nice if gnome gave me this).

> 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 874, in ?
    updatemanager.main()
  File "/usr/bin/update-manager", line 850, in main
    self.fillstore()
  File "/usr/bin/update-manager", line 648, in fillstore
    self.initCache()
  File "/usr/bin/update-manager", line 810, in initCache
    apt_pkg.PkgSystemLock()
AttributeError: 'module' object has no attribute 'PkgSystemLock'

Anyone know what that means?

---

### Post by faizulzone on 2005-10-18
i dont know what thats mean.
but i think u should try this

$ sudo dpkg --configure -a

---

### Post by silux on 2005-10-18
running sudo dpkg --configure -a didn't seem to make any difference, at least it didn't fix anything that I knew was broken.  Still can't run update manager and I get the same error.

---

