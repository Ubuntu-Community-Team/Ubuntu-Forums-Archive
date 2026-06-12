---
title: "Dual boot xp problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by cody50 on 2006-07-20
I recently used the ubuntu live cd to install it on my hard drive. i did the option where it resized my windows partition and used the free space.

ubuntu works fine. but when i try to boot into windows, i get this 

root(nd0,0)
filesystem type unknown,partition type 0x7
saved default
make active
chainloader +1

and then it is there, and nothing else happens. 
if someone could help me, even if it is to tell me that i accidently fragged windows and all my old files and that i have to move on in my life, it would be appreciated.

---

### Post by Paerez on 2006-07-20
you didn't frag it, it is just having trouble getting going. Can you post your "/boot/grub/menu.lst" file?

---

### Post by cody50 on 2006-07-20
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
# kopt=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Paerez on 2006-07-20
ok type:
```
sudo fdisk /dev/hda
```
then press P and Enter to display the partitions, then Q and enter to quit. Then paste me the output from the P. Don't press any other keys, if you accidentally do, press CTRL+C to quit immediately.

---

### Post by cody50 on 2006-07-20
cody@cody-desktop:~$ sudo fdisk /dev/hda
Password:
Sorry, try again.
Password:

The number of cylinders for this disk is set to 9964.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3968    31872928+   7  HPFS/NTFS
/dev/hda2            3969        9782    46700955   83  Linux
/dev/hda3            9783        9964     1461915    5  Extended
/dev/hda5            9783        9964     1461883+  82  Linux swap / Solaris

---

### Post by Paerez on 2006-07-20
OK so it looks like:
1) You have a big drive :D
2) The cyclinder number is weird, and as it says, it may cause problems with booting. But since you have a nice new version of grub, and I haven't heard of this before, I don't think thats the problem.

Sadly, I have no idea what the problem is, but now we have some more information and hopefully someone else (or google) can help.

---

### Post by cody50 on 2006-07-20
well thank you for your time!

---

### Post by cody50 on 2006-07-21
A friend told me to try the windows recovery console and use the commands fixboot and fixmbr. I have never done this before. before I try it, does anyone have any advice, tips, ideas if it will work? what would those commands do?

---

### Post by Paerez on 2006-07-21
That will remove GRUB (ubuntu's bootloader) from the master boot record (mbr) of the drive. Basically it will give windows control of the booting, and windows will pick windows to boot. So it will no longer let you boot linux unless you edit window's boot settings.

It will definitely work, and you can restore GRUB later, without any loss of data on linux or windows.

You will be unable to boot linux, but linux is still there, and you can switch back later.

fixmb and fixboot are generally used as last ditch efforts to put windows back.

---

### Post by cody50 on 2006-07-21
If I lose data on linux that isnt too bad, since I don't really have anything on there as of yet, so once i try the fixboot or fixmbr (which one should i use?) i'll pobobly be back here to redo GRUB. thanks.

---

### Post by Paerez on 2006-07-21
**fixmbr** will be all you need. That will allow windows to do the booting. fixboot fixes window's boot file (analogous to /boot/grub/menu.lst) and should be used if windows can't boot itself.

---

### Post by cody50 on 2006-07-22
I went to use the recovery console, but there is an issue with the password. i never remember putting in an admin password and if I try it blank it does not accept it.

I found this on [http://www.theeldergeek.com/recovery_console.htm](http://www.theeldergeek.com/recovery_console.htm)
--------------------------------------------------------------------------
Recovery Console Password

On many XP installations you can't start the Recovery Console because it won't recognize your password. This registry edit causes the Recovery Console not to ask for a password. This works for both XP Home and XP Professional.

Start | Run | Regedit
Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Setup\RecoveryConsole
Set the DWORD SecurityLevel value to 1
Exit Registry and Reboot
---------------------------------------------------------------------------

does anyone know a way to edit the windows registry though linux?

---

