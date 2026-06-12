---
title: "power failure"
date: 2009-04-20
forum: General Help
---

### Post by richard@ramcp.com on 2009-04-20
please can someone help I am using ubuntu 8.10 my system was shutdown due to a power failure and I can not get it back.I get the following message..
Find -- set-root ignor floppies / menu, 1st
error 15: file not found press any key to continue.
I am at the stage of removing and re installing.

Thanks Richard

---

### Post by Hellstudios on 2009-04-20
it sounds like menu.lst is broken.... I don't know if you'd be able to fix this, but I'm pretty sure it's that.

---

### Post by Hellstudios on 2009-04-20
boot from the ubuntu live CD, go to places, your hard drive with ubuntu on it, go to boot, grub, then look for menu.lst, open it with text editor, then replace everything with this:

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
# kopt=root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2

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
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


tell me if that works.


EDIT: find and online md5 hasher and replace ```
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
``` with ```
#      password --md5 your hash here
```

[http://www.miraclesalad.com/webtools/md5.php](http://www.miraclesalad.com/webtools/md5.php)

---

### Post by richard@ramcp.com on 2009-04-21
> **Hellstudios said:**
> boot from the ubuntu live CD, go to places, your hard drive with ubuntu on it, go to boot, grub, then look for menu.lst, open it with text editor, then replace everything with this:

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
# kopt=root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2

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
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


tell me if that works.


EDIT: find and online md5 hasher and replace ```
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
``` with ```
#      password --md5 your hash here
```

[http://www.miraclesalad.com/webtools/md5.php](http://www.miraclesalad.com/webtools/md5.php)
Thank you for the information.
Problem is I don't have the disc I got my copy on line when I upgraded from 8.04
any more thoughts?

---

### Post by prem1er on 2009-04-21
Download another disc and burn it, or if your computer is able to boot from a usb you can directly boot ubuntu from a flash drive.

---

### Post by Kareeser on 2009-04-21
> **Hellstudios said:**
> boot from the ubuntu live CD, go to places, your hard drive with ubuntu on it, go to boot, grub, then look for menu.lst, open it with text editor, then replace everything with this:

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
# kopt=root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2

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
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9e7f4f08-f076-4a4e-b6c4-79017b6c6ea2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


tell me if that works.


EDIT: find and online md5 hasher and replace ```
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
``` with ```
#      password --md5 your hash here
```

[http://www.miraclesalad.com/webtools/md5.php](http://www.miraclesalad.com/webtools/md5.php)

**STOP**

The contents of your menu.lst are different from his! Especially the UUIDs. You could be doing more harm than good.

Just google "Ubuntu error 15" and read up on the problem.

---

