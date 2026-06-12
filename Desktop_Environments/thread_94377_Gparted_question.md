---
title: "Gparted question"
date: 2005-11-23
forum: Desktop Environments
---

### Post by umdzig on 2005-11-23
I want to resize my linux and windows partitions. However, after installing Gparted i noticed that all the partitions have locks on them. So i used ```
sudo umount /dev/hda1 

``` but that didnt work.  It came up saying device is busy. Any ideas?

I also want to make a partition so that i could transfer files between windows and linux, again any ideas?

Thanks for your help in advance.

---

### Post by SilentCacophony on 2005-11-23
I believe that you want to unmount the actual mount point, not the device itself. The 'lazy' option might help as well. Assuming that the mount point is /media/hda1:

sudo umount -l /media/hda1

For example, if I wanted to unmount my hdb1:

```
brian@ubuntu:/usr/share/doc$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              4870284   2092828   2530056  46% /
tmpfs                   225840         0    225840   0% /dev/shm
tmpfs                   225840     12644    213196   6% /lib/modules/2.6.12-9-686/volatile
/dev/hda1              2493208    643072   1850136  26% /media/hda1
/dev/hda2              3241580    934516   2142400  31% /media/hda2
/dev/hda5              4055936   1039012   2810892  27% /media/hda5
/dev/hda6              4055936     65660   3784244   2% /media/hda6
/dev/hdb1             10006696   5085000   4921696  51% /media/hdb1

brian@ubuntu:/usr/share/doc$ sudo umount -l /media/hdb1
```

As for sharing a partition between Windows and Ubuntu, FAT32 is the best filesytem to use there.

---

### Post by art on 2005-11-23
you need to do that from a live CD, when you don't have to mount your HDD. As for sharing between Win and Linux, FAT32 partition will do it.

---

