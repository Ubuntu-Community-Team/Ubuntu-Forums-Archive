---
title: "Formatting my floppy disk in ubuntu"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Mikeee on 2006-08-23
Hi all,

Sorry for the newbie question. How can i format my usb floppy disk located at /dev/sdb and /media/floppy with the ext2 filesystem?

Thanks

---

### Post by fakie_flip on 2006-08-23
What is the output of this while your usb disk is plugged into the computer?
```
sudo fdisk -l
```

---

### Post by peabody on 2006-08-23
There is a floppy formatter program which is hidden under a system tools menu.  You can enable it using the Alacarte menu editor.  Not sure if it works with USB floppy drives though.  Let me know, I'd be interested.

---

### Post by Mikeee on 2006-08-23
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5903    47415816    7  HPFS/NTFS
/dev/hda2            7179        9621    19623397+  83  Linux
/dev/hda3            9622        9729      867510    f  W95 Ext'd (LBA)
/dev/hda4            5904        7178    10241437+   c  W95 FAT32 (LBA)
/dev/hda5            9622        9729      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   567332875  1110505095   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(567332874, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(1110505094, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   443394731   623053494   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(443394730, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(623053493, 0, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   179663131   645784101   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(179663130, 0, 2)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(645784100, 0, 3)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  1303039523  1303061302       32669+  bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1303039522, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(96, 0, 7) logical=(1303061301, 0, 2)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



```

It doesnt seem to like my floppy drive. Thanks for your help :)

---

### Post by fakie_flip on 2006-08-23
Use the following commands. Warning: this will delete all of your files from the usb disk. Backup the files to your hard drive from the usb disk.

```
sudo fdisk /dev/sdb
```

Next push d for delete, then 1 for partition number one, then n for new partition, p for primary partition, 1 for partition number, then w to write changes to usb disk, and last, q for quit.

Next give this command.

```
sudo mke2fs /dev/sdb1
```

All done :biggrin:

---

### Post by fakie_flip on 2006-08-23
Are you doing it now?

---

### Post by fakie_flip on 2006-08-23
I guess you like easy GUI programs like most windows users.

---

### Post by Mikeee on 2006-08-23
Not true. Your way worked perfectly and the GUI way didnt.

PeaBody: The floppyformatter didnt work, it complained about not being able to find the geometry

However Im still having problems with the floppy drive which is what ive been trying to fix for the past hour. Basically I tried to install grub to my USB floppy and nothing works. Im about to reinstall windows knowing its going to overwrite my MBR. So i need  a boot disk to get back into ubuntu to reinstall grub.

Is there away that I can use loadlin to boot back into my ubuntu? Thanks all for your help

---

### Post by Roger Mudd on 2006-08-23
> **Mikeee said:**
> Hi all,

Sorry for the newbie question. How can i format my usb floppy disk located at /dev/sdb and /media/floppy with the ext2 filesystem?

Thanks

Is there any benefit to doing this rather than simply formating fat32? It would seem to me that formatting ext2 would render the thumb drive inoperable for use with Windows machines. I know there is a general dislike/distrust of Microsoft -- but that doesn't change the fact that the vast majority of machines out there have some form of Windows OS installed. Just curious...

---

### Post by Mikeee on 2006-08-23
Yeah there is a reason as im not anti Microsoft. Basically i was following a tutorial on how to install grub on the floppy and it said to format it in ext2. Thats all :-)

---

### Post by peabody on 2006-08-23
couldn't you use the live cd?

---

### Post by fakie_flip on 2006-08-23
I'm not sure why your computer is not booting from the floppy or usb disk because you have not gave enough information, but my guess is that it is a bios problem. You must have your bios settings configured to try to boot from the floppy drive or usb before trying to boot the hard drive. If your bios is like most of the ones I've used, then hit f2 or delete when your computer first powers on to enter the bios settings when booting your computer, make the changes, save them, and reboot.

---

