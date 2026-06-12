---
title: "A dual boot question"
date: 2009-01-12
forum: General Help
---

### Post by baldy1 on 2009-01-12
Hi folks I have been dual booting WinXP and Ubuntu and just in the last few days the computer has been going straight to XP and the screen that give me the choice of both OS's does not show - can you help me please.

---

### Post by Elfy on 2009-01-12
Is this is wubi install or a normal one?

If it's a normal install have you reinstalled windows? If that is the case then reinstall grub - [http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2)

---

### Post by baldy1 on 2009-01-12
Thanks for the reply - I am new to Ubuntu so don't know what a wubi install is - no I have not reinstalled windows - I did install grub when I installed Ubuntu if that helps.

---

### Post by Elfy on 2009-01-12
Wubi is when you install from inside windows and not by booting the livecd.

If you did do a normal install then please boot your livecd, run this command with a terminal and paste the output here please.

```
sudo fdisk -l
```

You can find terminal in the Application > Accessories menu.

---

### Post by ajgreeny on 2009-01-12
You can also just try hitting Esc when the words "starting grub" appear on screen to see if that at least brings up the grub menu.  It is difficult to see why this problem should suddenly occur, however, without some sort of input from you.  Have you installed something recently from somewhere other than the repositories, or done something else in windows that might have affected your boot management system in some way?

---

### Post by baldy1 on 2009-01-12
Ok I ran the command and it came up with a whole lot of linux speak that I don't understand yet - so I rebooted but there is no change.

Grub does not appear on boot up that is my problem and as far as I can recall I have not installed anything.

---

### Post by baldy1 on 2009-01-12
Very sorry not reading properly it is very late here (NZ)

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Elfy on 2009-01-12
that's not a 1 it's a lowercase L

---

### Post by baldy1 on 2009-01-12
Not doing very well am I

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5258    42234853+   7  HPFS/NTFS
/dev/sda2            5259       19457   114053467+   f  W95 Ext'd (LBA)
/dev/sda5            5259        7786    20306128+   7  HPFS/NTFS
/dev/sda6   *        7787       10382    20852338+  83  Linux
/dev/sda7           10383       10501      955836   82  Linux swap / Solaris
/dev/sda8           10502       15758    42226821    7  HPFS/NTFS
/dev/sda9           15759       19457    29712186    7  HPFS/NTFS

---

### Post by Elfy on 2009-01-12
heh - no worries - I had to ask how to bump :)

Run this

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sda6 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
```

It will print a bunch of stuff in the terminal - please paste it all into a post.

That's another l not a 1 :)

---

### Post by baldy1 on 2009-01-12
here we go

ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/tmp
ubuntu@ubuntu:~$ cat /mnt/tmp/boot/grub/menu.lst
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.24-22-generic

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, kernel 2.6.20-16-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by baldy1 on 2009-01-12
Thanks for the help Forestpixi but my eye's are on the floor and I need to sleep so I will look in tomorrow - thanks again

---

### Post by Elfy on 2009-01-12
```
gksu gedit /mnt/tmp/boot/grub/menu.lst
```

change the first boot options - if it works change the rest from inside buntu
```

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,[COLOR="Red"]5[/COLOR])
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root (hd0,[COLOR="Red"]5[/COLOR])
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=01bd742d-4086-428e-9fdd-5e2c46464d6a ro single
initrd /boot/initrd.img-2.6.24-22-generic
```

lol - everything is easier after some sleep :)

---

### Post by baldy1 on 2009-01-12
Well I have had some sleep but I am no smarter - I am not sure what to do with the info you have given me - I need a bit more instruction.

---

### Post by baldy1 on 2009-01-12
This is the result I get from the first code

ubuntu@ubuntu:~$ gksu gedit /mnt/tmp/boot/grub/menu.lst

(gedit:8584): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

