---
title: "Windows xp, Ubuntu 5.10 Problems"
date: 2006-01-06
forum: General Help
---

### Post by h4ck3r on 2006-01-06
Ok, I have a small 5 gb ide harddrive and a 200 gb sata harddrive. I installed windows on the 5 gb and then installed linux on the 200gb. I ran across some problems though if you go into grub it gives you an error 17 on the linux distro (that is if you just hit enter on it.) and windows gives me an error 13, but if I have the windows install disk in the cd drive but don't hit boot off of the cd drive and just let grub load up. Because the cd is in the drive I am able to boot into windows and linux just fine no problems. Does anyone have any idea why the windows cd has anything to do with being able to boot into either distro. Also, does anyone have any ideas on how to fix it.

Thanks
Ben
:KS

---

### Post by docmanny on 2006-01-06
Please post /boot/grub/menu.lst

You are able to get into the boot menu, right?

---

### Post by h4ck3r on 2006-01-06
Ok, here it is and yes I am able to get into the boot loader letting me select which operating system.

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by dragonfyre13 on 2006-01-06
Something you may want to try, I know that many times, Windows Broks Grub unless it is on hda, so if you mount a  ~15mb partition as "/boot" it should rule that out.

---

### Post by docmanny on 2006-01-06
If you can get into the grub menu, you may want to try switching hd0 and hd1. 

Try typing an e at the boot menu and edit just that line and see if it works. I have a similar situation on my computer and I'll compare my grub.lst when I get home.

---

### Post by h4ck3r on 2006-01-06
How can I make the 15 mb partition?

---

### Post by h4ck3r on 2006-01-06
*I deleted it*

---

### Post by h4ck3r on 2006-01-06
[QUOTE=docmanny]If you can get into the grub menu, you may want to try switching hd0 and hd1. 

Try typing an e at the boot menu and edit just that line and see if it works. I have a similar situation on my computer and I'll compare my grub.lst when I get home.[/QUOTE]

If I have the windows cd in I can get into any disto installed. So getting in isn't the problem making it not rely on the windows cd being in the drive is the problem.

---

### Post by h4ck3r on 2006-01-06
Woot, I have linux booting up fine but windows still doesn't work. (it still needs the cd)
What I did was I changed linux from hd1,0 to hd0,0 in the menu.lst file. (I changed it for all 3 of the ubuntu ones. When I tryed changing the windows to hd1,0 though, it gave me this super wierd error that didn't make sense (It was lots of wierd symbols.)
So 1 down and 1 to go :cool: :cool: thanks guys for the help please keep it coming ;) .

---

### Post by docmanny on 2006-01-06
Windows won't boot unless it thinks its on the first hard drive.
So you have to add

map (hd0) (hd1)
map (hd1) (hd0)

Put this in before the root line in the Windows section. THis is from memory, if it doesn't work, I'll post by menu.lst when I get home...

---

### Post by h4ck3r on 2006-01-06
Thank you so much it worked and I am dancing for joy :) :). :KS :KS :KS :KS :KS for you.

---

