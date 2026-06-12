---
title: "Intrepid - Splashimage does not show"
date: 2009-02-24
forum: General Help
---

### Post by Aralhach on 2009-02-24
Hey everyone.  I recently tried to install a splashimage to the grub.  I put the image in the /boot/grub/images folder, and told it to load that splashimage (the nightship one).  I also put sudo update-grub and it said that it found the splashimage, but the grub menu ALWAYS shows the text and NEVER shows the image.  I tried to use the grub prompt, and still, nothing.

My menu.lst file follows:
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage=(hd0,1)/boot/grub/images/nightship.xpm.gz
foreground 87ceeb
background 0000ff

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
# kopt=root=UUID=7157fd92-0fe1-416e-be2f-5908b865e95d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7157fd92-0fe1-416e-be2f-5908b865e95d

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
# howmany=1

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
uuid		7157fd92-0fe1-416e-be2f-5908b865e95d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7157fd92-0fe1-416e-be2f-5908b865e95d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7157fd92-0fe1-416e-be2f-5908b865e95d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7157fd92-0fe1-416e-be2f-5908b865e95d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		7157fd92-0fe1-416e-be2f-5908b865e95d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'd appreciate the help!

---

### Post by ibuclaw on 2009-02-24
My guess would be extract the xpm image from the gzip it is in
```
cd /boot/grub/images
sudo gunzip nightship.xpm.gz
```
and edit the bootmenu to show this:
```
splashimage=(hd0,1)/boot/grub/images/nightship.xpm
```

Regards
Iain

---

### Post by Aralhach on 2009-02-24
Thanks for your idea!  I tried it and unfortunately it didn't work :'(

Any other ideas? ;)

---

### Post by deepclutch on 2009-02-24
you try this:
```
 sudo apt-get install grub-splashimages
```
now press ALT+F2 for run dialog,inside you type below text to open gedit with sudo rights:
```
gksudo gedit /boot/grub/menu.lst
```
search the splashimage portion and edit as below(Assuming ,you don't have seperate /boot partition-harddisk partition):
```
splashimage=/boot/grub/splashimages/menu-sta.xpm.gz
```
OR anyother splashimage available in /boot/grub/splashimages directory.
Good Luck :)

PS:it is always a good idea to mention your harddisk partition number where you have GNU/Linux installed.with uuid system ,we cannot find the partition number :p

---

### Post by Kevbert on 2009-02-24
Another way of doing this is to use startup-manager and let it do this for you. You can install this via Synaptic Package Manager. You don't even need to unzip the file. If you try this method, let us know how you get on.

---

### Post by Aralhach on 2009-02-24
> **deepclutch said:**
> you try this:
```
 sudo apt-get install grub-splashimages
```
now press ALT+F2 for run dialog,inside you type below text to open gedit with sudo rights:
```
gksudo gedit /boot/grub/menu.lst
```
search the splashimage portion and edit as below(Assuming ,you don't have seperate /boot partition-harddisk partition):
```
splashimage=/boot/grub/splashimages/menu-sta.xpm.gz
```
OR anyother splashimage available in /boot/grub/splashimages directory.
Good Luck :)

PS:it is always a good idea to mention your harddisk partition number where you have GNU/Linux installed.with uuid system ,we cannot find the partition number :p

This answer was the one that did it (I tried this first and it worked, I didn't get around to try the other one, although I will to see what features it has).  I knew that Ubuntu was installed on (hd0,1) so that was fine (and update-grub found the same image).

Why did I have to install that package for the splashimage to work?

Thanks for your time and answers!

---

### Post by deepclutch on 2009-02-24
>  Why did I have to install that package for the splashimage to work?
well ,it bundles few splashimages.I don't intend to make one myself.so this helped me :p .you can always make your own splashimage though.

---

