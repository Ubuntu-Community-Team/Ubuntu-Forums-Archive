---
title: "kernel problem???"
date: 2008-12-22
forum: General Help
---

### Post by neu2buntu on 2008-12-22
problem is that i did a kernel update, but while installing it i chose option "keep current menu.lst"  (because when i choose "use maintainers version it automatically add option vga=796 0r similar, this vga= gives me startup probs and then i have to edit all kernels)

two questions really
(1) how do i stop this vga=796 option from being added?


(2) how do i reinstall or get the kernel to show in menu.lst?


.....:confused:

---

### Post by neu2buntu on 2008-12-22
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3707842f-a5ff-46c1-bd31-b16a11089977

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
# defoptions=splash quiet vga=796

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

title        Ubuntu 8.10, kernel 2.6.27-10-generic
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro splash quiet  
initrd        /boot/initrd.img-2.6.27-10-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-10-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro  single
initrd        /boot/initrd.img-2.6.27-10-generic

title        Ubuntu 8.10, kernel 2.6.27-8-generic
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro splash quiet 
initrd        /boot/initrd.img-2.6.27-8-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro  single
initrd        /boot/initrd.img-2.6.27-8-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro splash quiet 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-3-rt
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-3-rt root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro splash quiet 
initrd        /boot/initrd.img-2.6.27-3-rt
quiet

title        Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/vmlinuz-2.6.27-3-rt root=UUID=3707842f-a5ff-46c1-bd31-b16a11089977 ro  single
initrd        /boot/initrd.img-2.6.27-3-rt

title        Ubuntu 8.10, memtest86+
uuid        3707842f-a5ff-46c1-bd31-b16a11089977
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        BackTrack 3
root            (hd0,2)
kernel          /boot/syslinux/lilo rw
initrd          /boot/initrd.gz
boot
```

here is my menu.lst..................ps i cant boot backtrack either (error is something to do with not enough video ram, think its to do with me using an acer aspire one)..but i will post this another time..lol

---

