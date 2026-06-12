---
title: "new hard drive not mounting on boot"
date: 2008-12-11
forum: General Help
---

### Post by kadafi69 on 2008-12-11
I got a new hard drive last week and after faffing about sorting out which file system to use, I settled with XFS. Now that Ive got the drive sorted with all my data on it, its not still not mounting on boot up, I have to manually mount it through terminal or using gparted to mount it to where i want it.

this is the result of fdisk -l (the drive in question is sdb):
> 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c502

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1014 MB, 1014497280 bytes
17 heads, 32 sectors/track, 3642 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Disk identifier: 0xc3072e18

and this is the entry in fstab:
> 
/dev/sdb1 /media/Media ntfs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

for some reason the fstab says the drive is ntfs (which is what the drive used to be on a previous system)

any ideas?

---

### Post by taurus on 2008-12-11
If you want it to mount upon boot, you need to add an entry in /etc/fstab for it.  You need to change the entry in /etc/fstab for /dev/sdb1 since it's not ntfs anymore.  

It should now look something like this.

```

/dev/sdb1 /media/Media  xfs  defaults  0  2

```
Save it.  Then reboot and see if it's mounted to /media/Media now.

```
df -h
```

---

### Post by kadafi69 on 2008-12-11
nope it didnt mount. i got this from df -h
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.2G  390M  8.4G   5% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  300K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.8M 1010M   1% /dev
tmpfs                1013M  244K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-10-generic/volatile
/dev/sda6             137M   29M  101M  23% /boot
/dev/sda7             9.2G  2.1G  6.7G  25% /home
/dev/sda8             1.4G   35M  1.3G   3% /tmp
/dev/sda9             7.4G  2.7G  4.3G  39% /usr
/dev/sda10            3.1G  386M  2.6G  13% /var
/dev/sdc1             966M  1.7M  964M   1% /media/MEMORYSTICK 


EDIT

I made a boob in fstab, sorted it and it mounted fine on reboot. thanks

---

