---
title: "Shdc card: can not remove files"
date: 2009-05-04
forum: General Help
---

### Post by Robbyx on 2009-05-04
I bought an 8GB sdhc card for my satnav. I put some files on to it and now I can not remove them. I didn't format it but just used it out of the box assuming it was formated and it did take the files I copied over to it using the USB port.  I can not now delete the files either under windows via VM box or under ubuntu using a file manager.It reports the files and directories are read only. I can not move files within the sdhc. I have tried reformating the disk to fat32 but the partition manager failed. It was not able to create the partition. 

I have tried to remove the files under su mode of the file manager but it could not remove them. 

I have tried copying a directory but when I try to paste it I am told it is a read only file system.

There is a small slider on the disk, but that is set to unlocked.

I don't know how to resolve this and make the disk writeable. Any suggestions?

---

### Post by pastalavista on 2009-05-04
I just tried to mount an SD card after upgrading to Jaunty a couple of days ago. I hadn't tried it and your post made me wonder. I could see the card in Computer but couldn't mount it. So I opened Synaptic and searched for SD card mount nad installed gnome-mount and pmount.. Still wouldn't mount. I logged out and back in, tried again and it worked! Just for your edification :D

---

### Post by Robbyx on 2009-05-04
I think my card is  mounted because it appears as a separate drive in my file manager. I can also see the contents.  I have both of those programs installed.

 What did you do to mount your sd card  beyond installing those two programs?

How can I check if the drive is mounted?

---

### Post by pastalavista on 2009-05-04
All I did was insert the card in the card reader and it opened in Nautilus. I had previously set gconf-editor to auto-mount removable drives for my USB thumb drives.

Here is a relevant shot of the drive properties. I'm still kinda stupid about the command line but I've got the GUI down pretty well, I think.

If you can open the drive and see the contents, it's mounted. Yours may be a permissions issue. Look in /media. Mine was mounted in /media/disk

---

### Post by Robbyx on 2009-05-05
I am having to face the possibility that Ubuntu has not mounted the card. Gparted says it is not mounted but the following implies that it is being seen. Perhaps that is not the same as being mounted. 

I thought I would try to reformat the disk but gparted is unable to detect the filesystem.

```
rob@rob-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59842124    29921031   83  Linux
/dev/sda2        59842125   122849054    31503465   83  Linux
/dev/sda3       122849055   964815704   420983325    5  Extended
/dev/sda4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sda5       122849118   205358894    41254888+  83  Linux
/dev/sda6       205358958   410412554   102526798+  83  Linux
/dev/sda7       410412618   964815704   277201543+  83  Linux

Disk /dev/sdb: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     4014079     2007024    e  W95 FAT16 (LBA)

Disk /dev/sdd: 0 MB, 49152 bytes
1 heads, 1 sectors/track, 96 cylinders, total 96 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 7944 MB, 7944011776 bytes
255 heads, 63 sectors/track, 965 cylinders, total 15515648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008fa9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63    15502724     7751331    b  W95 FAT32
rob@rob-desktop:~$ 

```

---

### Post by pastalavista on 2009-05-05
Try installing the Storage Device Manager (pysdm) ```
apt-get install pysdm
```
then, while the sd card is inserted, run System > Administration > Storage Device Manager

---

