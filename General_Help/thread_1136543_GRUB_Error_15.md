---
title: "GRUB: Error 15"
date: 2009-04-25
forum: General Help
---

### Post by RuleMaker on 2009-04-25
I messed up my GRUB and now all I can do is boot from the live CD. I was reading a lot about this and tried everything but no success, after reboot im getting the same error.

---

### Post by zvacet on 2009-04-25
Is [this]("http://users.bigpond.net.au/hermanzone/p15.htm#15") of any help to you?

---

### Post by regor210 on 2009-04-25
Did you use Jaunty's  Alt CD and ext4 file system to install Ubuntu on your computer?

---

### Post by RuleMaker on 2009-04-25
Thanks for quick replies, but it seems that my menu.lst is correct, i cant find any mistyping here:

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
# kopt=root=UUID=7e90b601-4b2c-4693-9a58-d14b2ff746b3 ro

## default grub root device
## e.g. groot=(hd0,0)
#groot=7e90b601-4b2c-4693-9a58-d14b2ff746b3

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

uuid		7e90b601-4b2c-4693-9a58-d14b2ff746b3
splashimage=/boot/grub/splash.xpm.gz

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7e90b601-4b2c-4693-9a58-d14b2ff746b3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7e90b601-4b2c-4693-9a58-d14b2ff746b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7e90b601-4b2c-4693-9a58-d14b2ff746b3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7e90b601-4b2c-4693-9a58-d14b2ff746b3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7e90b601-4b2c-4693-9a58-d14b2ff746b3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

And here is what i have in directories:
```
ubuntu@ubuntu:~$ ls /media/tmp/boot/
abi-2.6.28-11-generic	      memtest86+.bin
config-2.6.28-11-generic      System.map-2.6.28-11-generic
grub			      vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
```

```
ubuntu@ubuntu:~$ ls /media/tmp/boot/grub/
default        installed-version  minix_stage1_5     stage1
device.map     jfs_stage1_5       reiserfs_stage1_5  stage2
e2fs_stage1_5  menu.lst           splashimages       xfs_stage1_5
fat_stage1_5   menu.lst~          splash.xpm.gz
```

After editing my menu.lst yesterday I cant boot my xubuntu CD anymore so I have to use ubuntu, that's really strange.

---

### Post by bumanie on 2009-04-25
Post the output of > sudo fdisk -l

---

### Post by RuleMaker on 2009-04-25
Oops, I was stupid :D
If you look at the screenshot you can see what mistake I made...setup (hd0,4) insted of setup (hd0).

Now I just need to re-edit my menu.lst to fix what I've messed up.

---

