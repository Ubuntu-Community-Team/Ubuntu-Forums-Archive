---
title: "Ubuntu 12.04 LTS: Grub Menu Missing"
date: 2013-01-17
forum: Desktop Environments
---

### Post by noloader on 2013-01-17
Hi All,

This is a near duplicate of the closed [Grub Menu Missing]("http://ubuntuforums.org/showthread.php?t=1457210"), so I have to spin up a new thread. Unlike the closed thread, I have multiple OSes and the menu is still missing. At boot time, all I get is a purple screen until login.

The installation has both Ubuntu 12.04 and Fedora 17. I have not [yet] added x64 flavors of Ubuntu and Fedora, the Windows OSes (XP, Vista, and 7), nor the BSD OSes (Net and Free).

Ubuntu is managing GRUB from the MBR (installed on /dev/sda). Fedora had its boot loader installed on its partition.

I've re-generated the grub.cfg:

```
$ sudo apt-get clean
$ sudo apt-get autoclean
$ sudo apt-get autoremove
...

$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
```I've also re-installed grub to the MBR:

```
$ sudo grub-install /dev/sda
Installation finished. No error reported.
```In case anyone needs it (the FAT16 partition is for MS gear):

```
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002b33d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048       63487       30720    6  FAT16
/dev/sda2           65534   976771071   488352769    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5           65536    50063359    24998912   83  Linux
/dev/sda6        50065408   100063231    24998912   83  Linux
/dev/sda7       100065280   150063103    24998912   83  Linux
/dev/sda8       150065152   200062975    24998912   83  Linux
/dev/sda9       200065024   250062847    24998912   83  Linux
/dev/sda10      250064896   300062719    24998912   83  Linux
/dev/sda11      968773632   976771071     3998720   82  Linux swap / Solaris
```Any ideas?

---

### Post by mcduck on 2013-01-17
Based on the update-grub output, it's not detecting any other operating systems so that would be why it hasn't set the Grub menu to visible.

You'll probably have to add the entry for your Fedora install manually, and edit the /etc/default/grub file to set the menu to visible.

---

### Post by noloader on 2013-01-17
> **mcduck said:**
> Based on the update-grub output, it's not detecting any other operating systems so that would be why it hasn't set the Grub menu to visible.

You'll probably have to add the entry for your Fedora install manually, and edit the /etc/default/grub file to set the menu to visible.
Forgive my ignorance, but what are these two (duplicate) entries:

```
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
```Is that the same OS? (There's only two on this machine - Ubuntu and Fedora).

Jeff

---

### Post by oldfred on 2013-01-17
Just to see where everything is at post link to BootInfo.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

