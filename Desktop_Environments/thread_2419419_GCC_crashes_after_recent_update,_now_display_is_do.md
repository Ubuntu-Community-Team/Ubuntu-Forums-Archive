---
title: "GCC crashes after recent update, now display is dorked"
date: 2019-05-21
forum: Desktop Environments
---

### Post by govee257-7 on 2019-05-21
I'm running 19.04 and after a recent update my display changed to 640 x 480 and gnome-control-center crashes when launched. Display settings also crashes when launched. I reinstalled GCC to no avail. What else can I try? 

Andy

---

### Post by cruzer001 on 2019-05-21
```
sudo dpkg --configure -a && sudo apt -f install
```
That may give you some clues as to what went south.

---

