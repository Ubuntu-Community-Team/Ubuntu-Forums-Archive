---
title: "Minor problem with secondary partition"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Dillius on 2005-11-29
I have a partition on another hard drive that I'm trying to access using the Disk Management tool in Gnome. It is telling me that it is "inaccessable". Fstab entry for the partition (which is ext3 and the 2nd partition found on the 2nd hard drive):

/dev/hdd2 /mnt/storage ext3 noauto,uid=1000,gid=1000,auto,rw,nouser 0 0

Anyone know what acess is being denied to me?

I also have a FAT32 partition on the 1st hard drive, second partition. I am being denied write access to it while in my linux boot. It's Fstab entry is as follows:

/dev/hdc3 /win32 vfat defaults,uid=0,gid=0,auto,rw,nouser 0 0

I can read from it easily, I simply am not allowed to write to it.

---

### Post by amohanty on 2005-11-29
> noauto,uid=1000,gid=1000,auto,rw,nouser

This means that it is not to be automatically mounted and is only available to user with user id 1000 and group id 1000 and thats it not user mountable. Its most probably you. TO check:

cat /etc/passwd | grep 1000

Was the fstab hand-edited?

I would suggest replacing that line with the following:
/dev/hdd2 /mnt/storage ext3 auto,rw,user 0 0

some basic fstab help:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

HTH
AM

---

### Post by aysiu on 2005-11-29
```
sudo umount /win32
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

Change this line ```
/dev/hdc3 /win32 vfat defaults,uid=0,gid=0,auto,rw,nouser 0 0
``` to be this line instead ```
/dev/hdc3 /win32 vfat umask=000 0 0
``` Save ```
sudo mount -a
```

---

### Post by Dillius on 2005-11-29
Attempted the above change, I still do not have write permissions

---

### Post by amohanty on 2005-11-29
Both of them failed?
can you post the output of :
mount

AM

---

### Post by aysiu on 2005-11-29
[QUOTE=Dillius]Attempted the above change, I still do not have write permissions[/QUOTE] Try rebooting, then.

---

