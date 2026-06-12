---
title: "[SOLVED] I think I messed up my fstab...."
date: 2008-12-03
forum: General Help
---

### Post by Gonz_91 on 2008-12-03
So, here I am, trying this program, called pySDM.
Somehow, I changed something, and now I can't mount my external hard drive.


```
cat /etc/fstab
```
This is how my fstab looks like:

```
proc                                       /proc          proc         defaults                    0  0  
UUID=59c89f04-b31e-45f2-ae4c-196564725e26  /              ext3         relatime,errors=remount-ro  0  1  
UUID=2b3beab0-1066-4dd5-8c9d-3b3d8a3d736c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    vfat         user                        0  0  
```

---

### Post by taurus on 2008-12-03
Edit /etc/fstab and change the **user** for /dev/sdb1 to **defaults** and see if that works.

---

### Post by Gonz_91 on 2008-12-03
Thank you for your reply!
Ok, I changed it, now, when I plug the drive to my usb port, it says I'm not privileged enough to mount the drive.

I tried 
```
sudo mount /dev/sdb1
``` 

And got this:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Maybe the defaults are wrong?

---

### Post by taurus on 2008-12-03
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Gonz_91 on 2008-12-03
fdisk -l gives the following output:

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc98bb51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23568   189309928+  83  Linux
/dev/sda2           23569       24321     6048472+   5  Extended
/dev/sda5           23569       24321     6048441   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xedb62862

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       64601   488383528+   7  HPFS/NTFS


---

### Post by taurus on 2008-12-03
Your /dev/sdb1 is ntfs, not fat32/vfat.

> 
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 64601 488383528+ 7 HPFS/NTFS 


Therefore, you need to edit /etc/fstab and delete the line for /dev/sdb1.  Then, install ntfs-config use it to configure your external drive then.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by iponeverything on 2008-12-03
also do this to make sure the file ends with a newline:

```
sudo echo >> /etc/fstab
```

---

### Post by Gonz_91 on 2008-12-03
Thank you all very much, I can now mount and u(n)mount it at my heart's desire.

But, if I plug in another USB drive, when this one is not plugged in, will it mount?

---

### Post by Gonz_91 on 2008-12-03
> **Gonz_91 said:**
> 
But, if I plug in another USB drive, when this one is not plugged in, will it mount?

Forget this. I tried, and it worked. Thank you very much for your help!

:D

---

