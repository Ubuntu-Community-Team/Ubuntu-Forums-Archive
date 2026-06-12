---
title: "Boot Problem"
date: 2009-03-28
forum: General Help
---

### Post by dazzler on 2009-03-28
Need some assistance, dont know what happened but i cannot boot into windows 7 (Dont ask the family use it)

I have Ubuntu on one disk, Windows 7 another disk and one sata disk with media on it.

Now i can boot into Ubuntu fine but when i select Windows in grub i just get Starting Up...

I have tried /fixboot and /fixmbr from a Vista disk but its still the same.

In the style of Daphne ...HEYELP

---

### Post by DeMus on 2009-03-28
> **dazzler said:**
> Need some assistance, dont know what happened but i cannot boot into windows 7 (Dont ask the family use it)

I have Ubuntu on one disk, Windows 7 another disk and one sata disk with media on it.

Now i can boot into Ubuntu fine but when i select Windows in grub i just get Starting Up...

I have tried /fixboot and /fixmbr from a Vista disk but its still the same.

In the style of Daphne ...HEYELP

Please open a terminal and post the output of
```
fdisk -l
```

and post also the file /boot/grub/menu.lst.
Then we can see what's going on.

---

### Post by dazzler on 2009-03-28
fdisk -l output

```
dazzler@ubuntudesktop:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0d1e77c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38765   293057320+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc620c620

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30402   244204033+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b657bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18701   150215751   83  Linux
/dev/sdc2           18702       19457     6072570    f  W95 Ext'd (LBA)
/dev/sdc5           18702       19457     6072538+  82  Linux swap / Solaris
dazzler@ubuntudesktop:~$ 


```

Menu.lst

```
splashimage=/boot/grub/splashimages/77664-The_Linux_Force.xpm.gz
default 4
timeout 5
color white/black 

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=788

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

```

Thanks

---

### Post by Zalbor on 2009-03-28
It seems you have 3 hard drives on your computer, one of which has ubuntu and the other two an NTFS filesystem. Do you know which hard drive is the one that has windows 7? And, is there another installation of windows on the other one, or is it just a partition used for storage?

---

### Post by dazzler on 2009-03-28
Thats right one windows, one ubuntu, one just data.

The one with windows is 250gb so i presume its sdb1

---

### Post by Zalbor on 2009-03-28
Try rebooting the computer, and when you get to grub, highlight the windows option and press 'e'. Then highlight the line that reads "root (hd0,0)" and press 'e' again.
Edit the line, changing it to "root (hd1,0)". Then press enter, and 'b' to boot.

If that works for loading windows, you can make the change permanent by opening the /boot/grub/menu.lst file (using a command like "gksudo gedit /boot/grub/menu.lst") and edit the same line in the end of the file.

EDIT: Sorry, made a typo in how you should change the line. I corrected it.

---

### Post by dazzler on 2009-03-28
Legend worked a treat :) thanks a bunch

Thought you were on to something because I swear my vista drive used to be sda so somewhere they've swapped over.

Anyway it's all good I and my daughter especially now she can play toontown thank you

---

### Post by mhgsys on 2009-03-28
no help needed here anymore then> ( I wrote a long story about mapping disks in the first place)
btw? 
If that works, Does it mean that windows7 doesn't need to think it's on hd0?? , like the other Windows versions??
I'm used to map disks in cases like this.

---

### Post by dazzler on 2009-03-28
Apparently so, it works a treat again now.

Like i hinted earlier it has always been on hd0,0 previously but it works fine all as suggested earlier.

---

