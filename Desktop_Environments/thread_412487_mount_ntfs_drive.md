---
title: "mount ntfs drive"
date: 2007-04-18
forum: Desktop Environments
---

### Post by isamudysan on 2007-04-18
ok, i'm pretty much now very frustrated and stumped.  i've read all the mounting info on ntfs at this website:  [http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g](http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g).  it's a good one.  i got my external usb hdd mounted, eventhough ubuntu automatically detected and mounted it the instance i turned it on.

my only problem now, seems to be with my internal 160 GB sata drive.  below is the fdisk -l:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7169    57584961   83  Linux
/dev/sda2            7170        7476     2465977+   5  Extended
/dev/sda5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19929   160079661   42  SFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       36483   293041665    f  W95 Ext'd (LBA)
/dev/sdc5               2       36483   293041633+   7  HPFS/NTFS

the /dev/sdb is my d: drive (windows or other drive).  the file system is SFS.  wtf is SFS?  any how,  while i was dabbling with fc6 the last couple of days and nights i got this drive to mount with no problem.  but, with ubuntu i'm having a hard time.  i've already apt-get ntfs-3g already.   need help.  thanx.

---

