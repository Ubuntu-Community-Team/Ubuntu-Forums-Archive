---
title: "Deleting a Linux Partition from a Multi-Boot System"
date: 2009-06-10
forum: General Help
---

### Post by chessnerd on 2009-06-10
Alright, I currently have a 3 OS boot system set up on a two hard-drive computer with the main OS being Ubuntu on a 40 GB drive and then also Windows 2000 and Xubuntu on a 20 GB. I don't see any reason to have the Xubuntu partition anymore because I can just install XFCE on Ubuntu if I want to go back and I'd like to give Windows 2000 a little more room to breathe. 

So, how do I remove the Xubuntu partition while keeping Grub in tact for the other two?

---

### Post by hal8000 on 2009-06-10
To remove the partition use linux fdisk, cfdisk, gparted etc.

First you need to make sure that Grub is controlled by Ubuntu and not by Xubuntu.
So boot into Ubuntu
sudo apt-get install grub

Setup grub natively and in the mbr of your hard disk

[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

---

### Post by chessnerd on 2009-06-10
Alright, I installed Gparted and it can delete the Xubuntu partition, but how do I then re-allocate that space to the Windows 2000 partition?

---

### Post by bodhi.zazen on 2009-06-10
gparted will do that as well, but the free space must be adjacent to windows XP. You probably need to, in multiple steps, move and resize other partitions.

Screenshot of gparted if you need help.

---

### Post by chessnerd on 2009-06-10
I'm actually running Windows 2000, not XP. I deleted the Xubuntu partition and it is right next to the Windows 2000 one.

Here's what that hard disk looks like now:

---

### Post by merlinus on 2009-06-10
Use gparted to format the unallocated space as ntfs, and then perhaps you can extend the windows one.  You probably will have to first create a partition in that space before formatting.

---

### Post by ibuclaw on 2009-06-10
> **chessnerd said:**
> I'm actually running Windows 2000, not XP. I deleted the Xubuntu partition and it is right next to the Windows 2000 one.

Here's what that hard disk looks like now:

Looks like all you have to do is resize the partition to fit as you please on the hard disk.

Although I do wonder why there is a caution sign by the ntfs filesystem, does gparted give you any reason why that is there?

Regards
Iain

---

### Post by chessnerd on 2009-06-10
It won't let me format anything as NTFS. When I go under features it says it can only detect NTFS partitions. Also, it will only give me the option to delete that partition, I can't resize it. It says that the reason for the caution is that it can't read the file system.

Edit: My bad, I didn't mount the drive so I couldn't read it. Now the caution is gone.

---

### Post by chessnerd on 2009-06-10
Okay, the caution is gone, but now it has two keys next to the partition and I can't do anything to it (even delete it). How do I get permission to modify it?

---

### Post by merlinus on 2009-06-10
If the partition is mounted, then you cannot do anything with it.

Have you tried the live gparted disk?  Or you can boot from the live ubuntu disk and use gparted from there.

---

### Post by chessnerd on 2009-06-10
Alright, I think the problem is that I'm running Gparted 0.3.8, not the latest version. 0.3.8 can't do anything with NTFS. So, I guess I need the latest version of Gparted. 

I went to the website and downloaded a tarball of the latest version but it won't do anything when I try to run it.

How do I install the latest version?

---

### Post by Fatman22 on 2009-06-10
Deleted! Whoops wrong thread.

---

### Post by merlinus on 2009-06-10
Download the disk image.  It is an .iso file, same as ubuntu.  Burn it as a disk image and boot from it.

gparted-live-0.4.5-2.iso

---

### Post by chessnerd on 2009-06-10
Alright, I'm starting up the CD right now. Hope it works.

---

### Post by chessnerd on 2009-06-10
Okay, it seemed to work okay, but it seems to have caused a problem: I can't boot into Windows 2000 anymore...

I'm booting back into Ubuntu (which still works) and I'll try to see what the problem is. I hope I didn't ruin Windows 2000 because the disk has a scratch in it and might not work if I try to reload it.

---

### Post by merlinus on 2009-06-10
Post output of these commands from a terminal in ubuntu:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```This may show what is causing the problem.

---

### Post by chessnerd on 2009-06-10
Sorry it took so long for me to respond, I sat down to have dinner.

Here's what fdisk -l brought back:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4725    37953531   83  Linux
/dev/sda2            4726        4865     1124550    5  Extended
/dev/sda5            4726        4865     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf643f6bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+   7  HPFS/NTFS
```


Here's what cat /boot/grub/menu.lst brought back:

```
default 0
timeout 15

title Ubuntu 8.04.2, kernel 2.6.24-24-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=cea68723-7b08-4e8b-b527-ba158804bc62 ro quiet splash
initrd /boot/initrd.img-2.6.24-24-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=cea68723-7b08-4e8b-b527-ba158804bc62 ro single
initrd /boot/initrd.img-2.6.24-24-generic

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=cea68723-7b08-4e8b-b527-ba158804bc62 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=cea68723-7b08-4e8b-b527-ba158804bc62 ro single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows 2000 Professional
root (hd1,0)
chainloader +1
savedefault
makeactive

```

Does that mean anything?

---

### Post by merlinus on 2009-06-10
Is the hdd with linux set to boot first in bios?

If so, then you will need to add a map statement to menu.lst.

Try changing these lines:

title Microsoft Windows 2000 Professional
root (hd1,0)
chainloader +1
savedefault
makeactive

To:

title Microsoft Windows 2000 Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

Also, post content of /boot/grub/device.map

---

### Post by chessnerd on 2009-06-10
Thank you very much!!! :D

The fix worked and I can now boot into a 20 GB partition of Windows 2000 with all of my data intact!

Thank you everyone who helped me out with this. You've proven yet again that the Ubuntu forums community is one of the best online communities for computer help, Linux or otherwise, anywhere online.

Thanks again.

---

### Post by merlinus on 2009-06-10
Glad you got it working!  Post back if you run into other difficulties.

---

