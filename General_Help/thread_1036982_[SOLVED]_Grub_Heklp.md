---
title: "[SOLVED] Grub Heklp"
date: 2009-01-11
forum: General Help
---

### Post by ltlbgr67 on 2009-01-11
Hi,

I am new to ubuntu.
Here is my problem.  I was (am) using windowsxp.  Had it on a 120 gig hard drive that was getting full.  Decided to get new hard drive, partitioned it ok, installed xp first then ubuntu.  Got grub to boot either.
Now I would like to add the old hard drive and have grub boot that as a choice also.
Ubuntu sees the old hard drive after I installed it.  Here is what my grub code looks like, I added the last tone "Title xp old vers" thinking that it would be boot to the second hd(1,0) at the root parttion.
What am I doing wrong, does grub need to know I installed the second hard drive? I cannot figure out how to do that if that is the problem.

Any help is greatly appreciated.


default 0
timeout 10

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
# kopt=root=UUID=cc70f239-9df0-43dd-a26f-1106df0e303e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cc70f239-9df0-43dd-a26f-1106df0e303e

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

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=cc70f239-9df0-43dd-a26f-1106df0e303e ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=cc70f239-9df0-43dd-a26f-1106df0e303e ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cc70f239-9df0-43dd-a26f-1106df0e303e ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cc70f239-9df0-43dd-a26f-1106df0e303e ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

title xp old vers
root (hd1,0)
chainloader +1
savedefault
makeactive

---

### Post by caljohnsmith on 2009-01-11
How about trying this entry instead:
```
title       Windows XP Old Ver
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, please let me know exactly what happens when you try it from the Grub menu, and also post:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by ltlbgr67 on 2009-01-11
caljohnsmith,

Thank you for the quick reply.  It WORKED.  Thank you.

Paul.

Sorry it took so long to respond back!!!!

---

