---
title: "Dual booting"
date: 2009-04-23
forum: General Help
---

### Post by SvEnX on 2009-04-23
Hello,

I have recently installed new 9.04 x64. I really like it, it seems to be very stable and everything works like charm, exept dualbooting. I have a HDD with 2 partitions 1 pratition ext4 where the Ubuntu is sitting and another partition NTFS with Windows XP x64. The Windows option was not added automatically to grub, so I added it manually, but it still didn't work.
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096   83  Linux
/dev/sda2            6528        9038    20169607+   f  W95 Ext'd (LBA)
/dev/sda5            6528        9038    20169576    7  HPFS/NTFS


```

menu.lst is looking like this:
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=946fde6f-6c23-4329-9ee4-0e8a72b85801 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=946fde6f-6c23-4329-9ee4-0e8a72b85801

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		946fde6f-6c23-4329-9ee4-0e8a72b85801
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=946fde6f-6c23-4329-9ee4-0e8a72b85801 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		946fde6f-6c23-4329-9ee4-0e8a72b85801
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=946fde6f-6c23-4329-9ee4-0e8a72b85801 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		946fde6f-6c23-4329-9ee4-0e8a72b85801
kernel		/boot/memtest86+.bin
quiet

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I'v tried different options in loader, but non of them seem to be working

---

### Post by mosburn on 2009-04-23
Try setting your windows root partition to

root (hd0,4)

---

### Post by SvEnX on 2009-04-23
> **mosburn said:**
> Try setting your windows root partition to

root (hd0,4)

Ok, I'v tried with 

```
root (hd0,1)
root (hd0,2)
root (hd0,3)
root (hd0,4)

```

and the difference is

root (hd0,1) and root (hd0,4) ends up with error: Error 12: Invalid device requested
but with root (hd0,2) and root (hd0,3) I get: Error 8 : No such partition

---

### Post by SvEnX on 2009-04-27
Went for the easier way. I reinstalled everything and on new installation I used ext3 filesystem instead ext4. I think there aer some issues with dualbooting in ext4 what caused this problem, but I might be wrong.

---

