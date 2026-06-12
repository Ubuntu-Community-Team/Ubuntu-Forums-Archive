---
title: "Can't boot XP on SCSI disk after dist-upgrade of Ubuntu6.06"
date: 2006-08-29
forum: Desktop Environments
---

### Post by AlanQ on 2006-08-29
Been trying to fix this for about six hours.
It's now 2:30AM. Very tired. Please excuse poor description, etc...

Used to be able to boot XP from grub.
Now all I get is 'Error 13: invalid or unsupported executable format'

Have done 'apt-get upgrade' and 'apt-get dist-upgrade' on U6.06
since I last booted XP.

At end of 'apt-get dist-upgrade' it did do something with grub:
```
...
Setting up linux-image-2.6.15-26-386 (2.6.15-26.46) ...
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
...
```

I have three disks:
PATA  /dev/hda  and  /dev/hdc
SCSI  /dev/sda

Ubuntu is on /dev/hda1
WinXP is on /dev/sda1

device.map:
(hd0)   /dev/hda
(hd1)   /dev/hdc
(hd2)   /dev/sda

XP part of menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

I've since changed XP part of menu.lst to:
```
title           Microsoft Windows XP Professional
root            (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
makeactive
chainloader     +1
```

Same result.

When I choose XP option in grub I get:
Error 13: invalid or unsupported executable format.

Any help much appreciated.
Thank you
Al

---

