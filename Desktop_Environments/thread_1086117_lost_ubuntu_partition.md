---
title: "lost ubuntu partition?"
date: 2009-03-03
forum: Desktop Environments
---

### Post by vegetanks89 on 2009-03-03
i had a dual boot partition with windows on one and ubuntu 8.10 on another. i recently reformatted the windows partition and now when my pc turns on it does not show me the boot screen to choose which operating system i want to run. now i am wondering was my ubuntu partition lost is the boot screen deactivated or something along that line?

---

### Post by agim on 2009-03-03
Boot with your live cd. Look for your Ubuntu partition with GParted.
If its there, use this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by taurus on 2009-03-03
Boot your machine with Ubuntu LiveCD.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by vegetanks89 on 2009-03-03
thanks a lot.

---

### Post by andrea000 on 2009-03-04
You can also use [COLOR="black"][COLOR="Red"]Super Grub Disk [/COLOR][/COLOR]i had the same problem.
here is the address it should fix your partition.

 [http://stmaarten.globat.com/~supergrubdisk.org/](http://stmaarten.globat.com/~supergrubdisk.org/)

---

