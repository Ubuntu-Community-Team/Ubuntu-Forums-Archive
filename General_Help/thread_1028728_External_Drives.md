---
title: "External Drives"
date: 2009-01-02
forum: General Help
---

### Post by bolex100 on 2009-01-02
Does anyone know about problems looking at external drives?  I have and Icy Box 351 with a SATA drive inside but Ubuntu just won't look at it.  The thing is, I googled and found almost nothing.  I know it works on a Windoze rig.

---

### Post by albinootje on 2009-01-02
> **bolex100 said:**
> Does anyone know about problems looking at external drives?  I have and Icy Box 351 with a SATA drive inside but Ubuntu just won't look at it.  The thing is, I googled and found almost nothing.  I know it works on a Windoze rig.

Please plug the disk in and post the output of the following :
```

dmesg             (in .txt attachment)
sudo fdisk -l
sudo update-usbids
lsusb

```

---

### Post by bolex100 on 2009-01-03
It said;

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd576484a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   7  HPFS/NTFS

When I plugged it in there was an error message "Cannot mount volume"

---

### Post by albinootje on 2009-01-03
> **bolex100 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   7  HPFS/NTFS

When I plugged it in there was an error message "Cannot mount volume"
Okay, the 160 Gb is your external disk ?
Please try the following :
```

sudo mkdir /media/usb-disk
sudo mount /dev/sdb5 /media/usb-disk -t ntfs-3g -o force,umask=000

```
After that browse with your filemanager into /media/usb-disk
-> Places -> Home -> File System (at the left) -> Media -> usb-disk

---

### Post by bolex100 on 2009-01-04
> Okay, the 160 Gb is your external disk ?No.  Its the 120gb.  Does that change the command?

---

### Post by bolex100 on 2009-01-04
oops!

---

### Post by albinootje on 2009-01-04
> **bolex100 said:**
> No.  Its the 120gb.  Does that change the command?

The disk you want to look at from Ubuntu, is the disk with Windows, isn't it ?
If so, please try the commands mentioned earlier on.

---

### Post by bolex100 on 2009-01-04
dave@takadhall:~$ sudo mkdir /media/usb-disk
mkdir: cannot create directory `/media/usb-disk': File exists
dave@takadhall:~$ sudo mount /dev/sdb5 /media/usb-disk -t ntfs-3g -o force,umask=000
ntfs-3g: Failed to access volume '/dev/sdb5': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
dave@takadhall:~$ sudo mkdir /media/usb-disk
mkdir: cannot create directory `/media/usb-disk': File exists
dave@takadhall:~$

---

### Post by albinootje on 2009-01-04
> **bolex100 said:**
> 
ntfs-3g: Failed to access volume '/dev/sdb5': No such file or directory

Can you do the following :
```

sudo apt-get update
sudo apt-get install testdisk
sudo testdisk /list /dev/sdb5
sudo testdisk /list /dev/sdb1

```
And post the output. Thanks.

---

### Post by bolex100 on 2009-01-04
ok then  Testdisk installed ok
[B]
dave@takadhall:~$  sudo testdisk /list /dev/sdb5[/B]
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sdb5 - 160 GB / 149 GiB - CHS 19455 255 63, sector size=512

Disk /dev/sdb5 - 160 GB / 149 GiB - CHS 19455 255 63
     Partition			Start        End    Size in sectors
   P NTFS                     0   0  1 19455 253 63  312560577 [ICY BOX]
**dave@takadhall:~$  sudo testdisk /list /dev/sdb1**
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sdb1 - 1024 B - CHS 0 255 63, sector size=512

Disk /dev/sdb1 - 1024 B - CHS 0 255 63
     Partition			Start        End    Size in sectors
Invalid NTFS boot
 1 P HPFS - NTFS              0   1  1 19455 254 63  312560577
 1 P HPFS - NTFS              0   1  1 19455 254 63  312560577

Bad relative sector.
No partition is bootable
dave@takadhall:~$

---

### Post by albinootje on 2009-01-04
> **bolex100 said:**
> 
**dave@takadhall:~$ sudo testdisk /list /dev/sdbl**

Please try again, it's sdb1 as in sdb one.
```

sudo testdisk /list /dev/sdb1

```

---

### Post by bolex100 on 2009-01-05
I did type "1" and not "l".

---

