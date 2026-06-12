---
title: "USB Mounting Problems"
date: 2006-04-13
forum: Desktop Environments
---

### Post by crazycraig16 on 2006-04-13
Can anyone help me, I have an Ipod Shuffle which I use as a storage device for transferring files from windows to linux but when I connect the device it and try to mount it it says: Unable To Mount Volume or something like that

any suggestions?

Thanks

---

### Post by aysiu on 2006-04-13
Plug it in.

Go to KMenu > System > Konsole and type these two commands: ```
sudo fdisk -l
df -h
``` and post the output back here.

---

### Post by crazycraig16 on 2006-04-13
No It doesn't appear to work. 
```

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2339    18787986   83  Linux
/dev/hda2            2340        2432      747022+   5  Extended
/dev/hda5            2340        2432      746991   82  Linux swap / Solaris

Disk /dev/sda: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders
Units = cylinders of 504 * 512 = 258048 bytes

Disk /dev/sda doesn't contain a valid partition table
crazycraig@craigs-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  4.0G   13G  24% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-10-386/volatile

```

All this is WAY beyond me as I am new to linux (got fed up with windows).

---

### Post by aysiu on 2006-04-14
This doesn't look good: ```
Disk /dev/sda doesn't contain a valid partition table
``` Usually for an iPod or USB key, you see something like this: ```
Disk /dev/sde: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         992      499851+   6  FAT16
```

---

