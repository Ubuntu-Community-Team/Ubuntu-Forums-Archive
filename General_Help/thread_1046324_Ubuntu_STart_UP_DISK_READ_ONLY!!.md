---
title: "Ubuntu STart UP DISK READ ONLY!!"
date: 2009-01-21
forum: General Help
---

### Post by smartygoldenfish on 2009-01-21
hello.
i wanted to make a usb startup disk for my (x)ubuntu. 
So i fired up my Ubuntu 8.10 CD and clicked on Make USB Startup disk option. It made it successfully.
However, the usb fails to boot. It just Shows a smilie when i try to boot from it. I cant boot it! I tried it 2-3 times moe, but same result.
So i installed UNetBootIn in windows and installed Xubuntu in it.

The computer now boots perfectly from it, with one problem.
The USB drive from which it booted is marked as cdrom.
[i mean in file manager, its shown in Left Panel as CD].
Its perhaps mounted by /cdrom. And is READ ONLY. Even with root access, i am unable to even make a new folder in it.
Also it USB behaves as a Live CD, it does not save any settings.
[even though i click on "save session"].
What i thought of was, mounting USB again,
also this is what i did:
[i have 160 GB Vista and Ubuntu 8.10 dual boot
the USB drive is 4 GB]
```

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        6088    28418953+   7  HPFS/NTFS
/dev/sda6   *        6089        7499    11333826   83  Linux
/dev/sda7            7500        7650     1212876   82  Linux swap
/dev/sda8            7651       12749    40957686    7  HPFS/NTFS
/dev/sda9           12750       19457    53881978+   7  HPFS/NTFS

Disk /dev/sdf: 4089 MB, 4089446400 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         497     3992121    b  W95 FAT32
root@ubuntu:/home/ubuntu# umount /dev/sdf1
umount: /dev/sdf1: not mounted
root@ubuntu:/home/ubuntu# mount /dev/sdf1 /media/ABC
mount: /dev/sdf1 already mounted or /media/ABC busy


```



So now i am in a soup. The whole purpose of making a usb drive bootable is defeated, ie was to copy files from any computer to my pen drive and roam around!
Plz Help.

---

### Post by sedawk on 2009-01-21
Boot Ubuntu from your harddisk and when the Desktop is ready insert
the stick. It should be mounted automatically somewhere at /media/....
Let's assume it is at /media/disk
Check the file /media/disk/etc/fstab and compare the entry
for the root filesystem "/" with the one of your harddisk /etc/fstab.
Most likely there is an option set that forces "/" to be mounted
readonly. Remove that option from /media/disk/etc/fstab, save the file
and reboot from the USB stick.

BTW: mounting a USB stick read only is a good idea in the long run - 
or at least disable the use of access time field for files (also
configured in fstab). Otherwise the USB stick might wear off earlier
(at least in theory).

---

### Post by mixmaster on 2009-01-21
I've not used UNetBootIn but from the documentation I don't think it is designed to create persistent live USB installations.  

The menu option to make a bootable persistent USB does work, at least for me, so I would go back and try that again.  Failing that, there are instructions around for building persistent USB sticks by hand.

---

### Post by Yoodle on 2009-01-23
> **smartygoldenfish said:**
> 
Also it USB behaves as a Live CD, it does not save any settings.
[even though i click on "save session"].

Where is there an option to "Save Session"?  I'm having the same problem.  I created the boot USB and I'm able to boot from it, but it is not saving my session, so it's not different than booting from a Live CD.

---

