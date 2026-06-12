---
title: "Can't boot into ubuntu anymore"
date: 2006-10-03
forum: Desktop Environments
---

### Post by hossbert on 2006-10-03
Hello,

I installed ubuntu after installing windows and dual boot was working perfectly with grub. However I was changing some options in the menu.lst file and Windows disappeared from the list. After doing some more messing trying to get it back I ended up with no list but just the grub command prompt after turning on my laptop. I then booted with an old win98 cd and did a fdisk /mbr. Now the laptop boots into windows fine but I cant get into ubuntu!

I have followed the steps at: 
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

which involves running the installer again without formating partitions in an attempt to get to the grub setup stage. However the installer wont let me continue without formating my linux partitions :(

I have also tried the following after booting with the ubuntu cd:
[LIST=1]
[*]Open a terminal
[*]sudo grub
[*]root (hd0,2)
[*]setup (hd0)
[*]quit
[*]reboot
[/LIST]
NOTE: the root partition (/boot is not on a separate partition) is /dev/hda3.

After I did the above I was once again presented with the grub prompt and no list of operating systems.

Finally I have also tried the instructions here:
[http://doc.gwos.org/index.php/DapperGuide#How_to_restore_GRUB_menu_after_Windows_installation](http://doc.gwos.org/index.php/DapperGuide#How_to_restore_GRUB_menu_after_Windows_installation)

This involves booting in rescue mode. I cannot get into rescue mode. I booted with the ubuntu cd, pressed F6 to change the options to 'rescue' and then it starts booting but I get the error:
"Cannot open root device"

I also tried:   rescue root=/dev/hda3 and rescue root=/dev/hda
but I get the same error.

Any help appreciated.

---

### Post by cptnapalm on 2006-10-03
Warning: I am not a Grub Guru!

Boot with the CD.
Open a console and do this:
sudo mount -t ext3 /dev/hda3 /mnt

sudo gedit (or vi, if you prefer) /mnt/boot/grub/menu.lst

find the entry for booting Ubuntu off of the hard drive; a search for Ubuntu should get you there quickly.

read the entries.

if there isn't something like:

title Ubuntu blahblahblah
root (hd0,2)
kernel /boot/vmlinuz  (I'm not remembering what this is off the top of my head)
initrd /boot/initrd.img (Again, same as above note)
savedefault
boot

then add it :)

then:
cd /mnt
sudo chroot /mnt
sudo grub-install /dev/hda

I *think* this will do it.  I don't think things will be any worse than they are right now, at any rate.

---

### Post by cptnapalm on 2006-10-03
There are also these:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/archive/index.php/t-2689.html](http://ubuntuforums.org/archive/index.php/t-2689.html)

---

### Post by hossbert on 2006-10-03
Here's my menu.lst
> 
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
timeout		5

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Also I tried the commands that were suggested:
> 
cd /mnt
sudo chroot /mnt
sudo grub-install /dev/hda
sudo: unable to lookup ubuntu via getbyhostname()



I think that after chrooting the system can no longer
use sudo so I tried it without sudo and got an error relating
to it not being able to find /dev/hda - probably because it's
not really the system in use (since I'm chrooting).

As regards the links you supplied I've tried everything in them with no luck :(

Thanks for the reply. Hopefully I'll find the answer soon.

---

### Post by hossbert on 2006-10-05
I havent found a solution to this problem therefore I'm going to format the root partition and reinstall ubuntu.

---

### Post by viraptor on 2006-10-06
If you're booted into cd, just do sudo bash to stay in root account. Then
mount ..... /mnt
chroot /mnt
grub-install /dev/hda

If it doesn't work - post exact error messages.

---

### Post by hossbert on 2006-10-06
> **viraptor said:**
> If you're booted into cd, just do sudo bash to stay in root account. Then
mount ..... /mnt
chroot /mnt
grub-install /dev/hda

If it doesn't work - post exact error messages.


> grub-install /dev/hda
/dev/hda: Not found or not a block device.

I think this is happening because since I've chrooted the /dev/hda I'm referrening to is not 'real'

---

