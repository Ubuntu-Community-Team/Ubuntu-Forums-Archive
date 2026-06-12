---
title: "Error 11: Unrecognizable device string"
date: 2008-12-27
forum: General Help
---

### Post by Enkaybee on 2008-12-27
I recently upgraded to Ibex and have been extremely impressed with it.  I wanted to clear out some of the entries from my boot menu so I ran 

gksu gedit /boot/grub/menu.lst

to bring up the list.  I then put a # sign in front of each of the titles I didn't want to appear on my boot menu.  Then I rebooted.

Upon restarting, I saw only two items on my boot menu: Ubuntu Intrepid Ibex and Windows Vista.  This is exactly what I wanted to see.

However, when I tried to load Ubuntu, I got an error 11 and couldn't get it to load.  The vista partition works just fine.  Can someone tell me what I need to do to get my Ubtuntu partition working again?  I'd really rather not have to reinstall.

Thanks in advance.

---

### Post by Elfy on 2008-12-27
Can you boot the livecd please - run this command 

```
sudo fdisk -l
```

There will be at least 1 entry which is just Linux - not linux/swap - you need to know which is your installed ubuntu partition - it will be referred to as /dev/sdxy - with xy being letter/number combination

Now run these commands - replace sdxy with your / partition number

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp
```

Now run these commands and post the results here please

```
cat /mnt/tmp/boot/grub/menu.lst
blkid
```

---

### Post by lswb on 2008-12-27
Probably easiest is to boot with a live CD, mount your hd read/write, then edit menu.lst back to what it originally was. Post a copy of your menu.lst and we can see what needs to be changed to get the boot menu you want.

---

### Post by Elfy on 2008-12-27
I'm betting it's a uuid problem - had one the other day where menu.lst was

root blahblahblah

instead of

uuid blahblahblah

which is the reason for getting blkid

---

### Post by Enkaybee on 2008-12-27
> **lswb said:**
> Probably easiest is to boot with a live CD, mount your hd read/write, then edit menu.lst back to what it originally was. Post a copy of your menu.lst and we can see what needs to be changed to get the boot menu you want.

I thought I'd try this first since it seemed easier.  I booted from the CD, and now I'm looking at my menu.lst.  I changed everything back to the way it was, but I can't save it because I don't have permission.  Is there any way to get around this?

---

### Post by lswb on 2008-12-27
> **Enkaybee said:**
> I thought I'd try this first since it seemed easier.  I booted from the CD, and now I'm looking at my menu.lst.  I changed everything back to the way it was, but I can't save it because I don't have permission.  Is there any way to get around this?

In a terminal use this command:

```

sudo mount -o remount -o rw /dev/sda2

```

Substitute the correct device name for /dev/sda2, or you can use the mountpoint instead. Also you still need to edit it as root, so use "gksudo gedit" or "sudo vi" or whatever is appropriate for the editor you like.

The ubuntu live CDs by default mount the hard drive as read-only so that no accidental changes can be made. This command will remount the drive as read-write so you can save your changes. See "man mount" for more info.

---

### Post by Enkaybee on 2008-12-27
Here's my menu.lst (with everything changed back to the way it was.  The smileys are 8's in parenthesis):

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
timeout		5000

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
# kopt=root=UUID=91f2408c-7f5c-499e-bb3c-39981ad61ebf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10: Intrepid Ibex
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=91f2408c-7f5c-499e-bb3c-39981ad61ebf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=91f2408c-7f5c-499e-bb3c-39981ad61ebf ro  single

initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=91f2408c-7f5c-499e-bb3c-39981ad61ebf ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=91f2408c-7f5c-499e-bb3c-39981ad61ebf ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1




Iswb, can you tell me exactly what command I would need to enter so that I can save changes to menu.lst?  I don't know the Ubuntu file system as well as I should.

---

### Post by Enkaybee on 2008-12-27
Never mind.  Got it.  Thanks!

All I had to do was enter 

gksudo gedit

then open menu.lst in the window that pops up.  Then I made my changes and it let me save.

And for anyone still interested in cleaning up the boot menu, you have to put 2 # signs before each title to make it disappear.

---

