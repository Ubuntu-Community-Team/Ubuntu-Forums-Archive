---
title: "Grub menu.lst help required"
date: 2009-03-19
forum: General Help
---

### Post by utnubuuser on 2009-03-19
Hello -- I've got a triple-boot, Lenny, XP, and Puppy Linux, set up on an older pavilion laptop, and I've lost access to XP.

It was working, then I had to resize the Debian partition, and tried to make XP, (cringe), the default in grub.  Now I get error 27, an invalid command.
Debian and Puppy are still ok, but I cannot figure out how to get XP to load.
As I've said, I've made a couple changes in the menu.lst, and tried to revert unsuccessfully, so I'm hoping someone knowledgeable with grub can help.

here is the fdisk output:> Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a2b8a2

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           3       24066   a0  IBM Thinkpad hibernation
/dev/hda2   *           4        1276    10225372+   7  HPFS/NTFS
/dev/hda3            1277        1707     3462007+  83  Linux
/dev/hda4            1708        2432     5823562+   5  Extended
/dev/hda5            1708        1752      361431   82  Linux swap / Solaris
/dev/hda6            1753        2199     3590496   83  Linux
/dev/hda7            2200        2432     1871541   83  Linux
brad@debian-dp:~$ 


and the menu.lst file> brad@debian-dp:~$ fdisk -l

brad@debian-dp:~$ sudo fdisk -l
[sudo] password for brad: 

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a2b8a2

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           3       24066   a0  IBM Thinkpad hibernation
/dev/hda2   *           4        1276    10225372+   7  HPFS/NTFS
/dev/hda3            1277        1707     3462007+  83  Linux
/dev/hda4            1708        2432     5823562+   5  Extended
/dev/hda5            1708        1752      361431   82  Linux swap / Solaris
/dev/hda6            1753        2199     3590496   83  Linux
/dev/hda7            2200        2432     1871541   83  Linux
brad@debian-dp:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		30

# Pretty colours
color cyan/blue white/blue

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/hda3 ro quiet
initrd		/boot/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.26-1-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
default 0
makeactive
chainloader	+2

title Puppy Linux 400 full install in hda7
root (hd0,6)
kernel /boot/vmlinuz root=/dev/hda7 pmedia=idehd
brad@debian-dp:~$ 


I also tried using the Startup-manager, and got the same result from it.
Any chance of getting XP up and running again without having to use a XP disk to fix MBR?

---

### Post by meierfra. on 2009-03-19
Remove the  line 

default 0

from the Windows item in menu.lst

and change 

chainloader +2

to

 chainloader +1

---

### Post by utnubuuser on 2009-03-19
Thanks meierfra!!

---

### Post by meierfra. on 2009-03-19
> Thanks meierfra!!
You are welcome.
Have fun with XP, Lenny and Puppy.

---

