---
title: "GRUB Issues"
date: 2009-04-13
forum: General Help
---

### Post by Patricrawley on 2009-04-13
I installed Windows 7 a while ago and then added Ubuntu to the Windows bootloader. But then I played around with Suse and then installed Jaunty and now when I go with the Windows option in GRUB all my PC does is restart and go back to Grub. This is my Grub menu:
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
# kopt=root=UUID=b2156685-08ee-4334-a4ce-12668eee9620 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b2156685-08ee-4334-a4ce-12668eee9620

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		b2156685-08ee-4334-a4ce-12668eee9620
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b2156685-08ee-4334-a4ce-12668eee9620 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		b2156685-08ee-4334-a4ce-12668eee9620
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b2156685-08ee-4334-a4ce-12668eee9620 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		b2156685-08ee-4334-a4ce-12668eee9620
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

### Post by AXeS on 2009-04-13
Could you give more information.

Like : is it on 1 drive, partitioned? or seperate drives? Sata? or IDE? (might need that info if you did installs on seperate HDD.

---

### Post by brunogirin on 2009-04-13
> **Patricrawley said:**
> I installed Windows 7 a while ago and then added Ubuntu to the Windows bootloader. But then I played around with Suse and then installed Jaunty and now when I go with the Windows option in GRUB all my PC does is restart and go back to Grub. This is my Grub menu:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

The bit of code at the end of your GRUB config tells it to chainload whatever boot loader is on the first partition of hd0, which is presumably where your Windows 7 partition is. Unfortunately, it looks like that boot loader is GRUB itself so it chainloads itself. To resolve this you can do one of two things:

1. Change that entry so that it loads W7 directly.
2. Install the Windows 7 boot loader in the first sector of partition hd0,0: in this case, you would have GRUB in the MBR of hd0 (i.e. before any partition) and a secondary boot loader with W7 in hd0,0.

I'm not sure how you would do either though.

---

### Post by defaultusername on 2009-04-13
Patricrawley,

Are you sure W7 is located on (hd0,0)? Did W7 ever work? When you say you played around with OpenSUSE and installed Jaunty, what did your partition table look like previously and what does it look like now?

---

### Post by brunogirin on 2009-04-13
> **brunogirin said:**
> I'm not sure how you would do either though.

Have a look at [Herman's SuperGrubDisk page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), it is a good place to start from.

---

### Post by AXeS on 2009-04-13
> **brunogirin said:**
> The bit of code at the end of your GRUB config tells it to chainload whatever boot loader is on the first partition of hd0, which is presumably where your Windows 7 partition is. Unfortunately, it looks like that boot loader is GRUB itself so it chainloads itself. To resolve this you can do one of two things:

1. Change that entry so that it loads W7 directly.
2. Install the Windows 7 boot loader in the first sector of partition hd0,0: in this case, you would have GRUB in the MBR of hd0 (i.e. before any partition) and a secondary boot loader with W7 in hd0,0.

I'm not sure how you would do either though.


im no expert but i think you have to check in terminal what drive your windows 7 is installed or just change your menu.lst file contents.

if you wana have windows 7 back, what you can do is :

1. if you cant get into an ubuntu terminal then use the live cd and install ms-sys ( i did this manually because it's not in the repo's) and re-install your poriginal mbr with that in terminal... im sorry if i can give you anymore info, but it's a lead...im searching for that same thread that helped right now as we speak.

2.edit you /boot/grub/menu.lst under live cd terminal to map drives and change the settings maybe.

---

### Post by Patricrawley on 2009-04-13
The setup I initially had was XP and Ubuntu, then I installed 7 and couldn't get into Ubuntu but I added Ubuntu to the Windows bootloader with a Grub install on had0,1. That setup worked fine and when I installed opensuse it loaded windows 7 just fine from it's bootloader. But I decided to go back to Ubuntu and when I installed it the Grub bootloader wouldn't load 7. 7 is on hda0,0, ubuntu: hd0,1, swap:hd0,2, ubuntu-home:hd0,3.

---

### Post by Patricrawley on 2009-04-13
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dd23884

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6324    50795520    7  HPFS/NTFS
/dev/sda2            6324        8756    19535040   83  Linux
/dev/sda3            8756        8999     1951897+  82  Linux swap / Solaris
/dev/sda4            8999       30401   171912551   83  Linux

```

---

### Post by AXeS on 2009-04-13
i think you should ms-sys...
Here try these:

[http://ubuntuforums.org/showthread.php?t=1119807&highlight=ms-sys](http://ubuntuforums.org/showthread.php?t=1119807&highlight=ms-sys)

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by brunogirin on 2009-04-13
It looks to me like you your GRUB config is ok in the MBR but you need to restore a Windows 7 boot loader in the first sector of hd0,0 so that the GRUB can chainload it. See if [Super Grub Disk]("http://www.supergrubdisk.org/") can help.

---

