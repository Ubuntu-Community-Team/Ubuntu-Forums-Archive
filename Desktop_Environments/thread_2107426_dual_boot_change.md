---
title: "dual boot change"
date: 2013-01-21
forum: Desktop Environments
---

### Post by earlgray on 2013-01-21
How to change default OS with a dual boot setup.
It's currently set to boot up with Ubuntu with Windows as the option.

---

### Post by offgridguy on 2013-01-21
> **earlgray said:**
> How to change default OS with a dual boot setup.
It's currently set to boot up with Ubuntu with Windows as the option.
Grub customizer here.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by uniman on 2013-01-22
Hi or the manual way:
edit /etc/default/grub
change GRUB DEFAULT TO = 4 OR 5(depending on the position of the Windows OS in the grub menu)
change GRUB TIMEOUT = 30 to give you more time to select the required OS

---

