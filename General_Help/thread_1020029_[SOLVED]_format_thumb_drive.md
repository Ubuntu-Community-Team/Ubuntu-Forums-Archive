---
title: "[SOLVED] format thumb drive"
date: 2008-12-23
forum: General Help
---

### Post by knightstar76 on 2008-12-23
Simple question.... Is there a way to re-format my USB Thumb Drive in Ubuntu?

---

### Post by plucky on 2008-12-23
> **knightstar76 said:**
> Simple question.... Is there a way to re-format my USB Thumb Drive in Ubuntu?


From a terminal.

```
sudo apt-get install gparted
```

Then open **System > Administration > Partition editor** and select your thumb drive,delete whatever partitions are there and then recreate a vfat partition.

---

### Post by knightstar76 on 2008-12-23
I tried the code but I get the folllowing error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Any sugustions?

---

### Post by oilchangeguy on 2008-12-23
in the terminal type sudo dpkg --configure -a and press enter. you should be able to right click on the thumb drive and select format.

---

### Post by knightstar76 on 2008-12-23
Thank You...:D This worked perfectly and solved my problem. ):P

---

