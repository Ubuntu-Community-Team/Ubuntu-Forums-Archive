---
title: "how to use live CD for fix GRUB Error?"
date: 2009-06-29
forum: Desktop Environments
---

### Post by tonjaa on 2009-06-29
i have problem when i boot to Ubutu. i have 2 Hard disk and 2 OS at first time it's can use normal.
one hard disk i install Ubuntu 9.04 and another one i install fedora 11 . but now when i try to boot in
Ubuntu it can't to login . at screen show this.
[COLOR=DarkOrange]
Booting from localdisk...
GRUB Loading stage1.5.

GRUB loading,please wait...
Error 22[/COLOR]

i try to use live CD of Ubuntu 8.10 for find the way to fix it but i don't know how to use it.?
i can't see line for use command .

and i have CD. system rescue x86 v.1.2.0  i try to do but don't know the correct way to use it.
it can use to fix about GRUB Error or not?  how i can change directory to hard disk and how to
use GRUB to boot again? 
please guide me to do.

---

### Post by Mia1990 on 2009-06-29
Hello,
have you tried super grub disk you can download it from this [website ]("http://www.supergrubdisk.org/index.php?pid=5")

---

### Post by binbash on 2009-06-29
you will mount with Ubuntu Live CD , run ubuntu via Live CD.Then open a terminal there, mount the partition you want to work, mount /proc /dev etc and start fixing your problem.

---

### Post by 0x29a on 2009-06-29
Error 22 means that grub can't find the boot device in /boot/grub/menu.lst

Fedora still works, correct?

As binbash noted you an use the Live CD to fix your boot problem. The hard part is going to be walking you through all of this. The first thing you'll need to do is boot from the Live CD and open a command prompt.

Once that's done please type the following command:
```

sudo fdisk -l
```
That will list your hard drives. This will help us find where /boot/grub is located. Look for lines similar to this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15735636    83  Linux
```

Look for the partition that has the star (*) next to the device as shown above. Remember that it <i>may not</i> be /dev/sda1 on your system. This is the most likely location of /boot/grub/

Once you find that run these commands:
```

sudo mkdir /tempmount
sudo mount -t auto /dev/sda1 /tempmount
```

Now type:
```

cd /tempmount
ls
```
Look for the /boot directory. If you find it run this command:
```

cat /tempmount/boot/grub/menu.lst > ~/Desktop/menu.lst
```
This will create a file on the desktop called menu.lst. Copy the contents of that file here. That will help us figure out what's wrong.

Let me know if you have any problems getting this far.

Andrew

---

### Post by tonjaa on 2009-06-29
[COLOR=Green]i thank you so much for everybody to guide me .
that i do for down load super grub cd and i try to use it . but may be i use it wrong way
i can't fix it i do partition lose i try to bring it back but i don't know the correct way.
it's have some file Error and i don't know to edit grub. 
and now i clinch to reinstall Ubuntu again i had back up some flies in cd rom i regret bit .
OK. now i can use . and i try to learning to manage about grub problem that you guide to me .  
thank you [/COLOR];)

---

### Post by Platypus123 on 2009-07-19
Sorry about hijacking this thread.  This sounds like my problem as well (separate hard drives for Windows and Ubuntu).  Here is my menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sdd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-13-generic
uuid 235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid 235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=235a9612-9d5f-4200-ac18-9fa3cbc4ab99 ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid 235a9612-9d5f-4200-ac18-9fa3cbc4ab99
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Let me know if you need any more information.  My original post is [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1215012").

---

### Post by Platypus123 on 2009-08-14
Wiped Vista off of my system and switched my NTFS drives to EXT4.  Much faster! Problem solved, but not by figuring out non-formatting answer.  I can't remember if I had to reinstall Ubuntu though...

---

