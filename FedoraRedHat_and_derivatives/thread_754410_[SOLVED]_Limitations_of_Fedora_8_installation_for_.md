---
title: "[SOLVED] Limitations of Fedora 8 installation for a dual-boot PC"
date: 2008-04-13
forum: Fedora/RedHat and derivatives
---

### Post by &amp;wP*!) on 2008-04-13
The intention why I open this thread is that an Ubuntu user shares his experiences with Fedora 8 to configure his dual boot system for multi boot with more operating systems.

For a machine of MSI-6590 mainboard, AMD Athlon XP 2800+, 1 GB RAM, I have only one 80 GB IDE harddisk which has following partitions (hda=harddisk is a primary IDE master):
```
hda1     40 GB      Windows XP,     NTFS, bootable
hda2         -      (extended partition of the following)
hda5      5 GB      data exchange   FAT32
hda6      2 GB      swap
hda7    256 MB      /boot           ext3
spare   768 MB      spare free unallocated area
hda8      5 GB      /home           ext3
hda9      2 GB      /tmp            ext3
hda10    10 GB      /               ext3
spare    10 GB      spare free unallocated area
```
I thought the scheme above is not optimal (swap 2x RAM, /home too small, no need to separate /tmp etc), therefore I bought another 80 GB IDE harddisk, for which I did following partitions using **fdisk** (hdd=harddisk is a IDE secondary slave):
```
hda1      1 GB      Grub            FAT32, bootable
hdd2     10 GB      data exchange   FAT32
hdd3      1 GB      swap
hdd4                (extended partition of the following)
hdd5     20 GB      /home           ext3
```
The reason why I have the scheme above, is:[LIST=1]
[*]First partition of GRUB boot loader to support several operating system boot files
[*]A FAT32 data exchange with more disk capacity because I can use it for Windows
[*]A swap common for all operating systems
[*]A home partition common for all operating systems
[/LIST]
Here are my observations for this:
[LIST=1]
[*]Linux utility /sbin/mkdosfs cannot make first partition bootable if this is a FAT16/FAT32 partition (see its man page). Man page seems to be outdated (1995's) but Windows XP sees this partition as an active partition (the word **active** is *bootable* partition in Microsoft terminology). Quite confusing!
[*]DVD ISO image Fedora 8 downloaded. Since I don't have a DVD writer, I created a mount to this ISO image; copied vmlinuz and initrd.img files from the ISO and copied them to /boot partition above, into the 1st harddisk. I have manually edited /boot/grub/menu.lst so that GRUB can boostrap Fedora 8 these install files. The complete ISO image has been extracted into /dev/hdd2, so that Fedora 8 install can look for a distro directory.
[*]Fedora 8 renamed all IDE harddisks with /dev/sda,sdb; because Linux kernels starting 2.6.20 do not support naming schemes for IDE harddisks any more. It took me half an hour to get this.
[*]Fedora 8 installation succeeds and installation is able to read all necessary files from /dev/hdd2.
[*]Fedora 8 asks me what to do for partitioning. It sets all the harddisks and partitions in this harddisks for formatting to install Fedora on a fresh system. If I had not paid attention to this, Fedora install could have deleted my complete data.
[*]I have therefore selected Custom Layout option for the partitioning I want.
[*]When I reconfigure hdd5 for /home and add / partition with /dev/hdd6, Custom Layout option aborts and Fedora does not continue with installation, because Fedora wants to have a primary partition on hdd. But I had created all the primary partitions on the harddisk where I wanted to install. Ubuntu never does this and gives the user complete freedom to use any partition it wants.
[*]I deleted then hdd5 (extended partition) and I created hdd5 in Fedora Custom Layout option. In this case, when I try to create / in hdd6, Fedora moves / partition in front /home partition!!
[/LIST]

I did not like Fedora in this aspect. Installation of a Linux distro shall not force user to install itself on a primary partition. It just does not support the flexibility Ubuntu supports. If Fedora is like this, I think Ubuntu is far best Linux distro in terms of installation flexibility.

Please correct me if I am wrong above.

---

### Post by &amp;wP*!) on 2008-04-16
Hey  community,

I correct myself. It is a shame now for me to have this thread. I looked for a button to delete this thread but there is not. Anyway, I correct my mistakes below.

> Linux utility /sbin/mkdosfs cannot make first partition bootable if this is a FAT16/FAT32 partition (see its man page). Man page seems to be outdated (1995's) but Windows XP sees this partition as an active partition (the word **active** is *bootable* partition in Microsoft terminology). Quite confusing!No need to use mkdosfs. Do that partition and leave the formatting to the OS installer.
> DVD ISO image Fedora 8 downloaded. Since I don't have a DVD writer, I created a mount to this ISO image; copied vmlinuz and initrd.img files from the ISO and copied them to /boot partition above, into the 1st harddisk. I have manually edited /boot/grub/menu.lst so that GRUB can boostrap Fedora 8 these install files. The complete ISO image has been extracted into /dev/hdd2, so that Fedora 8 install can look for a distro directory.Complete ISO image does not need to be extracted. Fedora is able to read ISO images installed on harddisks and perform installation by reading the ISO image from there.
> Fedora 8 renamed all IDE harddisks with /dev/sda,sdb; because Linux kernels starting 2.6.20 do not support naming schemes for IDE harddisks any more. It took me half an hour to get this.A lot announcements exist on internet. Shame on me.
> Fedora 8 asks me what to do for partitioning. It sets all the harddisks and partitions in this harddisks for formatting to install Fedora on a fresh system. If I had not paid attention to this, Fedora install could have deleted my complete data.This is quite normal for an installer...
> I have therefore selected Custom Layout option for the partitioning I want.Wow, great on me!
> When I reconfigure hdd5 for /home and add / partition with /dev/hdd6, Custom Layout option aborts and Fedora does not continue with installation, because Fedora wants to have a primary partition on hdd. But I had created all the primary partitions on the harddisk where I wanted to install. Ubuntu never does this and gives the user complete freedom to use any partition it wants.This is the mistake of me. When a extended partition has to be created, it has to allocate the complete rest of the harddisk. I did not do it. Therefore Fedora could not partition unallocated harddisk area which does not belong to extended partition.
> I deleted then hdd5 (extended partition) and I created hdd5 in Fedora Custom Layout option. In this case, when I try to create / in hdd6, Fedora moves / partition in front /home partition!!
Because of the reason above.
> I did not like Fedora in this aspect. Installation of a Linux distro shall not force user to install itself on a primary partition. It just does not support the flexibility Ubuntu supports. If Fedora is like this, I think Ubuntu is far best Linux distro in terms of installation flexibility.

Please correct me if I am wrong above.Yes I am wrong, and I correct myself.

Now I have 3 operating systems on 2 harddisks. There is still room about 5 more operating systems to go...

---

