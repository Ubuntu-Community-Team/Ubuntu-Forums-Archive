---
title: "grub and winxp  help please"
date: 2005-12-12
forum: General Help
---

### Post by Lush on 2005-12-12
Heya. just reinstalled ubuntu onto my recently formatted computer. I also have Win xp installed. When I try to load WinXp Professional i get the following:
[PHP]
Booting 'Microsoft Windows XP'
root (hd1, 0) 
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
[/PHP]
the computer just hangs i can only use ctrl-alt-del to restart. now I read on techforums that i have to add 'boot'  in the menu.lst file for grub  i did that, but the same error happened except that the text 'boot' came after chainloader +1 here is my Windows section of menu.lst
[PHP]
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot
[/PHP]

Thanks a ton!

---

### Post by xequence on 2005-12-12
[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub)

That might work. Not sure though.

---

### Post by Lush on 2005-12-12
sadly this has not worked =( can anyone who uses Xp proffesional show me their grub .lst file?

---

### Post by hoodwink on 2005-12-12
[QUOTE=Lush]Heya. just reinstalled ubuntu onto my recently formatted computer. I also have Win xp installed. When I try to load WinXp Professional i get the following:
[PHP]
Booting 'Microsoft Windows XP'
root (hd1, 0) 
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
[/PHP]
[/QUOTE]
Your grub stanza looks to be correct iffff your WinXP is installed in the first partition of the second harddrive (hd1,0). Most people would have WinXP on the first harddrive (hd0,0). What is your actual disk setup? When booted from Ubuntu, enter 'sudo fdisk -l' and post the results.

---

### Post by mherring on 2005-12-12
You have not said if you installed grub to hd or floppy as part of the install.  I am one of several who have had issues when putting grub on the hd.

Before you see the error message you posted, do you get the grub menu listing windows, Ubuntu, and maybe some variation of Ubuntu?

---

### Post by fannymites on 2005-12-12
Try this - 
```

title Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Apparently, Windows doesn't like to be booted from a second hard drive and this somehow fools it into thinking it's on the first drive.  Or something.  It's the only way I can get it to boot.

---

### Post by Element.Ren on 2005-12-13
This is mine.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Blue"]title           Other operating systems:
root
[/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[COLOR="Blue"]title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
[/COLOR]
```

---

### Post by Ocxic on 2005-12-13
did you have a win xp dual boot befor installing ubuntu? if you did windows xp only install the bootloader to ONE hard disk, the one the first hard disk XP is installed too. if you erase the first xp installation the second one will fail to boot because the boot loader was erased with the first installation of XP

---

### Post by Lush on 2005-12-13
ahh fannymites thanks a ton for that fix ^_^

---

### Post by Lush on 2005-12-13
[PHP]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8134    65336323+   7  HPFS/NTFS
/dev/hda2           12358       14596    17984767+   f  W95 Ext'd (LBA)
/dev/hda3            8135       12357    33921247+  83  Linux
/dev/hda5           12523       14596    16654648+  83  Linux
/dev/hda6           12358       12522     1325299+  82  Linux swap / Solaris[/PHP]

here is the results for the fdisk -l command
before i boot to see if the fix works out fine >_<

---

### Post by Lush on 2005-12-13
yeah sorry for the tripple post but that fix gave me error 21 or 22 something about WIndows not existing on that location

---

### Post by Original Brownster on 2005-12-13
Hi,
Your xp partition is hda1 so thats (hd0,0) in grub

Try:

title           Microsoft Win XP
rootnoverify    (hd0,0)
chainloader     +1


Regards

---

### Post by Lush on 2005-12-13
Comp just hangs after i do this
with the following text:
```
Microsoft Win XP
rootnoverify (hd0,0)
chainloader +1
```

here is my windows boot.ini file
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


```

---

### Post by fannymites on 2005-12-13
I'm thinking windows boot details were at the start of the disk and have been overwritten by grub.
I'm not sure of the best way around this because if you use a windows rescue disk to fix the mbr you will lose grub.  Then if you re-install grub to the mbr it will mess up windows again.  I've always had windows and linux on seperate disks so I'm sure how to go about booting them both from one disk. 
One possible way I think would be to copy all the boot files from the root of your windows xp pro partition to the root of your xp home partition and point grub to that.
However, your boot.ini doesn't seem to match in with the fstab output.
Have you edited your boot.ini file yourself? try changing the first partition entry to partition(0) I can't remeber exactly but I think boot.ini, like grub count the first partition as 0, not 1.

[EDIT]  No, I'm wrong.  partition(1) is the first partition in boot.ini
Can you actually describe how your partitions are set out and how many hard drives you are using?
ie something like - 

disk 1
partition1 windows xp pro
partition2 windows xp home
partition3 ubuntu

disk 2 
partition1 windows 98
partition2 shared

I know you've posted the fstab output but personally, I didn't set up all of my partitons when installing ubunt so they don't show in fstab.

---

### Post by Lush on 2005-12-13
here is how i got it setup:

Only one Disk:
partition 1 xp pro
partition 2 xp home
partition 3 ext3 system for linux "/"
partition 4 ext3 system for linux "/home"
partition 5 Swap system for linux

i think i found how to fix this, i'll just boot grub from floppy ^_^. It should work out fine.

---

