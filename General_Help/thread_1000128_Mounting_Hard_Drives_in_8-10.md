---
title: "Mounting Hard Drives in 8-10"
date: 2008-12-02
forum: General Help
---

### Post by Sabar on 2008-12-02
I have been running a duel boot system with XP and 7-10 untill today. I have finally updated to the latest Ubuntu 8-10.

Under 7-10 both of my hard drives were mounted on my desktop, and also listed under places.

With my new install of 8-10 neither one of my two drives are mounted on my desktop. But my XP Partition on one drive is listed and the complete other drive is also listed under places.


How ever If I right click on the drive and click on mount it comes up with an error and asking for my password. is this normal? I dont know how I should proceed if this is a precaution  new to 8-10 or if I did something wrong on the installation.

Any Help would be appreciated
Sabar

---

### Post by vitaraq1962 on 2008-12-02
It asks for your password as you are mounting the drive. If you enter your password you can also tick the box to remember the action so next time you should not have to enter it. 

Gaz :guitar:

---

### Post by Sabar on 2008-12-02
That's what I was kinda figuring.  I just get very nervous when things don't look like I think they should.

Thank you very much for helping me out

Sabar

---

### Post by Sabar on 2008-12-03
Well I thought I had everything figured out, And then I rebooted the computer.

On Start up my hard drives are no longer mounted on the desktop, so that means Amarok and I am going to assume some other programs can not read them.

This is easily remedied by just going to Places and Clicking on the drives that are listed there. Unfortunately this means that Amarok has to research the folders in order to get my music collection.

Is there some way around this?  Some way to keep the Drives mounted on the Desktop even after a start-up?

Thanks for any help that you all can give.

---

### Post by taurus on 2008-12-03
Have you considered adding an entry in /etc/fstab to mount that harddrive/partition upon boot.  Then, you don't have to click it to mount it since it would be mounted automatically each time you boot.  Post the outputs of these commands if that is what you want to do, adding an entry in /etc/fstab.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Sabar on 2008-12-03
sudo fdisk -l

> Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeedbeedb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19925    78124095    5  Extended
/dev/sda5           10200       10442     1951866   82  Linux swap / Solaris
/dev/sda6           10443       19925    76172166   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d8d3d8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   7  HPFS/NTFS



sudo blkid


> /dev/sda1: UUID="D25076015075ED1B" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="677bfbb7-5301-4fc0-9680-e355d4aab3eb" 
/dev/sda6: UUID="76c83423-bdfc-446a-8d24-77782c734e0d" TYPE="ext3" 
/dev/sdb1: UUID="92FCF0BFFCF09EA3" TYPE="ntfs" 


cat /etc/fstab

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=76c83423-bdfc-446a-8d24-77782c734e0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=677bfbb7-5301-4fc0-9680-e355d4aab3eb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



df -h


> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              72G  4.3G   64G   7% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  100K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  502M   1% /dev
tmpfs                 504M  116K  504M   1% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             233G   55G  178G  24% /media/disk
/dev/sda1              79G   14G   65G  18% /media/disk-1

---

