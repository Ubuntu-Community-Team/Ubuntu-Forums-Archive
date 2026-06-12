---
title: "Grub Missing - WinXP loads automatically"
date: 2009-04-25
forum: General Help
---

### Post by Vitamin-Carrot on 2009-04-25
:(

Hey guys,

So I have been having an issue after performing a complete reinstall (everything) I reinstalled windows XP pro (x86) first and did the usual 1 hour drivers, sp3 install sit in. Windows XP hdd (hd1,0)

Then installed ubuntu 9.04 64bit onto the hdd i wanted it on (hd2,0), unfortunately after the install finished it seems that grub has not even been installed or is not writing to the mbr (hd0)
so in the usual response i performed the following

```
sudo grub
find /boot/grub/stage1
root (hd2,0)
setup (hd0)
quit
sudo reboot
```

this doesnt prompt with any errors and has not worked at all as my machine still boots into windows and still appears to not have grub installed. now i am back into the live cd trying to find anything and everything in regards to this issue. if anyone can help it would be awesome.

fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5453ea93

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9faf9fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25e9b22b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9726    78124063+  83  Linux
/dev/sdc2            9727        9964     1911735    5  Extended
/dev/sdc5            9727        9964     1911703+  82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8bbf8bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14593   117218241   83  Linux

```

menu.lst
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
# kopt=root=UUID=47b8c28b-d066-4301-94ba-3fef2d1e5fd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=47b8c28b-d066-4301-94ba-3fef2d1e5fd1

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
uuid		47b8c28b-d066-4301-94ba-3fef2d1e5fd1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=47b8c28b-d066-4301-94ba-3fef2d1e5fd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		47b8c28b-d066-4301-94ba-3fef2d1e5fd1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=47b8c28b-d066-4301-94ba-3fef2d1e5fd1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		47b8c28b-d066-4301-94ba-3fef2d1e5fd1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

grub setup results
```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

```

Unfortunately it doesnt seem to work as the machine still loads straight into windows - so again please help everything was fine with ubuntu 8.10 64 bit and now 9.04 just doesnt seem to want to play nice

---

### Post by meierfra. on 2009-04-25
Install grub with

```
sudo grub
root (hd2,0)
setup (hd2)
quit
```

Then reboot, but make sure that your bios are set to boot from the  81.9GB  Ubuntu drive

---

### Post by Vitamin-Carrot on 2009-04-25
Cheers,

I have already fixed it
my 1tb ntfs storage drive was being seen as sda so setup (hd0) was going to that - unfortunately the side effect of this seems to be that that hdd is no longer mountable due to a corruption so i unpluged the hdd and reinstalled 9.04 so that the hdd with windows on it is now seen as sda or (hd0) this fixed the grub issue but due to the corruption i am now running test disk to get all my data back.

a bit of a pain when you have friends over with their machines wanting to play L4D

---

### Post by meierfra. on 2009-04-25
> unfortunately the side effect of this seems to be that that hdd is no longer mountable due to a corruption

Did you ever use

```
sudo grub 
root (hd2,0)
setup (hd2,0)

```
If yes, use "backup BS" in testdisk  to fix the boot sector.

---

