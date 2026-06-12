---
title: "Change default OS in GRUB"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by oldtraveler on 2007-08-14
In my Grub list (shown below) I dont find either a timeout or a default # - just the word "savedefault".  I would like to edit the list to set a 4 second timeout and change the default OS to boot to the Windows loader.

How may I do this?

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
# kopt=root=UUID=66627aa3-2b7c-4589-9ffd-8ddc9e12fb40 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,7)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=66627aa3-2b7c-4589-9ffd-8ddc9e12fb40 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=66627aa3-2b7c-4589-9ffd-8ddc9e12fb40 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=66627aa3-2b7c-4589-9ffd-8ddc9e12fb40 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=66627aa3-2b7c-4589-9ffd-8ddc9e12fb40 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		pclinuxos (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hdb6 ro noapic nolapic acpi=ht nomce psmouse.proto=imps splash=silent 
initrd		/boot/initrd-2.6.12-oci6.mdk-i586-up-1GB.img
savedefault
boot

---

### Post by logos34 on 2007-08-14
It's staring you right in the face--at the top.  Change it thus:

> 
...

#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default 6**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout 4**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

...



('6' because Grub starts counting 'title' lines from 0.  windows is the seventh line down)

---

### Post by oldtraveler on 2007-08-14
Thank you.  I thought all that wording at the top was just instructions.

Anyway I made the changes and when I went to save them it told me I don't have the permissions necessary to save the file.  What gives?

---

### Post by kebes on 2007-08-14
> **oldtraveler said:**
> I made the changes and when I went to save them it told me I don't have the permissions necessary to save the file.  What gives?

You need admin privilege to edit that file. So in a terminal type:
```

gksudo gedit /boot/grub/menu.lst

```

And then enter your password when prompted.

(If you prefer pure a terminal interface, you can instead use "sudo nano /boot/grub/menu.lst")

---

### Post by logos34 on 2007-08-14
your need to open with root permisisons:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

EDIT: or use nano editor as kebes suggested above.  Use 'gksudo', Avoid using 'sudo gedit' -- not a good idea to open external applications from the terminal as root

---

### Post by oldtraveler on 2007-08-14
Thank you again.  I am trying that now.  

The file saved OK.  Now to see what happens upon reboot.

Works like a charm.

---

