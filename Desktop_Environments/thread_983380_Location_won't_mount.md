---
title: "Location won't mount???????"
date: 2008-11-15
forum: Desktop Environments
---

### Post by fluhartz on 2008-11-15
Hello All,

 I am having a small issue when trying to open my Windows OS folder in Linux.  When I double click on it I get this error.. 

Unable to mount location.
Internal Error: No mount object for mounted volume.

It's not a huge deal because when the error comes up.. I just click ok and double click the folder again and all is fine. Like I said it's not a huge deal just a couple extra click, but can anyone explain why this is happening... and maybe how to fix it.....

I have added a screenshot... 
Any help would be appreciated......


Also... It worked fine until I upgraded to 8.10

Thanks
Flu

---

### Post by aamit_wraj on 2008-12-23
I am too getting irritated by this Bug.Though Ive reported it to launchpad.net,Im yet to see any patches or fix.I witnessed this almost on every computer I used,but I wonder why there aren't much hues and cries over it.Here is the real detail:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/256749]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/256749")

---

### Post by taurus on 2008-12-23
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by aamit_wraj on 2009-01-08
**Here is what I got while punching in those commands:**


amit@amit:~$ sudo fdisk -l
[sudo] password for amit: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d0df245

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         892     7164958+   7  HPFS/NTFS
/dev/sda2             893       19457   149123362+   f  W95 Ext'd (LBA)
/dev/sda5             893        2549    13309821    7  HPFS/NTFS
/dev/sda6            2550       13385    87038976    7  HPFS/NTFS
/dev/sda7           13386       14660    10241406    7  HPFS/NTFS
/dev/sda8           14661       15935    10241406    7  HPFS/NTFS
/dev/sda9           16573       17847    10241406    7  HPFS/NTFS
/dev/sda10          17848       18739     7164958+   7  HPFS/NTFS
/dev/sda11          15936       16572     5116671   83  Linux
/dev/sda12          18740       19457     5767303+  83  Linux

Partition table entries are not in disk order
amit@amit:~$ sudo blkid
/dev/sda1: UUID="085C9FD95C9FBFBC" LABEL="Jukebox 2" TYPE="ntfs" 
/dev/sda5: UUID="9CBA76E2BA76B7FA" LABEL="Vista" TYPE="ntfs" 
/dev/sda6: UUID="F0E26DD5E26DA098" LABEL="Jukebox" TYPE="ntfs" 
/dev/sda7: UUID="8458D20A58D1FB3E" LABEL="Program Files" TYPE="ntfs" 
/dev/sda8: UUID="2E74FC5174FC1D71" LABEL="Workstation" TYPE="ntfs" 
/dev/sda9: UUID="9E5CB7195CB6EAE3" LABEL="Digital Library" TYPE="ntfs" 
/dev/sda10: UUID="9630D38230D3682F" LABEL="Dumps" TYPE="ntfs" 
/dev/sda11: UUID="b831204f-0779-4b29-908c-034033055ba4" TYPE="ext3" 
/dev/sda12: UUID="2c3f8d0b-92f5-4f94-93d4-6fcb396757d9" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 
amit@amit:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=b831204f-0779-4b29-908c-034033055ba4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda12
UUID=2c3f8d0b-92f5-4f94-93d4-6fcb396757d9 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
amit@amit:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda11            4.9G  2.2G  2.4G  48% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  200K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.9M  498M   1% /dev
tmpfs                 501M  144K  500M   1% /dev/shm
/dev/sda12            5.5G  2.8G  2.4G  54% /home


**Partition table entries are not in disk order**(while executing sudo fdisk -l)...Is it the culprit here???

---

