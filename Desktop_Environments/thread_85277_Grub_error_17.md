---
title: "Grub error 17"
date: 2005-11-02
forum: Desktop Environments
---

### Post by otey on 2005-11-02
Hi. after a kubuntu install, my grub displays "error 17" on startup. 

The kubuntu installation is made on my slave harddisk, but copied some stuff to the boot secter of my master harddisk.

But what am i to do now. None of the harddisks are bootable. 
Master:
hdc1 (ubuntu) (ext2)
Slave:
hdd1 (Windows xp) (vfat)
hdd3 (kubuntu) (ext2)

---

### Post by beefsprocket on 2005-11-02
I take it that you've tried booting each disc from the motherboard then? I'd suggest using a livecd like Ubuntu, kanotix, or knoppix to boot your computer and then edit and reinstall grub on your disc(s). Disable your hdc through your bios if you want to install grub on hdd and vice versa. Then you can edit or add entries to your menu.lst pointing to your other installations.

For the windows disc, try running console recovery and typing (with your other drive disabled for now) fixboot and fixmbr.

---

### Post by otey on 2005-11-02
I have tried to edit the "menu.lst" just to get it top boot

it now looks like this:

(mnt/hdc1/boot/grub/menu.lst)

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

# title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
# root		(hd0,0)
# kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro single
# initrd		/boot/initrd.img-2.6.12-9-386
# savedefault
# boot

# title		Ubuntu, memtest86+
# root		(hd0,0)
# kernel		/boot/memtest86+.bin  
# boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
# title		Microsoft Windows XP Professional
# root		(hd1,0)
# savedefault
# makeactive
# map		(hd0) (hd1)
# map		(hd1) (hd0)
# chainloader	+1
```

shuldnt it be working now?

You said something about reinstalling grub? How do i do that?

thanks for helping, by the way!

---

### Post by beefsprocket on 2005-11-02
You can reinstall grub by running either grub-install or running grub. I've only ever used grub on its own so I can only give you half the options available to you. Regardless...

If you can't boot windows directly from the hard drive, you want to uncomment the final 7 lines of your grub.conf. That entry will allow grub to call upon windows and let windows boot itself. Note that you'll also want to run the aforementioned fixboot and fixmbr commands on your /dev/hdd1 drive (is windows on your secondary slave? I can think of no better place than that!).

Once those two steps are completed (in the order of your choosing, though I'd suggest the windows fix first in order to reduce your rebooting), fire up your live cd of choice and, from a root terminal, run grub.

Once in grub, type:
```
root (hd0,0)
setup (hd0)
quit

``` 
This sets grub up in the master boot record of your primary (hd0) hard drive. To get an idea of how the numbering scheme works, (hd0,1) would likely be your swap partition, as it is the second partition (the ,1 part) on your primary disc (which is hd0). hd1,0 would be your windows disc. 

Once you reboot and reenable all your hard drives, what happens? If you still get error 17 and are up for it, try reinstalling with a 128mb boot partition. You can create one in the installer when the partition section comes up. On my old 40gb drive, my motherboard doesn't like it having partitions cross the 1024 cylinder boundary (whatever that is... some archaic limitation that came about when discs broke the 2gb barrier I'm sure). Having the small boot partition before the boundary allows linux to see my full disc and properly boot.

Though it details lilo, this page might shed some insight into the problem:
[http://howtos.linux.com/howtos/Large-Disk-HOWTO-5.shtml]("http://howtos.linux.com/howtos/Large-Disk-HOWTO-5.shtml")
>  This problem (if it is a problem) is very easily solved: make sure that the kernel (and perhaps other files used during bootup, such as LILO map files) are located on a partition that is entirely contained in the first 1024 cylinders of a disk that the BIOS can access - probably this means the first or second disk. 
 

---

### Post by otey on 2005-11-07
I got mad.. formattet it all again.. now i'm running kubuntu on the master and ubuntu on the slave.. no xp yet..

---

### Post by shinygerbil on 2005-11-07
Beware, if you try to install XP on to that, it'll overwrite your boot record...

Steve

---

### Post by otey on 2005-11-07
Can i avoid that if I remove my master harddisk while i install?

Or could you point me to a good xp-emulator so i wont have to try.. can't live without my dear tsw webcoder 5

---

