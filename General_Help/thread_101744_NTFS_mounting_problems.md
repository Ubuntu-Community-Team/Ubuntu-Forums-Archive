---
title: "NTFS mounting problems"
date: 2005-12-10
forum: General Help
---

### Post by typhoontycoon on 2005-12-10
Currently I have Ubuntu 5.10 installed on my first drive and my old windows 2000 installation on my second drive.  However I'm running into problems when trying to mount an NTFS partition even as read only.

The following is the resultant output from the "sudo fdisk -l" command...

-----
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30024   241167748+  83  Linux
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276       11721    83907495    f  W95 Ext'd (LBA)
/dev/sda3   *       11722       14593    23069340    c  W95 FAT32 (LBA)
/dev/sda5            1276        2550    10241406    7  HPFS/NTFS
/dev/sda6            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda7            5101        8924    30716248+   c  W95 FAT32 (LBA)
/dev/sda8            8925        8937      104391    b  W95 FAT32
/dev/sda9            8938       10849    15358108+  83  Linux
/dev/sda10          10850       11595     5992213+  82  Linux swap / Solaris
/dev/sda11          11596       11721     1012063+  82  Linux swap / Solaris
-----

When I try to mount /dev/sda5 under a newly created directory "/media/win/" I get the following...

xxxxx@xxxxxxxx:/media$ sudo mount /dev/sda5 /media/win/ -t ntfs -o nls=utf8.umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Does any one know what I've done wrong here?  I seem to be able to mount Fat32 partitions Okay but can't mount NTFS ones.

Thanks for any pointers.

---

### Post by adie273 on 2005-12-19
I'm relatively new to Ubuntu so i'm no real help to be honest, but I mounted an NTFS drive on my Ubuntu and did it by adding to 'fstab' instead so it would mount automatically.

Have you tried simplying it a bit more, I mean, you mention you did..

sudo mount /dev/sda5 /media/win/ -t ntfs -o nls=utf8.umask=0222

Where as I just did something like.. (In fstab)

/dev/sda5	/mnt/Data	ntfs	ro,uid=1000		0	0

Doubt it will help any sorry, but I find if you start with basic commands just to get something working, you can build on from there.

Good Luck Anyhow

---

### Post by aysiu on 2005-12-19
See the fourth link of my sig.

---

