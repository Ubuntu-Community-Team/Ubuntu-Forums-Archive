---
title: "Mounting the master hdd?"
date: 2006-01-09
forum: General Help
---

### Post by s_spiff on 2006-01-09
hey, I have a 120 gb hdd, with the ubuntu installed on the 80 gb slave hdd. The 120 gb hdd has 6 partitions, all fat32. Is there a way I can do something , so that its mounted at boot up? with the freedom to read/write and execute stuff from it? 
I boot into linux via the 80 GB, changing the second boot device to HDD 1.

---

### Post by lisje on 2006-01-09
here's what I've put in my fstab (/etc/fstab) to mount my windows partition on boot:

```
/dev/hda1       /media/hda1    vfat  iocharset=utf8,umask=000,defaults,noatime,user        0       0
```

I don't know if it can help you. Since you don't really specify what kind of harddrives you've got ... 
greetings,
Lisje

---

