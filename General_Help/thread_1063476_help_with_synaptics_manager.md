---
title: "help with synaptics manager"
date: 2009-02-07
forum: General Help
---

### Post by mikeonthebeach on 2009-02-07
anytime i click the synaptics manager this error message comes up


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone tell me how to fix this

---

### Post by Tim Sharitt on 2009-02-07
Open a terminal (Applications > Accessories > Terminal) and enter
```
sudo dpkg --configure -a
```

Then enter you password when promped.

---

