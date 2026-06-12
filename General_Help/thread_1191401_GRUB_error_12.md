---
title: "GRUB error 12"
date: 2009-06-18
forum: General Help
---

### Post by FraggedLocust on 2009-06-18
I recently decided to get my Ubuntu partition working again after installing Windows for school, and of course I lost my Ubuntu partition because of the Windows rewrite of the MBR. I've heard good things about SuperGrub, so I decided to give it a try. I used it to repair GRUB with the option /boot/grub/stage1.

GRUB is working again, But now when I try to load the Vista chainloader, I get an Error 12.

fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71ca1ba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1362    10940233+   5  Extended
/dev/sda2   *        1363       19458   145348608    7  HPFS/NTFS
/dev/sda5               1        1298    10426122   83  Linux
/dev/sda6            1299        1362      514048+  82  Linux swap / Solaris
```

menu.lst:
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
# kopt=root=UUID=f8aa6258-1a91-4f65-9e97-bf7af08aa985 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8aa6258-1a91-4f65-9e97-bf7af08aa985

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f8aa6258-1a91-4f65-9e97-bf7af08aa985
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f8aa6258-1a91-4f65-9e97-bf7af08aa985 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f8aa6258-1a91-4f65-9e97-bf7af08aa985
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f8aa6258-1a91-4f65-9e97-bf7af08aa985 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f8aa6258-1a91-4f65-9e97-bf7af08aa985
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f8aa6258-1a91-4f65-9e97-bf7af08aa985 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f8aa6258-1a91-4f65-9e97-bf7af08aa985
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f8aa6258-1a91-4f65-9e97-bf7af08aa985 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f8aa6258-1a91-4f65-9e97-bf7af08aa985
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by Villiam on 2009-06-18
You may like to check a discussion thread over here where Grub error 12 is discussed: [http://ubuntuforums.org/showthread.php?t=464695](http://ubuntuforums.org/showthread.php?t=464695)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by lindsay7 on 2009-06-18
Change this```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```


To this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```


Note: this is because windows boot is on hd0,1 as seen here where sda2 would equal hd0,1



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1362    10940233+   5  Extended
/dev/sda2   *        1363       19458   145348608    7  HPFS/NTFS


type this in the terminal "sudo gedit /boot/grub/menu.lst"  without the quotes and that is the letter l not number 1 in "lst"

Make the change and save the file. Do not change anything else.

---

### Post by merlinus on 2009-06-18
Try changing this:

title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

to this:

title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2009-06-18
Hey indsay, great minds think alike!

---

### Post by lindsay7 on 2009-06-18
Not only that but I am a LOBO too!!

---

