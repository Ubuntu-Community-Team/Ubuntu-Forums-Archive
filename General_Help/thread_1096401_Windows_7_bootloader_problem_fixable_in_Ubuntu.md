---
title: "Windows 7 bootloader problem fixable in Ubuntu?"
date: 2009-03-14
forum: General Help
---

### Post by tiddlydum on 2009-03-14
Up until recently, I was running a dual-boot Ubuntu & Windows XP system. The two OS were on the same drive. Then, I tried installing Windows 7 on a different drive. I lost GRUB, but found I still had my old systems in their partitions. So, I reinstalled grub. My problem is, when I try to boot XP, GRUB loads the Windows 7 bootloader. As my only active OS on the computer, I was wondering if I could fix this using Ubuntu's terminal or GRUB's terminal. Any help would be greatly appreciated.

---

### Post by circa82 on 2009-03-14
Would mind posting your menu.lst file along with the ouput of fdisk -l? 

From a terminal (Applications > Accessories > Terminal):
```
# [color=blue]sudo fdisk -l[/color]  <-- lowercase L

# [color=blue]cat /boot/grub/menu.lst[/color]
```

---

### Post by tiddlydum on 2009-03-15
sudo fdisk -l returns

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe18ae18a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50993   409601241    7  HPFS/NTFS
/dev/sda2           50994       51966     7815622+   5  Extended
/dev/sda3           51967       77825   207712417+  83  Linux
/dev/sda5           50994       51966     7815591   82  Linux swap / Solaris
```

```
cat /boot/grub/menu.lst returns
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=26699c6c-b3d8-4ee8-970d-d804b0423cd0

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26699c6c-b3d8-4ee8-970d-d804b0423cd0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		26699c6c-b3d8-4ee8-970d-d804b0423cd0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1 
```

Thanks for your help. 
P.S. I removed the drive that Windows 7 was on, so this is only listing one drive. The bootloader seems to be installed where GRUB thinks XP is installed. $%^£*&^ windows.

---

