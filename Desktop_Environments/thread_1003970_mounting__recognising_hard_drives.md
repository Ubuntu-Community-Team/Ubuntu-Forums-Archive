---
title: "mounting / recognising hard drives"
date: 2008-12-06
forum: Desktop Environments
---

### Post by y2jeff on 2008-12-06
Hi guys, im a total noob and i appreciate all the help i can get.

im running 8.10 and Im having trouble finding my IDE hard drive. I have 1xsata drive with windows on it, as well as a dvd drive and IDE hard drive on the same cable.

Ubuntu can recognise my main sata hard drive with windows on it, but it cant recognise the IDE (with no OS installed), HOWEVER this is the hard drive where ubuntu was installed, and currently running from. this is my sudo fdisk -l output:

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe965e965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef4ed781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       60801   488376000    5  Extended
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS
root@ubuntu:/home/luke#


anyone have any ideas on what i should try?

---

### Post by adaptr on 2008-12-06
It lists two drives, and you say you have one SATA drive; it follows that one of them is the IDE drive.
Since Ubuntu boots from it, it's the first one.

---

### Post by y2jeff on 2008-12-06
> **adaptr said:**
> It lists two drives, and you say you have one SATA drive; it follows that one of them is the IDE drive.
Since Ubuntu boots from it, it's the first one.
yet it doesnt appear in the computer file browser like the other hard drive. how can i mount it?

---

