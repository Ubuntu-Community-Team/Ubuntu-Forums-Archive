---
title: "General Upgrade Error Message - Help"
date: 2009-01-31
forum: General Help
---

### Post by kmatousek on 2009-01-31
Receiving this error when trying to run system upgrades:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

E: _cache->open() failed, please report.


Any suggestions?

Thanks.

---

### Post by taurus on 2009-01-31
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kmatousek on 2009-01-31
thanks taurus -

What are the differences between the Alt + F2 Command and Terminal Manager?

---

### Post by taurus on 2009-01-31
Just two different ways to bring up a terminal.

---

