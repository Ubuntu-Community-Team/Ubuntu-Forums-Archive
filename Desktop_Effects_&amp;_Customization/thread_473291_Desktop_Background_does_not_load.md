---
title: "Desktop Background does not load"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by lsutiger on 2007-06-13
My desktop background does not show up when I boot up. Its shows up immediately when I open system-->prefrences-->desktop background.
any ideas?
Also, how do I setup a splash screen? It was on the system-->preferences menu when I had edgy.

---

### Post by satx on 2007-06-14
On the Splash Screen issue:
You must be logged in as root (sudo)
Go to terminal. Type sudo -s; type password.
then type 
cd /boot/grub
gedit menu.lst (this is an L not a 1)

Now you can edit the bootup menu entries/look. 
Here's mine (My changes in RED) Note on the splash image location must be in /boot/grub directory, and the partion must be your partition- in my case hd0(1):


**** START MENU.LST ******

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
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

[COLOR="Red"]# Splash screen
splashimage=(hd0,1)/boot/grub/u6.xpm.gz[/COLOR]

# Pretty colours
[COLOR="Red"]foreground 663333
background FFFF99
shade 0
viewport 7 0 76 16 [/COLOR]
# color cyan/blue white/blue

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
# kopt=root=UUID=601a0bbc-6987-4832-9dea-33660b4abbb1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=601a0bbc-6987-4832-9dea-33660b4abbb1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=601a0bbc-6987-4832-9dea-33660b4abbb1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Red"]title		Other Crappy Operating Syste[/COLOR]ms:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[COLOR="Red"]title		MS WIN XP PRO SP2[/COLOR]
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
[COLOR="Red"]title		WIN XP RECOVERY PARTITION[/COLOR]
root		(hd0,2)
savedefault
makeactive
chainloader	+1


*****END OF MENU.LST ***** 

Note that image must be in xpm.gz format
Cannot have more than 14 colors
You can download beaucoups splash screens, edit in GIMP.

---

### Post by lsutiger on 2007-06-15
Thats odd. All I had to do before was go to System--> Preferences--> Splash Screen and choose an image...How can I get that function back?
PS - Before, I was running Edgy.

---

### Post by andrewsomething on 2007-06-15
No help on the background problem. Sorry...

You can get a splash screen manager (which will install to System>Preferences>Splash Screen) by searching for "gnome-splashscreen-manager" in Synaptic.

---

### Post by Hater385 on 2007-06-16
About your backgroud, are you sure your backgroud is not on a unmounted drive? that happened to me, i had my wallpapers on my ntfs drive.

---

### Post by lsutiger on 2007-06-16
Nah, it's in my home folder.

---

### Post by lsutiger on 2007-06-16
Thanx! The splashscreen works!
Still dumbfounded about the background though.

---

### Post by satx on 2007-06-28
lsutiger:

Key is in the location of the image: I put mine in /boot/grub. Also note specifying partition- I have a dual boot system, XP and UBUNTU. In the script I sent you note: 
splashimage=(hd0,1)/boot/grub/u6.xpm.gz

Note the file format must be xpm, zipping makes it work better. No more than a 14 color pallette! Max size 640x480

Hope this helps. SATX

---

### Post by lsutiger on 2007-06-30
> **satx said:**
> lsutiger:

Key is in the location of the image: I put mine in /boot/grub. Also note specifying partition- I have a dual boot system, XP and UBUNTU. In the script I sent you note: 
splashimage=(hd0,1)/boot/grub/u6.xpm.gz

Note the file format must be xpm, zipping makes it work better. No more than a 14 color pallette! Max size 640x480

Hope this helps. SATX

Thanx for the reply! I have since reinstalled because I jacked up my wireless fooling around...hehe, Thank God I backup!

---

