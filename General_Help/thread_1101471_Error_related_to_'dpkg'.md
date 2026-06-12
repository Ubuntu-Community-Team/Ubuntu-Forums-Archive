---
title: "Error related to 'dpkg'"
date: 2009-03-20
forum: General Help
---

### Post by farahf on 2009-03-20
Error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Help please

---

### Post by Therion on 2009-03-20
Open a Terminal.

Cut and Paste the following:

```
dpkg --configure -a
```

---

### Post by taurus on 2009-03-20
Shut down update manager, add/remove, or synaptic if you have any of those apps open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

