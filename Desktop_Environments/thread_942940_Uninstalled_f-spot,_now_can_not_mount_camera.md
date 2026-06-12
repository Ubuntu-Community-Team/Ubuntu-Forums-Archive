---
title: "Uninstalled f-spot, now can not mount camera"
date: 2008-10-09
forum: Desktop Environments
---

### Post by Leav on 2008-10-09
Ok.

so this all started with the f-spot-import program which insisted on loading photos from my camera instead of letting me browse the folder myself.

I couldn't find a way around it so I tried uninstalling it.

I have also disabled the importing of photos in the:
System > Preferences > Removable Devices and Media

and now in nautilus'
Edit > Preferences > Media > Photos
it says:
"no application found"
where as before it has nautilus alongside f-spot.

here is my dmesg, after I plugged in and disconnected the camera 3 times:
```

[14484.875861] usb 2-2: new full speed USB device using uhci_hcd and address 17
[14485.069129] usb 2-2: configuration #1 chosen from 1 choice

```

here is lsusb:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 017: ID 040a:059e Kodak Co. 
Bus 002 Device 003: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

so it is clearly there, connected, but fdisk -l shows:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62ef6b93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4982    19535040   83  Linux
/dev/sda3            4983        5955     7815622+  82  Linux swap / Solaris
/dev/sda4            5956       19457   108454815    b  W95 FAT32

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47bd620d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

```

which are the two harddrives I have and their partitions.
no mention of the camera.

How can I browse my camera?
Please help!
:)
-Leav

p.s.
it's a Kodak EasyShare Z650, and I have been reading a bit on how kodak doesn't like to play ball and support the "mass storage device" standard. could this be the problem?

---

### Post by Leav on 2008-10-10
err... is it ok to bump?

---

### Post by timcredible on 2008-10-10
you could use digikam, it's a 1,000 times better than f-spot

---

### Post by TenPlus1 on 2008-10-10
I pretty much removed f-spot and went back to gthumb, adding the line "gnome-volume-manager-gthumb" under Removable Drives and Media, Digital Camera Tab so that gthumb handles cameras from then on...

---

### Post by HeWhoE on 2008-11-03
I don't want to use f-spot either!  I'd like to mount the flash card to a mount point where I can read the contents of the card from the terminal or from nautilus.

---

