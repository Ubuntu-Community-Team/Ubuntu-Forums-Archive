---
title: "advanced grub configuration"
date: 2009-01-27
forum: General Help
---

### Post by sailingboarder on 2009-01-27
So I have a dual boot set up on my new desktop. I use Windows for a couple of games either from steam or that failed to work under wine, and ubuntu for everything else. Since I usually just leave the system running, the only time I ever restart is to change operating systems. 
Grub was configured to default to ubuntu, but I want to change that. Specifically, I want the system to boot the the os that I was NOT previously using. basically, the opposite of the savedefault command. 
I think this is possible using ```
savedefault X
``` where X is the number of the other entry to boot from, so use the number for windows under the ubuntu listing and vice versa
this is my menu.lst, but it still defaults to ubuntu, so the numbering must be wrong or my plan just doesn't work
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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	3	

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
# kopt=root=UUID=e2f87944-02e1-48f4-bc5a-e00535a828ae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de4797c6-7136-4d91-bca0-19dd79e7cee7

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		de4797c6-7136-4d91-bca0-19dd79e7cee7
kernel		/vmlinuz-2.6.27-9-generic root=UUID=e2f87944-02e1-48f4-bc5a-e00535a828ae ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet
savedefault	7

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		de4797c6-7136-4d91-bca0-19dd79e7cee7
kernel		/vmlinuz-2.6.27-9-generic root=UUID=e2f87944-02e1-48f4-bc5a-e00535a828ae ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		de4797c6-7136-4d91-bca0-19dd79e7cee7
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e2f87944-02e1-48f4-bc5a-e00535a828ae ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		de4797c6-7136-4d91-bca0-19dd79e7cee7
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e2f87944-02e1-48f4-bc5a-e00535a828ae ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		de4797c6-7136-4d91-bca0-19dd79e7cee7
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1
savedefault	0

```
any thoughts?

---

### Post by dcstar on 2009-01-27
> **sailingboarder said:**
> So I have a dual boot set up on my new desktop. I use Windows for a couple of games either from steam or that failed to work under wine, and ubuntu for everything else. Since I usually just leave the system running, the only time I ever restart is to change operating systems. 
Grub was configured to default to ubuntu, but I want to change that. Specifically, I want the system to boot the the os that I was NOT previously using. basically, the opposite of the savedefault command. 
I think this is possible using ```
savedefault X
``` where X is the number of the other entry to boot from, so use the number for windows under the ubuntu listing and vice versa
this is my menu.lst, but it still defaults to ubuntu, so the numbering must be wrong or my plan just doesn't work
```

........
savedefault**	0**

```
any thoughts?

Get rid of the useless numbers and the "savedefault" option will work.

---

### Post by sailingboarder on 2009-01-28
the savedefault will reboot to the os that I was previously using. I want it to boot to the os NOT saved when using savedefault

---

### Post by Dies on 2009-01-28
You could try using grub-set-default

[http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dset_002ddefault](http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dset_002ddefault)

---

### Post by sailingboarder on 2009-01-28
well, grub-set-default would have to be run every time I want to restart, as it is a one time change
I want to change the settings so that when ubuntu starts up, it sets the default to windows, and when windows starts up it sets the default to ubuntu

i'm looking at fallback now, maybe have windows default, with fallback to ubuntu, then i could use grub-set-default to reset windows as default from rc.local
does this sound any better than the savedefault X?
[http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems]("http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems")

---

### Post by Dies on 2009-01-29
> **sailingboarder said:**
> well, grub-set-default would have to be run every time I want to restart, as it is a one time change


Not an issue. Just add the command in a script in 

/etc/rc6.d/

Sorry, I originally had that in my post but edited it out... not sure why now? :D


I would just have Ubuntu as the default then when you reboot the script runs and Windows boots, the next time you reboot it defaults back to Ubuntu... or at least I *think* that's how it would work.

---

