---
title: "Dual Booting Windows 98se and Ubuntu"
date: 2006-09-27
forum: Desktop Environments
---

### Post by fitzilee on 2006-09-27
I have an older P3 500mhz, 512mb system.  I used to use Windows 98se, but a few months ago I switched over to ubuntu and installed it on a seperate hard drive, but I didn't dual boot I just took out the Windows 98 hard drive and put in a new one.  I now would like to dual boot.  I have Windows 98se on one hard drive and Ubuntu on another.  I really don't want to have to reinstall either of the operating systems is there any way to setup a dual boot now?

Any help is appreciated 

Tks
Mike

---

### Post by louieb on 2006-09-27
I assume these are eide drives
Leave Ubuntu drive as master drive.
Install windows drive as slave.
add the following to the end of /boot/grub/menu.lst :

```
title Win 98
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      chainloader +1
      makeactive
      boot
```
The first time I installed Linux on a pc I wanted to make sure the windows drive didn't get messed up so I unpluged it before installing Linux. After the install I pluged it back in. It worked for me.

---

### Post by almrking on 2006-09-27
Do as louieb says. I have the same setup using W2000 Pro instead and it works fine.

---

