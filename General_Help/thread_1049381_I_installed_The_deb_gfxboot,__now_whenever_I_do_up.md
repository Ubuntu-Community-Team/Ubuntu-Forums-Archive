---
title: "I installed The deb gfxboot,  now whenever I do update it says its debian"
date: 2009-01-24
forum: General Help
---

### Post by Lukasz Tarkowski on 2009-01-24
I installed The deb gfxboot, whenever I do sudo grub-update shows its debian but its not its Ubuntu Hardy Heron Gnome!
sudo gedit /boot/grub/menu.lst
Debian GNU/Linux, kernel 2.6.24-23-generic

I would like it to show Ubuntu all the time

---

### Post by fooman on 2009-01-24
run the following in a terminal and post the contents of the file back here, please:

```
gedit /boot/grub/menu.lst
```

---

### Post by Lukasz Tarkowski on 2009-01-24
> gfxmenu /boot/grub/splashimages/StargateSG1AndAtlantis.message
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
color cyan/blue white/blue

#A splash image for the menu


## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro

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
# defoptions=quiet splash vga=794

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro single
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.24-22-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro single
initrd		/boot/initrd.img-2.6.24-22-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.24-19-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro single
initrd		/boot/initrd.img-2.6.24-19-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Here is my content
It keeps on _happening after I do sudo update-grub_

---

### Post by fooman on 2009-01-24
ok,  first thing i would do is limit the amount of kernels that are showing in grub.  easiest way is to install "startup-manager".  it is in the repos, so you could install using synaptic,  or in a terminal,  type or copy/paste the following:

```
sudo apt-get install startupmanager
```after it installs,  open it in system > administration > startup-manager

when it opens,  click the advanced tab,  put a check next to "limit the number of kernels in the boot menu" and set the "number of kernels to keep" to 2.  then close the startup manager app.

next open a terminal and type or copy/paste:

```
gksudo gedit /boot/grub/menu.lst
```when it opens,  scroll down to just under the line that says "## ## End Default Options ##"....there you will see a section that starts with "[COLOR=Red][COLOR=Black]title[/COLOR]        Debian GNU/Linux[/COLOR], kernel 2.6.24-23-generic"

edit that line so it reads "[COLOR=Red][COLOR=Black]title[/COLOR] Ubuntu Hardy 8.04[/COLOR], kernel 2.6.24-23-generic"

repeat in the next three sections below that as well...changing only the parts that say: "[COLOR=Red]Debian GNU/Linux[/COLOR]" to "[COLOR=Red]Ubuntu Hardy 8.04[/COLOR]"....leave the kernel version numbers as they are.

finished product should look like this:

```
## ## End Default Options ##

title        Ubuntu Hardy 8.04, kernel 2.6.24-23-generic
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.24-23-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro quiet splash vga=794
initrd       /boot/initrd.img-2.6.24-23-generic
boot

title        Ubuntu Hardy 8.04, kernel 2.6.24-23-generic (recovery mode)
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.24-23-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro single
initrd       /boot/initrd.img-2.6.24-23-generic
boot

title        Ubuntu Hardy 8.04, kernel 2.6.24-22-generic
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.24-22-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro quiet splash vga=794
initrd       /boot/initrd.img-2.6.24-22-generic
boot

title        Ubuntu Hardy 8.04, kernel 2.6.24-22-generic (recovery mode)
root         (hd0,2)
kernel       /boot/vmlinuz-2.6.24-22-generic root=UUID=1fd5b09d-821b-405a-95b9-0488de1c5f7e ro single
initrd       /boot/initrd.img-2.6.24-22-generic
boot

title        Debian GNU/Linux, kernel memtest86+
root         (hd0,2)
kernel       /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```when you are done,  save and close the file.  reboot and see if thats to your liking.

hope that helps.

---

### Post by Lukasz Tarkowski on 2009-01-24
I did sudo grub-upgrade and it messed up again :(

---

### Post by fooman on 2009-01-24
> **Lukasz Tarkowski said:**
> I did sudo grub-upgrade ...

why?  ...is there a need to run that command??

---

### Post by Lukasz Tarkowski on 2009-01-24
I have solved it,  
I removed menu.lst namely menu. Then I installed grub again :D
Now whenever I run sudo upgrade everything works :D

---

