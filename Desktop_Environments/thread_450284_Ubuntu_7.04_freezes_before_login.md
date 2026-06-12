---
title: "Ubuntu 7.04 freezes before login"
date: 2007-05-21
forum: Desktop Environments
---

### Post by bjornhakon on 2007-05-21
I run Ubuntu 7.04 with Gnome. Yesterday, I did a couple of things at the same time:

I changed the loginscreen to one of the other choices (similar to the default, but blue)
I activated automatic login and timed login = 30 sec. ( I wanted the given user to be logged in automatically after a 30 sec. delay)

After a reboot, I'm unable to log in. The screen is black and the machine hangs before the loginscreen even shows up. What can be wrong? How can I fix this? 
If the problem is the newly chosen loginscreen, then I can live very happily with the default one - if I only can bring it up.
I am able to log in as root from the second choice in Grub (Ubuntu 7.04 Recovery mode), but I only get the Command Line Interface. I don't know how to start Gnome or Gedit from there. However, I'm sure there is a way to fix this from here, but I have no clue about how to do it.
Any tips?

---

### Post by siteguru on 2007-05-21
Can you login selecting the recovery mode? (I presume you do see the grub menu?)

If you can then edit the menu.lst file to remove the word **splash** from the kernel line.

No guarantees that this will work, but I had a similar sounding issue with Feisty 7.04 64-bit version and this cured the problem for me. (See post linked below).

[http://ubuntuforums.org/showthread.php?t=449412](http://ubuntuforums.org/showthread.php?t=449412)

---

### Post by bjornhakon on 2007-05-21
Yes, I can log in using recovery mode.
I will try your suggestion when I get home from work (it's now 2:30 PM here in Norway).
Thanks so far.

---

### Post by bjornhakon on 2007-05-21
The word **splash** doesn't exist in my menu.lst.
I would need some CLI command to get the default loginscreen (where I enter username and password) back. Or, there might be a problem with the settings I changed?

---

### Post by siteguru on 2007-05-21
gksudo gedit /boot/grub/menu.lst

What does that show? Probably need to see what's actually in the grub menu. Not saying I can help, but someone else here may have a better idea.

---

### Post by bjornhakon on 2007-05-22
This is my /boot/grub/menu.lst :
> 
# menu.lst - See: grub, info grub, update-grub
#            grub-install, grub-floppy,
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
default		saved

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
# kopt=root=UUID=41407db4-a86e-41ba-b02b-31c632b80156 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
# defoptions=quiet splash locale=nb_NO

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41407db4-a86e-41ba-b02b-31c632b80156 ro quiet locale=nb_NO
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault=4

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41407db4-a86e-41ba-b02b-31c632b80156 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault=1

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault=0
makeactive
chainloader	+1



I don't really think the problem is in here, because everything worked nicely until I changed the loginscreen ( I don't remember the name, but I think it was the first choice. Anyway, it is blue and very similar to the default, orange one ), and at the same time activated automatic login and timed login. Everything was done through the Ubuntu menus. What I really need is a CLI command (or several) to restore these settings to the values that come with the Ubuntu CD. In other words, standard settings.
I can log in using recovery mode, and I can edit text-files with nano.

Anyone have a clue?

---

### Post by bjornhakon on 2007-05-22
Just to make it clear - it is the loginscreen itself that doesn't show. When the time comes to enter username and password, instead of showing the login screen, the screen is black and the mouse pointer is a circle that goes round and round forever.

---

### Post by siteguru on 2007-05-22
Ah. That's slightly different to my problem. Mine was that I didn't even see the timer (Ubuntu's equivalent to the MS hourglass) and the monitor went off as though there was no graphics signal. Removing **splash** allowed the login screen to show.

Sorry - can't help any further - please see my sig! :lol:

---

### Post by bigdoby on 2007-05-22
i have exactly the same issue... 
but i can log in correctly if i restart X (CTRL+ALT+BACKSP).
the second time gdm load nautilus and everything else..
if someone knows how to handle this annoying problem is welcome ;)

---

### Post by bjornhakon on 2007-05-22
I got it fixed!

The commands

Pressing ALT+F2 and then entering the commands

sudo /etc/init.d/gdm stop
startx

did the trick, but in order to access Administration -> Login screen, I had to start gdm. Then I was able to make the changes needed. Now the system is back in business again.

Actually, I pressed ALT+CTRL+F2, and that opened tty2. I entered all the commands from here, and the black screen with the spinning mouse-pointer was back. Pressing ALT+CTRL+F7 brought me back to the x session, and now when gdm was started, I could change anything I liked. BUT ... With every change I made, the "bad-screen" came back. I figured that I was thrown back to tty2, so I just pressed ALT+CTRL+F7 and could continue to change settings. After a restart, everything was normal.

Bjorn Hakon

---

