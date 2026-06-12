---
title: "[SOLVED] Grub Error 17 Problems"
date: 2008-12-18
forum: General Help
---

### Post by celtic426 on 2008-12-18
I've looked for help for error 17 and there's tons of it but my situation is a little more unique.  

Right now I'm kinda triple booting Crunchbang linux, Linux Mint, and Windows XP.  I was in XP today fine, rebooted into Crunchbang, and now I can't get to XP anymore.

But the thing is, I don't have an option in my grub to boot into XP, I have an option directed to my linux mint grub menu that I click on, which then gives me another list with XP in it.  This is what my grub menu looks like now:

```
title		Crunchbang Linux
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eae454d3-e85d-4b9b-9280-f8fa9e19b3d0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Crunch - recovery mode
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eae454d3-e85d-4b9b-9280-f8fa9e19b3d0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Crunch - memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Linux Mint Grub Menu
configfile (hd0,7)/boot/grub/menu.lst
```

Clicking on the last option, Linux Mint Grub Menu, will bring up my old grub menu I used when I had linux mint, and from there I can choose to boot into xp.  But now I'm getting error 17 right after I click the Linux Mint Grub Menu option.  I didn't do anything to my knowledge to change any settings of the drive or anything else.

This is the output of fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01450145

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5554    44612473+   7  HPFS/NTFS
/dev/sda2            5555       30401   199583527+   f  W95 Ext'd (LBA)
/dev/sda5            5555       11931    51223221   83  Linux
/dev/sda6           11932       19498    60781896   83  Linux
/dev/sda7           19499       30122    85337248+  83  Linux
/dev/sda8           30123       30401     2241036   82  Linux swap / Solaris
tim@crunch:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075736     473676    1602060          0      16652     259576
-/+ buffers/cache:     197448    1878288
Swap:      2241028          0    2241028

```

Does anyone have any ideas on this?  Thanks.

---

### Post by caljohnsmith on 2008-12-18
If you Mint entry in Grub uses (hd0,7), that would sda8, which is your swap partition. Do you know which partition is Mint? If Mint is on say sda7 then that's (hd0,6) to Grub, because Grub's numbering begins at 0 and not 1. How about changing the (hd0,7) to whichever is your Mint partition and see if that works.

---

### Post by celtic426 on 2008-12-19
I just added this to my grub file and it worked:

title Windows XP
rootnoverify (hd0,0)
chainloader +1

---

