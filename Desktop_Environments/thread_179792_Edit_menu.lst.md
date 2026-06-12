---
title: "Edit menu.lst?"
date: 2006-05-20
forum: Desktop Environments
---

### Post by majkmil on 2006-05-20
Here is my ( menu.lst ) file. My Kernel is 2.6.15.23-k7. Should I edit the file to show my kernel only and do I need to remove the kernels also? How? Seems very clutered.   Thanks

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-22-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-22-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-22-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-22-k7
boot

title		Ubuntu, kernel 2.6.12-10-k7-smp
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7-smp
boot

title		Ubuntu, kernel 2.6.12-10-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, kernel 2.6.12-10-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-k7-smp
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-k7-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-k7-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-k7-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-k7-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-k7-smp
boot

title		Ubuntu, kernel 2.6.12-9-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by barbarian on 2006-05-20
If you successfully use 2.6.15.23-k7, you can safely remove all the rest accept 'recovery mode' kernel, by using apt-get remove.

---

### Post by adamkane on 2006-05-20
Use > , when you have a long text to paste:

[ quote]
blah blah
[ /quote]

You've got quite a mess here.  The latest kernel you've installed always ends up at the top. 

First:
```

sudo gedit /boot/grub/menu.lst

``` 
The last part of the menu should look like this:

[quote]
[FONT=Courier New] ## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-23-k7
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-k7
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-k7
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST[/FONT]                


---

### Post by Jucato on 2006-05-20
You can also simply uninstall (through Adept or apt-get) the older/unused kernel versions. This will automatically remove those entries in the menu.lst.

Unless of course, you manually edited menu.lst to include those entries in the first place. :D

---

