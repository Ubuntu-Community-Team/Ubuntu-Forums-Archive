---
title: "Some help with the boot :)"
date: 2009-05-09
forum: General Help
---

### Post by nickozor on 2009-05-09
Ok so I have been trying to fix this "Error 13 Invalid or unsupported executable format" for a couple days now and nothing has worked. Here's the lay down...

I have two SATA drives, One has WINXP, other Ubuntu(9.04). GRUB loads up fine and I'm able to load up Ubuntu fine, but with XP I get that error 13. I have gone into recovery console and fixed my MBR and that didn't work, I have also tried to change the root and that didn't work. I don't know if this matters but I'm able to load up XP if I go into my BOIS and change the order of the drives for booting up.

Here is my menu.lst
```
splashimage (hd1,0)/boot/grub/splashimages/97109-bam.xpm.gz
default 2
timeout 10
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
# kopt=root=UUID=d7144bec-6f56-498b-9cec-980b1e4cb578 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7144bec-6f56-498b-9cec-980b1e4cb578

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
# defoptions=quiet splash

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
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title Ubuntu 9.04
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d7144bec-6f56-498b-9cec-980b1e4cb578 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04 (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d7144bec-6f56-498b-9cec-980b1e4cb578 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1
savedefault
makeactive

```

Here is my fdisk -lu
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdeccdecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   468744569   234372253+  83  Linux
/dev/sda2       468744570   488392064     9823747+   5  Extended
/dev/sda5       468744633   488392064     9823716   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba1cba1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488375999   244187968+   7  HPFS/NTFS

```

Also my boot.ini
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Any help would be greatly appreciated.

---

### Post by dandnsmith on 2009-05-09
[i]"title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1
savedefault
makeactive"[/i]

Looks at odds with the Windows being on sdb1, which would be
(hd1,0) to grub

I'd try using 
[i] map (hd0) (hd1)
map (hd1) (hd0)[/i]
before the *rootnoverify (hd0,0)*
and that might do it

---

### Post by nickozor on 2009-05-09
The map and changing the root to (hd1,0) worked!!!!

Thank you so much!

---

