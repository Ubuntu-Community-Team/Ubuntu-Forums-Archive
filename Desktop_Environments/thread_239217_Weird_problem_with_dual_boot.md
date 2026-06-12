---
title: "Weird problem with dual boot"
date: 2006-08-18
forum: Desktop Environments
---

### Post by totalnoob on 2006-08-18
I had windows XP sp2 installed then installed ubuntu on it's own partition. 
WhenI boot up grub does not give the option to boot windows it ONLY shows ubuntu. Here is my grub file..

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Please help me get XP back on the boot list. I know it exists because I can access all the files and see the NTFS partition from ubuntu. 

THANK YOU ALL!

---

### Post by Herman on 2006-08-18
totalnoob,
All you probably need to do is copy the bottom section (everything below where it says '                        ### END DEBIAN AUTOMAGIC KERNELS LIST' of the example of a typical menu.lst file, [click here,]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst")
 and then paste that under the same place in your own menu,lst file and save the changes.
You did not include any copy of your partition information such as the output from 'sudo fdisk -lu' or other information as to whether yours is a typical installation with Windows as (hd0,0) (partition 1), so I am presuming this is a typical installation.
If it is different, you may need to edit the commands. If you need more help, please post the result from the following command ```
sudo fdisk -lu
``` or provide some accurate partitioning information and someone will be able to provide you with some system-specific help.
It will be safe to edit the words on the line after the command 'title' if yours is not 'Windows XP Home Edtition'. You can type anything there you like.
You may need to replace the command '[root]("http://www.gnu.org/software/grub/manual/grub.html#root")' with '[rootnoverify]("http://www.gnu.org/software/grub/manual/grub.html#rootnoverify")' if you have the NTFS filesystem and you get any error message. More information can be found on the [*this page*]("http://users.bigpond.net.au/hermanzone/p15.htm") about how to edit your menu.lst file and customize grub.
Regards, Herman :D

---

