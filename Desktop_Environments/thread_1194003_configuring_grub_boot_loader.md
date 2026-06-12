---
title: "configuring grub boot loader"
date: 2009-06-22
forum: Desktop Environments
---

### Post by dazman19 on 2009-06-22
Hi,

Currently running jaunty 9.04 and think its great!
I have a spare hard disk. In my case its /dev/sdb1 

I am going to a LAN and need to install a few games which I unfortunately cant seem to get working on wine very well. And I also want to put a copy of archlinux on it.

So I am to make 2 partitions, 1 for NTFS windows and 1 for archlinux ext3. (I have 8gb of ram so i am not gonna run swap for archlinux).

I will do windows XP first.. as i need it to run some games:
And I have backed up /boot/grub/menu.lst

My question is, after I install windows to that disk and want to edit menu.lst to give me the option of either ubuntu or xp. 

I dont understand these grub configuration commands:
- root (hd0,0)
- setup (hd0) 

is the root (***) my boot loaders hard drive? And is the setup the drive I want to set up? 

Also to add it to the menu what would you add?

title Windows XP
root (????)
makeactive
chainloader +1

here is my current menu.lst and /etc/fstab and I have not yet installed windows.

menu.lst
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
# kopt=root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=893c0d9e-fe59-4b17-b756-a2eff952973d

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
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=893c0d9e-fe59-4b17-b756-a2eff952973d /               ext3    relatime,errors=remount-ro 0       1
# /seagate160/ was on /dev/sdb1 during installation
UUID=a99cfbaa-65b4-42f4-bb61-97de5a5bc564 /seagate160/    ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=421d666a-7604-4ad3-85f7-e8373b32b309 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /data                   ntfs    defaults        0       0
/dev/sdd2       /video          ntfs    defaults        0       0

---

