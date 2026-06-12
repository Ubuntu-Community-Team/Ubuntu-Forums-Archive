---
title: "every drive shows as removable"
date: 2009-04-14
forum: General Help
---

### Post by strider22 on 2009-04-14
All my drives show as removable. There are 4 partitions on this laptop drive and now they all show as removable.

My usb drive shows up 3 times. I can't unmount it. I have restarted. I unplugged the usb during the bios prompt. Then after letting the desktop come up and all regular disk activity stopped I plugged the usb back in and now I have 3 usb icons for 1 drive.

Ah, I remember adding a swap file so here is my fstab.

fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ad2076e1-8d0e-45bb-b821-e16fe9846036 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/swap_file       none            swap    sw              0       0

```

fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x970575bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13083   103550976    7  HPFS/NTFS
/dev/sda3           18591       19458     6962176   17  Hidden HPFS/NTFS
/dev/sda4           13084       18590    44234977+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    c  W95 FAT32 (LBA)

```

system monitor file systems;
```

/dev/sb4  {shows the fixed disk}
gvfs-fuse-daemon  {redefines sb4}
/dev/sdb1  {usb 1}
/dev/sdc1  {2 -same as b1}
/dev/sdd1  {3 -same as b1,c1}  

```

places shows file system and then the other 3 partitions and the 3 usb are all in removable.

---

### Post by mb_webguy on 2009-04-15
Any internal partitions not mounted at startup (by having an fstab entry) will show up in the Nautilus Places menu.  They're not really removable drives, but they can be mounted and unmounted by clicking on them.  So yeah, they're basically treated like removable drives, except they don't go away when you unmount them.

Since you're not mounting them in fstab, I assume that you don't want to mount them at all.  If this is the case, then you need to hide them from Nautilus.  Unfortunately, there's no quick and easy way of doing this -- unless you're comfortable with editing text files.

Anyway, here's how you [hide unmounted internal partitions]("http://ubuntuforums.org/showpost.php?p=6677262&postcount=2") from the Nautilus Places menu.

---

### Post by strider22 on 2009-04-16
Although the prior two reboots left things the same as described the latest reboot has corrected the problem??? I am back to showing drives in the places drop down and there is now no removable entry.

You noticed the missing fstab entries. Should I put them in or let the automagically method continue to do its stuff? Ah, I may as well just add them as I can't see any advantage to leaving them out. (of course I won't put the usb entry in.)

Thanks, Strider22

---

