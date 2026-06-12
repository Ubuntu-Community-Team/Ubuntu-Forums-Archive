---
title: "[SOLVED] copy file error"
date: 2008-02-24
forum: Desktop Environments
---

### Post by SpaceCowboy41706 on 2008-02-24
Am trying to copy a file to /boot/grub/ and i keep getting an error saying I don't have permission to do that? have tried doing it in the normal desktop and in terminal and I get the same thing both ways? can someone give me a bit of help on how to do this.

---

### Post by lloyd_b on 2008-02-24
> **SpaceCowboy41706 said:**
> Am trying to copy a file to /boot/grub/ and i keep getting an error saying I don't have permission to do that? have tried doing it in the normal desktop and in terminal and I get the same thing both ways? can someone give me a bit of help on how to do this.

In a terminal:
```
sudo cp thefile /boot/grub
```
and when it asks for your password, enter your regular password.

The "sudo" command causes the program to be run with "root" permissions, so that it can access anything on the system.  It's also used to run some programs that are restricted (for security reasons) to root.

Lloyd B.

P.S. - Make sure you are certain of what you are doing.  Messing up grub can easily leave you with an unbootable system!

---

### Post by SpaceCowboy41706 on 2008-02-25
Just to make sure i'm not doing anything wrong. I don't want to be left unbootable...
 Am trying to change the black and white grub screen to something a little neater... and I am following the installation instructions located here:
[http://www.gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907](http://www.gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907)

Installation:

Copy the file (*.xpm.gz) to e.g. /boot/grub/
Then add the following line to your /boot/grub/menu.lst:
splashimage=(hd1,0)/boot/grub/blu.xpm.gz
Change the (hd1,0) if you have a different setup.

How do I find out what my setup is (IE... hd1,0?)

---

### Post by lloyd_b on 2008-02-26
> **SpaceCowboy41706 said:**
> Just to make sure i'm not doing anything wrong. I don't want to be left unbootable...
 Am trying to change the black and white grub screen to something a little neater... and I am following the installation instructions located here:
[http://www.gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907](http://www.gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907)

Installation:

Copy the file (*.xpm.gz) to e.g. /boot/grub/
Then add the following line to your /boot/grub/menu.lst:
splashimage=(hd1,0)/boot/grub/blu.xpm.gz
Change the (hd1,0) if you have a different setup.

How do I find out what my setup is (IE... hd1,0?)

Neither the file copy nor the addition of that line represents any danger.  

As for that "hd1,0":

The number after "hd" is the number of the hard drive, with 0 being the first drive, 1 being the second drive, etc.  The number after the comma is the number of the partition on that drive, again with 0 being the first partition, 1 being the second partition, etc.

So (hd1,0) would be correct if "/boot/grub/..." was on the first partition of the second hard drive.

Note: If my explanation doesn't clear things up, please post a copy of the file "/etc/fstab" - that'll provide the info required to determine what the proper value of "(hd#,#)" should be.

Lloyd B.

---

### Post by SpaceCowboy41706 on 2008-02-26
If I try to get the /etc/fstab from the file browser i get... "Couldn't display /etc/fstab the location is not a folder"

If I try it in terminal I get "Permission denied"

I don't even know if I am doing it right in terminal.. since I have been with Ubuntu for a week now and know very very little. I was just entering /etc/fstab on the command line???

---

### Post by lloyd_b on 2008-02-26
> **SpaceCowboy41706 said:**
> If I try to get the /etc/fstab from the file browser i get... "Couldn't display /etc/fstab the location is not a folder"

If I try it in terminal I get "Permission denied"

I don't even know if I am doing it right in terminal.. since I have been with Ubuntu for a week now and know very very little. I was just entering /etc/fstab on the command line???

"/etc/fstab" is a text file, so you'll need to pull it up in an editor.  From the command line:
```
nano /etc/fstab
```
or
```
gedit /etc/fstab
```
"nano" is an easy to use text-mode editor.  "gedit" is an even easier to use GUI based editor.

Note that unless you put a "sudo" in front of those commands, you will not be able to save changes to the file.  Which is a good thing, as you do *not* want to make any changes to the file in this case...

As an alternative - just run the command "df" in a terminal window, and post that info.  It should have everything that's needed as well (and involves a bit less work - I should have suggested it in the first place).

Lloyd B.

---

### Post by SpaceCowboy41706 on 2008-02-27
purina@purina-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             50957080  24758212  23610396  52% /
varrun                 1037428        88   1037340   1% /var/run
varlock                1037428         0   1037428   0% /var/lock
udev                   1037428       104   1037324   1% /dev
devshm                 1037428         0   1037428   0% /dev/shm
lrm                    1037428     33652   1003776   4% /lib/modules/2.6.22-14-generic/volatile
purina@purina-desktop:~$ 


OR FROM GEDIT...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d555f231-7ecc-42b4-8b88-42cc6615c6f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fa5da4a7-273e-46de-b563-7cebddb9efc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by lloyd_b on 2008-02-27
Okay, the root partition is on "sda2".  Which translates to the first hard drive ("sda", "sdb", etc), and the 2nd partition (in this context, partition numbers start from 1, rather than 0.).

So the correct entry would be
```
splashimage=(hd0,1)/boot/grub/blu.xpm.gz
```
(assuming that the file name is "blu.xpm.gz", of course).

Lloyd B.

---

### Post by SpaceCowboy41706 on 2008-02-27
OK I'm doing something wrong because I am still getting the default black screen... Here is exactly what I'm doing (I took notes in case I messed something up I wanted to be able to tell you what I did):

downloading file to: /home/purina/Grub <---- i just made this folder to keep all my grub images in.

Extracted Orange1.xpm.gz to actual picture file... Orange1.xpm and put it into /home/purina/Grub

Open a terminal and type in: cd /home/purina/Grub

Now type in: sudo cp Orange1.xpm /boot/grub

Now I type in: cd /boot/grub

Now I Type in: ls

And verify that the Orange1.xpm is in fact there and it is.

To open the grub config I typed into the terminal: sudo gedit /boot/grub/menu.lst

at the bottom of the document I type in: splashimage=(hd0,1)/boot/grub/Orange1.xpm

save file, close file, exit terminal, reboot. and I'm still getting the ugly black grub screen.

This is what the "menu.lst" looks like...

++++++++++++++++++++++++++++++++++++++++++++++

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
timeout		30

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
# kopt=root=UUID=d555f231-7ecc-42b4-8b88-42cc6615c6f9 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d555f231-7ecc-42b4-8b88-42cc6615c6f9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d555f231-7ecc-42b4-8b88-42cc6615c6f9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu (memtest86+)
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		P.O.S. Operating System:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microcrap Windoze XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
splashimage=(hd0,1)/boot/grub/Orange1.xpm

---

### Post by lloyd_b on 2008-02-27
Just did a quick test.  With the "splashimage=..." line at the end of the file (as in your "menu.lst"), I got the black & white screen.

However, by moving it to an earlier point in the file, I got the pretty screen.

Try moving that line  to here:
```
# Pretty colours
#color cyan/blue white/blue

**splashimage=(hd0,1)/boot/grub/Orange1.xpm**

## password ['--md5'] passwd

```
and see if that fixes it.

Lloyd B.

---

### Post by SpaceCowboy41706 on 2008-02-28
Worked fantastic. Thanks for all your help !

---

