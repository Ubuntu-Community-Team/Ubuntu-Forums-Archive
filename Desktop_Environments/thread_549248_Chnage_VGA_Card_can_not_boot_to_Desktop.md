---
title: "Chnage VGA Card can not boot to Desktop"
date: 2007-09-12
forum: Desktop Environments
---

### Post by moonhk on 2007-09-12
Hi All
Today, I change to other VGA Card, then My Ubuntu can not able to boot into desktop. Which command need to run in order to reconfig the VGA card ?

Moonhk

---

### Post by swisscow on 2007-09-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

is the one i think you are looking for

---

### Post by moonhk on 2007-09-13
Thank.
I am using below command. All items .last than 10 min to complete
sudo dpkg-reconfigure -a

moonhk

---

