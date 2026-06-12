---
title: "editing GRUB"
date: 2009-02-20
forum: General Help
---

### Post by oren tal on 2009-02-20
I am sure someone already asked this but I could not find it so I ask it.

I am using linux in daul boot and I want to edit the grub menu, or however it is called.

Right now if I don't press anything then it is loading linux.

However I want the default to be windows and only if I choose otherwise to load ubutu.

How do I edit it?
changing the grub options?

---

### Post by taurus on 2009-02-20
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And change the **default 0** option.

Otherwise, you can install startupmanager and use it to configure GRUB.

---

### Post by oren tal on 2009-02-20
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And change the **default 0** option.

Otherwise, you can install startupmanager and use it to configure GRUB.

thanks man.

---

### Post by oren tal on 2009-02-20
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And change the **default 0** option.

Otherwise, you can install startupmanager and use it to configure GRUB.

looking on it again it not clear to me what I need to do.
I run the command you told me and this is the text I got in that file:
```


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
# kopt=root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8053f43b-094a-46fe-90d3-8e10b78ebe64

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
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


What exactly do I need to change?

Thanks

---

### Post by taurus on 2009-02-20
> **oren tal said:**
> 
```


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		**[COLOR="DarkRed"]0[/COLOR]**

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
# kopt=root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8053f43b-094a-46fe-90d3-8e10b78ebe64

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
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8053f43b-094a-46fe-90d3-8e10b78ebe64 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8053f43b-094a-46fe-90d3-8e10b78ebe64
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


What exactly do I need to change?

Thanks
Change the 0 in red to **[COLOR="Blue"]6[/COLOR]** since windows is the 7th entry.  Unix/Linux counts from 0.

---

### Post by oren tal on 2009-02-20
> **taurus said:**
> Change the 0 in red to **[COLOR="Blue"]6[/COLOR]** since windows is the 7th entry.  Unix/Linux counts from 0.

no, it is the 6th entry.
So I guess I need to change it to 5.

But real thanks for your explanation.

---

### Post by taurus on 2009-02-20
No, it is the 7th entry.  Each **title** is counted as one entry.

Don't forget about an "empty" entry just before your windows.

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
**[COLOR="Red"]title[/COLOR]**		Other operating systems:
root

```

---

### Post by oren tal on 2009-02-20
> **oren tal said:**
> no, it is the 6th entry.
So I guess I need to change it to 5.

But real thanks for your explanation.

well I must have missed something.
When I use the program startupmanager, and change it to windows, then it indeed change it to 6 as you said.
So you were right.

However I don't see where are the 7th options.

And second when I used the editor to change it, if I put the number 5 then I don't see anything in  startupmanager line of default operating system, but when I change to the other number then I see the suitable operating system.

Does option 5 mean title "Other operating systems"?

---

### Post by oren tal on 2009-02-20
> **taurus said:**
> No, it is the 7th entry.  Each **title** is counted as one entry.

Don't forget about an "empty" entry just before your windows.

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
**[COLOR="Red"]title[/COLOR]**		Other operating systems:
root

```

**thanks.**
It was the exact thing I wanted to ask you.

:popcorn:

---

