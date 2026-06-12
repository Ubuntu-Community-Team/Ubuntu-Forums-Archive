---
title: "Booting freebsd with ubuntu's grub"
date: 2009-06-20
forum: General Help
---

### Post by gawadelnil2002 on 2009-06-20
im going to install freebsd on partition sd2 and i dont wanna keep ubuntu grub the boot loader for my computer i have ubuntu the only operating system on my computer now and grub installed on hda(0,0) and i will attach my menu.list ,all i want to know how i can boot freebsd from grub after installing it, i knew that i can choose when i install free bsd option like dont touch boot loader so i have to do mannully the boot options for free bsd but i dont what to write :)   can any body help me?

---

### Post by gawadelnil2002 on 2009-06-20
that is my menu.list
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
# kopt=root=UUID=e5db2f67-14c5-420a-bafc-590de914390c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e5db2f67-14c5-420a-bafc-590de914390c

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

uuid        e5db2f67-14c5-420a-bafc-590de914390c
splashimage=/boot/grub/splash.xpm.gz

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        e5db2f67-14c5-420a-bafc-590de914390c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=e5db2f67-14c5-420a-bafc-590de914390c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        e5db2f67-14c5-420a-bafc-590de914390c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=e5db2f67-14c5-420a-bafc-590de914390c ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, memtest86+
uuid        e5db2f67-14c5-420a-bafc-590de914390c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by paul_in_london on 2009-06-25
I'm planning to do this myself soon.

As you know, I think, FreeBSD uses a,b,c etc to represent its "partitions" within the slice allocated to it during the install and "a" is FreeBSD's root partition within that slice so you need an entry like this in your **/boot/grub/menu.lst**:

[B]title  FreeBSD <your_version>
root (hd0,1,a) 
kernel /boot/loader
[/B]

where **hd0** in grub-speak is your first hard disk i.e. **hda/sda** in Linux-speak and "**1**" represents your BSD slice (i.e. your **2nd** primary/Linux/BIOS partition because legacy grub counts from 0). I think it needs to be primary by the way.

If you had FreeBSD installed on the third Linux/BIOS partition (or  slice in BSD-speak) on hdb/sdb then you would use:

[B]root (hd1,2,a)
[/B]

This approach calls the FreeBSD boot loader program (/boot/loader) on the FreeBSD partition as if it were a kernel.

(When you migrate to grub2 it'll be grub.cfg instead of menu.lst and you'll need to adjust your FreeBSD stanza slightly). 

Another possibility would be:

[B]title  FreeBSD <your_version>
rootnoverify (hd0,1,a) 
chainloader +1
[/B]

but I think for this last one to work you would need to have FreeBSD's boot manager installed within the FreeBSD slice (not in the MBR).

HTH

---

### Post by gawadelnil2002 on 2009-07-04
Thank u thank thank u thank u i thought no one will answer this and i made alot of searchs before i see ur post and its excatly the same but u made me more sure to start playing :)

---

