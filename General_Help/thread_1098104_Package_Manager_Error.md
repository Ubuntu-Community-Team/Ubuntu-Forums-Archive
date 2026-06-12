---
title: "Package Manager Error"
date: 2009-03-16
forum: General Help
---

### Post by digital-daniel on 2009-03-16
I crashed during an update and received an error from my package manager. Tried following some threads and now have a new error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I sudo dkg --configure -a

I get 
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 EOF after field name `24x24/stock/generic'

I  deleted my status file in dpkg and renamed the the status old to status.
Can someone help me.

Daniel

---

### Post by yaroto98 on 2009-03-16
If you're getting an EOF error, I'd delete everything in the /updates folder, and let the package manager re-download it. Obviously before trying this, make a copy first

```
sudo cp -r /var/lib/dpkg/updates /tmp

sudo rm -rf /var/lib/dpkg/updates/*
```

---

### Post by stargate2500 on 2009-03-18
Thanks for the code 

root@ray-desktop:/home/ray# sudo cp -r /var/lib/dpkg/updates /tmp
root@ray-desktop:/home/ray# sudo rm -rf /var/lib/dpkg/updates/*

---

