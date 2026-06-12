---
title: "/bin/sh: can't access...."
date: 2009-01-22
forum: General Help
---

### Post by Amyrlin on 2009-01-22
Hi! I am dual booting Vista and Ubuntu and Vista boots from grub just fine. When I boot Ubuntu from grub I get the following:

/bin/sh: can't access tty; job control turned off
#

How do I fix this? Thanks :)

also: I have three copies to boot from for Ubuntu (they all give me the same result) and I was told I could erase two of them, how do I do that? Thanks again :)

---

### Post by Crafty Kisses on 2009-01-22
First you might want to read this thread, [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588). Secondly you can remove GRUB entries, so you have the ones you want, you can do that by doing the following: 
```
sudo gedit /boot/grub/menu.lst
```
Then look at what entries you want to remove, and you can do it that way.

---

### Post by Amyrlin on 2009-01-22
I get this with fdisk -l from the live CD which boots fine for me on re-start:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7699    61842186    7  HPFS/NTFS
/dev/sda2            7700       14408    53890042+  83  Linux
/dev/sda3           14409       14593     1486012+   5  Extended
/dev/sda5           14409       14593     1485981   82  Linux swap / Solaris

If I follow those instructions will it erase the things I already had there? I have emails from my Dad who passed away this last October and I REALLY don't want to lose them.

Also, when I use:

sudo gedit /boot/grub/menu.lst

from the CD it comes up blank so I went to file and 1. menu.lst and it says it is not found.

---

### Post by bodhi.zazen on 2009-01-23
If you are booting from the live CD you have to mount your linux install before you can access the data.

```
sudo mount /dev/sda2 /mnt
```

you will find menu.lst at 

```
gksu gedit /mnt/boot/grub/menu.lst
```

I am not sure that error is from grub though ...

---

### Post by Amyrlin on 2009-01-23
can I skip the first part (of the above links instructions) because the CD boots fine and just mount the drives that are still there?

I think I just need to fix the chroot as it is misplaced (after mounting the drives)?

also, I am dual booting from grub regularly and want to keep doing so, not boot directly into Ubuntu. I am lost in this part of the chroot command :( 

-----------------------------------------------------------

*Thanks, Here's grub:*

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
timeout		25

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
# kopt=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1

*and I also got this in the terminal:*

(gedit:7470): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


*By the way, how do I put code in those boxes? Thanks :)*

---

### Post by bodhi.zazen on 2009-01-23
looks like you need to change sda3 to sda5 in these lines (for all your enteries).

itle		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 **root=/dev/sda3** ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

to

itle		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 **root=/dev/sda5** ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

---

### Post by Amyrlin on 2009-01-23
so I am supposed to have grub booting Ubunto from sda5 then? The swap/Solaris? Will this fix the job control problem or is this something else? :D Nervouse here because I'm new...Thanks!

Okay, I changed them to 5 and am still getting a boot up error. I am also attempting the "fix" in the link above and am now getting this:


ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ mkdir target
ubuntu@ubuntu:~$ sudo mount /dev/sda2 target
ubuntu@ubuntu:~$ sudo chroot target
root@ubuntu:/# echo piix >> /etc/initramfs-tools/modules
bash: /etc/initramfs-tools/modules: No such file or directory
root@ubuntu:/# gksu gedit /etc/initramfs-tools/modules

(gksu:6956): Gtk-WARNING **: cannot open display:
root@ubuntu:/# sudo gedit etc/initramfs-tools/modules
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@ubuntu:/# gksudo gedit etc/initramfs-tools/modules

(gksudo:7008): Gtk-WARNING **: cannot open display:
root@ubuntu:/#

---

### Post by Amyrlin on 2009-01-23
bumpity...

---

### Post by bodhi.zazen on 2009-01-23
> **Amyrlin said:**
> so I am supposed to have grub booting Ubunto from sda5 then? The swap/Solaris? Will this fix the job control problem or is this something else? :D Nervouse here because I'm new...Thanks!

Okay, I changed them to 5 and am still getting a boot up error. 

My mistake, sorry I was tired when I looked at your post.

No you need to point grub to your root partition. /dev/sda3 is an extended partition not root.

So it must be /dev/sda2 ;)

---

