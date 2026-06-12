---
title: "grub loading wrong kernal"
date: 2009-05-01
forum: General Help
---

### Post by david kirkpatrick on 2009-05-01
I hope that this is the right forum for this if not please tell me which one it should be in.
 I have upgraded from 8.10 to 9.04 that was no problem it was not till I had to replace my video card with a new one that the problem started and may have been in existence from when I upgraded from 8.04. The new video card is NVIDIA  GF8400GS by PNY my old card was a ATI RADEON X550 (name on sticker on  back of card) When I tried to load the NVIDA drivers via envyNG it told me that the kernel was wrong, that sent me to the boot folder to see what menu.lst was loading on start up  see attached copy of menu.lst to see what I found. Can I just change the A) the root present root (hd0,0) 8.04 old kernel to root (hd2,0) new kernel 9.04 by changing the hd2,0 for 9.04 to hd0,0, and 8.04 to hd2.0 or just delete any mention of 8.04 from menu.lst and remove all the old kernels just leaving the new one, also because of the problem I remove all trace of NVIDIA drivers from my system which one do I reinstall. I have also (I hope) attached a picture of my boot folder to show you what is in there.
 Hope some one can help thanks in advance.
P.S sorry it's a bit long winded.

#A splash image for the menu
#splashimage=(hd2,0)/boot/grub/splashimages/54488-napoleon.xpm.gz
default 0
timeout 10
hiddenmenu

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
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
# kopt=root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dbdd4c7-3556-46b5-9da8-426e97f1cac7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[http://ubuntuforums.org/attachment.php?attachmentid=111980&stc=1&d=1241186407](http://ubuntuforums.org/attachment.php?attachmentid=111980&stc=1&d=1241186407)

---

### Post by david kirkpatrick on 2009-05-08
Ia actually fix this problem just the way that i suggested doing it in the message and it work a treat also fixed the graphics problem as well as the nvidia driver could now see that it was the matching kernel.

---

