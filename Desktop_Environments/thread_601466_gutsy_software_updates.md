---
title: "gutsy software updates"
date: 2007-11-03
forum: Desktop Environments
---

### Post by robeec on 2007-11-03
when i go to install updates delivered to my desktop, i get  this:
"E: dpkg was interrupted, you must manually run "dpkg --configure-a" to correct the problem.
E: _cache->open()failed, please report"

anybody know what this means?
thanks,
robby

---

### Post by taurus on 2007-11-03
It means that you have a broken package.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure-a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by robeec on 2007-11-03
the update you gave me for the terminal seemed to go smoothly. but the updates still wont install. i get the same message.

thanks for helping.

---

