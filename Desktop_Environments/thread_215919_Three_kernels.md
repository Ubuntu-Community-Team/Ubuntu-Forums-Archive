---
title: "Three kernels?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Amatsu Mikaboshi on 2006-07-14
Ok, so, I'm new to Linux and I just installed Ubuntu (Dapper) and after I got all the available updates, when I boot, in the GRUB menu there are three identical kernals. (The normal, the recovery consoles, and the mem one, and my Windows OS.)

Is there something I did wrong or is this some kind of glitch that can be fixed rather easily? I wouldn't know where to start or why this is happening but, I'd appriciate the help.

---

### Post by Paerez on 2006-07-14
The first is the normal kernel. The second is the same kernel, but it will boot you into a terminal as root so you can do emergency repair. The third tests your memory.

They are not different kernels, just different ways of booting the kernel for different purposes.

It doesn't have to be "fixed" because thats how it supposed to be.

---

### Post by Amatsu Mikaboshi on 2006-07-14
No, It lists it as following. (The exact numbers aren't right...so I'll just put "Numbers".)

Ubuntu Linux Numbers
Same thing (Recovery)
Ubuntu Linux Numbers
Same thing (Recovery)
Ubuntu Linux Numbers
Same thing (Recovery)
Mem thingy
Windows OS...

That's what I meant....

---

### Post by Paerez on 2006-07-14
so the "Numbers" are identical too? You can remove the ones you dont use by editing /boot/grub/menu.lst and removing the ones you don't want, **but be careful** not to remove all the ubuntu kernels!!

---

### Post by Amatsu Mikaboshi on 2006-07-14
Yeah it's all identical. I'm not sure what to do...I don't know if I delete one, if the others will get deleted.

---

### Post by Paerez on 2006-07-14
if you post your /boot/grub/menu.lst I will edit it for you.

---

### Post by Amatsu Mikaboshi on 2006-07-15
[quote=My list]# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=/dev/hdb1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
[/quote]

There it is. Thanks, I haven't actually even looked at this, so I'm sure it can't be that hard, right?

---

### Post by Ramses de Norre on 2006-07-15
when you look closely to the numbers you'll see they're not the same, you have 2.6.15-**26**-386, 2.6.15-**25**-386, 2.6.15-**23**-386. So you've got three versions of the linux kernel. If the 2.6.15-**26**-386 works perfect I'd use that, keep one older and delete the other (it's always good to have one older kernel as backup).
To delete the 2.6.15-**25**-386 for instance, type that in the search box in synaptic and delete the linux and restricted modules stuff.

---

### Post by Amatsu Mikaboshi on 2006-07-15
Ha, I'm dumb. So, I can do that, and I can even edit the way they're displayed from reading that. This may be some fun...

Though, why did it do that? I mean, shouldn't it just update itself autimatically to just use the new one as default (as in there is only the "new" kernel listed,) when I haven't done anything to the system besides get all the updates?

---

### Post by Ramses de Norre on 2006-07-15
A new kernel might have problems on some systems, therefore the older one (which was probably working then) is never deleted automaticaly. When the new kernel works perfect you can delete the old one yourself of course.
And be carefull not to change anything but the title line, otherwise your kernels may become unbootable.

---

### Post by Amatsu Mikaboshi on 2006-07-15
Ok, I see that I can edit the time out and all of that stuff, which seems fairly easy...but, how can I make it list the stuff like this...

"Operating Systems"
Most Updated Kernel
(Recovery)
Windows OS

"Other Stuff"
Mem thingy
The Older Kernel
(Recovery)

---

### Post by Ramses de Norre on 2006-07-15
Hmm I wouldn't mess with the file too much.. I think your changes will be undone with every grub-update (performed when a kernel is updated) anyway..
You surely can edit the timeout value etc these will remain, but I'd keep the layout as it is.

---

### Post by Amatsu Mikaboshi on 2006-07-15
Aww....that sucks...

So basically all I do is delete this part from the file and it should be all good right?

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386

---

