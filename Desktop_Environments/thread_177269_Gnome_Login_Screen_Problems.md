---
title: "Gnome Login Screen Problems"
date: 2006-05-16
forum: Desktop Environments
---

### Post by phenolholic on 2006-05-16
Hello, I'm trying to login into my setup. I get the GUI login, submit my login/passwd, and see a text terminal login flash for a second then goes right back to GUI login. I'm using 6.06 beta.
Thanks in advance

---

### Post by codejunkie on 2006-05-16
[quote=phenolholic]Hello, I'm trying to login into my setup. I get the GUI login, submit my login/passwd, and see a text terminal login flash for a second then goes right back to GUI login. I'm using 6.06 beta.
Thanks in advance[/quote]
could you login before, or has it been doing this since you installed ubuntu?

---

### Post by phenolholic on 2006-05-17
[QUOTE=codejunkie]could you login before, or has it been doing this since you installed ubuntu?[/QUOTE]

this was a fresh install, and i updated it as soon as i installed it. after the restart, it wouldnt let me log in

---

### Post by codejunkie on 2006-05-17
[quote=phenolholic]this was a fresh install, and i updated it as soon as i installed it. after the restart, it wouldnt let me log in[/quote] 
Here's several things you can try that might help fix your problem

[B]NOTE: LINUX IS CASE SENSITIVE SO WHEN ENTERING 
THESE COMMANDS IF YOU GET MESSAGES LIKE[/B] *bash: command: command not found* **CHECK THAT THEY HAVE BEEN ENTERED IN THE CORRECT SYNTAX.**

** 1**: Try using the failsafe gnome session click on sessions then Failsafe GNOME and try logging in 
if everything is cool press alt+F2 and enter ```
gnome-session-save
``` this should save this session and you should be alright the next time you login. 

** 2**: if you installed any video card drivers or made any changes to the /etc/X11/xorg.conf file, some nvidia cards suffered from a bug where they would freeze or get a black screen at the login prompt using certian drivers, if so try changing the video card driver back. 

** 3**: you can also try creating a new user account, incase your's got messed up. press ctrl+alt+F1 and when you get to the console login and run 
```
sudo adduser newusername
```replace newusername with what ever you want to call your new account fill in the new user info, then run ```
sudo /etc/init.d/gdm restart
```to restart the loginmanager an try logging in under your new user account.

**<<[COLOR=Red]WARNING!![/COLOR] YOU MUST ENTER THESE COMMANDS IN ORDER OR IT WILL REMOVE IMPORTANT FILES AND MAY BREAK YOUR SYSTEM>> **
** 4**: i've had upgrades go bad on me sometimes, and it helped by clearing the temp files that can be done by doing this in order press ctrl+alt+F1 login then run
1: ```
sudo su
``` 2: ```
cd /tmp
``` 3: ```
rm -R *
``` 4: ```
rm -R .*
``` the reboot by entering ```
reboot
``` when it boots back up try logging back in.

** 5**: make sure there were no package errors with apt-get/dpkg/synaptic during the upgrade press ctrl+alt+F1 and login to when you reach the terminal enter ```
sudo apt-get update
``` 
```
sudo apt-get dist-upgrade
```if you recieved errors usually entering ```
sudo apt-get -f install
``` then ```
dpkg --configure -a
``` will fix the broken packages.
if it doesn't you'll need to post the exact error messages here.

** 6**: if you installed ubuntu on a small harddrive partition say 2 gigs or less, this can happen if your out of diskspace press ctrl+alt+F1 to get to the terminal login then run ```
sudo apt-get clean
```this will clean out the apt cache which over time can grow to be over 1gig depending on what you have installed.

** 7**: sorry for the long post but i tried to list everything i know of that could cause this  problem in hopes one of these will fix it.

codejunkie,

---

### Post by phenolholic on 2006-05-18
wow. you own man! thanks a bunch! i'm having another problem. i initially had ubuntu and xp, with GRUB defaulting to ubuntu, but then i installed red hat on a partition and it also installed GRUB (a nicer GUI one might i add), and its recognizing xp and allowing me to boot into it, but i can't add ubuntu in GRUB for the life of me. any ideas? thanks again

---

### Post by phenolholic on 2006-05-18
oh by the way, ubuntu is on /dev/hda3 and i have the following command on GRUB for ubuntu:

root (hd0,2)
chainloader +1

and i get the following message:
Error 13: Invalid or unsupported executable format

XP boots fine, so does redhat, but i cant get into ubuntu at all. by the way, i only have redhat for a 64bit computational chemistry application thats specifically made for redhat. otherwise, i wouldnt bother.

---

### Post by codejunkie on 2006-05-18
[quote=phenolholic]oh by the way, ubuntu is on /dev/hda3 and i have the following command on GRUB for ubuntu:

root (hd0,2)
chainloader +1

and i get the following message:
Error 13: Invalid or unsupported executable format

XP boots fine, so does redhat, but i cant get into ubuntu at all. by the way, i only have redhat for a 64bit computational chemistry application thats specifically made for redhat. otherwise, i wouldnt bother.[/quote] 
boot into redhat open a terminal and enter ```
su -
```enter the root password and mount the ubuntu harddisk it should go something like this
```
mkdir /ubuntu
``` ```
mount /dev/hda3 /ubuntu
```open nautilus and navigate to **/ubuntu/boot/grub** and open the menu.lst file find your ubuntu entries, they should look something like mine in the blue 

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

[COLOR=Blue]title        Ubuntu, kernel 2.6.15-22-386
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.15-22-386 root=/dev/hdb2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-22-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.15-22-386 root=/dev/hdb2 ro single
initrd        /boot/initrd.img-2.6.15-22-386
boot
[/COLOR]
title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

``` now open a root terminal with ```
su -
``` and run 
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.saved
``` then enter```
gedit /boot/grub/menu.lst
``` copy and paste your ubuntu entries into the bottom of this file save it and reboot and your ubuntu entries should show up in the grub menu.
hope this helps codejunke,

---

