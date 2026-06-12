---
title: "Cannot mount volume. Unable to mount the colume 'Unit A and B'"
date: 2009-04-15
forum: General Help
---

### Post by aiko.uda on 2009-04-15
Hi.

I have an external drive that I used to open with Ubuntu. I saved some documents from a Windows based computer and now cannot open the drive with Ubuntu anymore.

I switched my second laptop from Windows to Ubuntu and I no longer have Windows based computer...

I tried the suggestion below but didn't work. It said it has to be root.
mount -t ntfs-3g /dev/sdb1 /media/Unit A -o force 

There are some results below.

Thanks
__________________________________________________

denis@denis-laptop:~$ sudo mount -a
[sudo] password for denis: 
denis@denis-laptop:~$ sudo mount -a
denis@denis-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c79411c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4982    40017883+   7  HPFS/NTFS
/dev/sdb2            4983        9964    40017915    f  W95 Ext'd (LBA)
/dev/sdb5            4983        9964    40017883+   7  HPFS/NTFS
denis@denis-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  2.8G  136G   3% /
varrun                442M  104K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   60K  442M   1% /dev
devshm                442M   12K  442M   1% /dev/shm
lrm                   442M   39M  403M   9% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      146G  2.8G  136G   3% /home/denis/.gvfs
denis@denis-laptop:~$ sudo mkdir /media/sdal
denis@denis-laptop:~$ sudo mount -t ntfs-3g /dev/sdal /medoa/sdal -o force
ntfs-3g: Failed to access volume '/dev/sdal': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
denis@denis-laptop:~$ df-h
bash: df-h: command not found
denis@denis-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  2.8G  136G   3% /
varrun                442M  104K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   60K  442M   1% /dev
devshm                442M   12K  442M   1% /dev/shm
lrm                   442M   39M  403M   9% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      146G  2.8G  136G   3% /home/denis/.gvfs
denis@denis-laptop:~$

---

### Post by chinmaya_n on 2009-04-15
I too had a similar before......... the command it showed didnt work for me too........ 

It is better to connect the xternal hdd to a windows system and remove it properly....(i mean, safely remove or shutdown the system when the xter. hdd is connected to the system.). 
It will defentelly work.....;)
Let me know did that work when u did it!!

---

### Post by aiko.uda on 2009-04-15
Oh, that means I got to bring this heavy drive to work tomorrow...

Thank you for the advice. Greatly appreciated.

---

