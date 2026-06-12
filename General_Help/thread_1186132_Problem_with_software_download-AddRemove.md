---
title: "Problem with software download-Add/Remove"
date: 2009-06-13
forum: General Help
---

### Post by GCkid7 on 2009-06-13
I have problem on Ubuntu 9.04 when I try to download software from Applications -  Add/Remove, windows prompt saying:


"An error occurred"
The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Can someone please help, also I can't download anything from Synaptic Package.

---

### Post by _Purple_ on 2009-06-13
Open terminal (Application > Accessories > Terminal) and type
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by GCkid7 on 2009-06-13
Thanx it works

---

