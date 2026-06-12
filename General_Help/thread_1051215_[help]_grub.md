---
title: "[help] grub"
date: 2009-01-26
forum: General Help
---

### Post by ren_mot on 2009-01-26
when i turn on my computer it loads the grub 
directly into the bash shell commands 

it doesn't show my os but i can still
start them by typing

root (hdx,x)
kernel /boot/vmlinuz...
initrd

its a real pain to have to type that everytime i 
want to start the os

i have the menu.lst file on /boot/grub
i've tried 
going to the konsole
and typing
sudo grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0)

this happened when i changed the menu.lst file so it 
would only show the most recent versions of the kernel on the 
grub boot screen, but i had a backup file and i already changed it back to the way it was and it still not showing me anything

anyone has any idea of whats going on????

---

### Post by stchman on 2009-01-26
> **ren_mot said:**
> when i turn on my computer it loads the grub 
directly into the bash shell commands 

it doesn't show my os but i can still
start them by typing

root (hdx,x)
kernel /boot/vmlinuz...
initrd

its a real pain to have to type that everytime i 
want to start the os

i have the menu.lst file on /boot/grub
i've tried 
going to the konsole
and typing
sudo grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0)

this happened when i changed the menu.lst file so it 
would only show the most recent versions of the kernel on the 
grub boot screen, but i had a backup file and i already changed it back to the way it was and it still not showing me anything

anyone has any idea of whats going on????

Editing GRUB can be tricky for the n00b.  I recommend using StartUpManager.

```

sudo apt-get install startupmanager

```

This GUI program will allow you to tailor GRUB much more safely.

---

### Post by caljohnsmith on 2009-01-26
What is the contents of your /boot/grub/menu.lst? Does that file even exist?

---

### Post by ren_mot on 2009-01-26
> **caljohnsmith said:**
> What is the contents of your /boot/grub/menu.lst? Does that file even exist?

yeah 
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
# kopt=root=UUID=40cf83a7-9f10-427d-9a32-624a72ce12d7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40cf83a7-9f10-427d-9a32-624a72ce12d7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=40cf83a7-9f10-427d-9a32-624a72ce12d7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		BackTrack (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=current ro append = "resume=/dev/hda5 splash=silent vga = 769 
savedefault
boot


```

but now i've messed it up even more i get 
error 18 message 
im only able to boot with the live cd now 
and even if i succesfully reinstall kubuntu
im still getting this error 18 message 
=/

---

### Post by caljohnsmith on 2009-01-26
OK, how about reinstalling, but first open up the partition editor (System > Admin > Partition Editor) and use that to create a ~200 MB ext3 partition at the very beginning of your HDD. You can also use the partition editor to set up your main Ubuntu partition and swap partition if you want. Then when you go through the installer again, set the mount point on the 200 MB partition as "/boot". After you are done reinstalling and reboot, let us know what happens.

---

### Post by malfist on 2009-01-26
Try using the SuperGrub CD

---

