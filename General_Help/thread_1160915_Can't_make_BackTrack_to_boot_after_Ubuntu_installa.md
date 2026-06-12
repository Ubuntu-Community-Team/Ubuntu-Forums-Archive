---
title: "Can't make BackTrack to boot after Ubuntu installation"
date: 2009-05-16
forum: General Help
---

### Post by Lockheed on 2009-05-16
After installation of Ubuntu I cannot boot to backtrack anymore.

This is my fdisk printout:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a53d359

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    7  HPFS/NTFS
/dev/sda2            2090       38913   295788780    5  Extended
/dev/sda5            2090       36224   274189356    7  HPFS/NTFS
/dev/sda6           36225       38193    15815961   83  Linux
/dev/sda7           38194       38324     1052226   82  Linux swap / Solaris
/dev/sda8           38325       38337      104391   bb  Boot Wizard hidden   ///BACKTRACK'S BOOT
/dev/sda9           38338       38913     4626688+  bb  Boot Wizard hidden   ///BACKTRACK'S ROOT

```


and menu.lst
```

title		Win7
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


title		U9
uuid		087b9e3b-a65c-4890-9b0e-de019b0fff18
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=087b9e3b-a65c-4890-9b0e-de019b0fff18 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title 		BT4
root (hd0,7)
kernel /boot/vmlinuz ro root=/dev/sda8
boot
```

What am I doing wrong?

---

### Post by Lockheed on 2009-05-17
Come on, guys. I am sure this is a farily easy question.

---

