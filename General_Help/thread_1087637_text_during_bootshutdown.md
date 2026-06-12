---
title: "text during boot/shutdown"
date: 2009-03-05
forum: General Help
---

### Post by theozzlives on 2009-03-05
I took my Windows XP and put it in a VirtualBox, deleted the partition and gave the free space to /home. Now I get the standard text messages plus my usplash. I checked Startup Manager and "text during boot" is not checked. why am I getting text?

---

### Post by theozzlives on 2009-03-05
bump

---

### Post by kanikilu on 2009-03-05
Can you post the contents of your /boot/grub/menu.lst file?

---

### Post by theozzlives on 2009-03-05
sure:
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=36db3c4e-1ba5-48bf-8f7a-82f174f0b796

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
# defoptions=quiet splash vga=792

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		36db3c4e-1ba5-48bf-8f7a-82f174f0b796
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		36db3c4e-1ba5-48bf-8f7a-82f174f0b796
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		36db3c4e-1ba5-48bf-8f7a-82f174f0b796
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		36db3c4e-1ba5-48bf-8f7a-82f174f0b796
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		36db3c4e-1ba5-48bf-8f7a-82f174f0b796
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		The part I have to keep:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsnot Winblows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

ozzie@ozzie-laptop:/boot/grub$ 


```

OH CRAP! I forgot to take the Windows entry out... I bet that's it! 

no it wasn't, bummer!

---

### Post by kanikilu on 2009-03-05
Hmm, I was going to suggest adding the "ro quiet splash vga=792" if it wasn't already there, but that's not the problem. Sorry, I'm not sure...maybe someone else can suggest something?

---

### Post by plucky on 2009-03-05
There is a possibility the UUID of your partition has changed which would cause the splash screen not to display.

Post output of ```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

and see if the uuid's match


Good Luck

---

### Post by theozzlives on 2009-03-05
```
ozzie@ozzie-laptop:~$ sudo fdisk -lu
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40001849    20000893+  83  Linux
/dev/sda2        40001850   270630989   115314570   83  Linux
/dev/sda3       270630990   312576704    20972857+   5  Extended
/dev/sda5       270631053   312576704    20972826   82  Linux swap / Solaris
ozzie@ozzie-laptop:~$ sudo blkid -c /dev/null
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="36db3c4e-1ba5-48bf-8f7a-82f174f0b796" TYPE="ext3" 
/dev/sda2: UUID="3b519d3a-36f9-4b0c-ba4d-de096ad3fe82" TYPE="ext3" 
/dev/sda5: UUID="097ab7e1-5bc9-4b63-8f0d-e1462a6c3eae" TYPE="swap" 
ozzie@ozzie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3b519d3a-36f9-4b0c-ba4d-de096ad3fe82 /home           ext3    relatime        0       2
# /dev/sda5
UUID=097ab7e1-5bc9-4b63-8f0d-e1462a6c3eae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ozzie@ozzie-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0b1ce304-9f7f-447b-b750-cb422a02d22b
ozzie@ozzie-laptop:~$ 

```

---

### Post by dcstar on 2009-03-05
> **theozzlives said:**
> I took my Windows XP and put it in a VirtualBox, deleted the partition and gave the free space to /home. Now I get the standard text messages plus my usplash. I checked Startup Manager and "text during boot" is not checked. why am I getting text?

```
sudo update-initramfs -k all -u
```

---

### Post by theozzlives on 2009-03-06
> **dcstar said:**
> ```
sudo update-initramfs -k all -u
```

Thanks I actually thought that would work. I get the usplash, it goes back and forth a couple times, the I get "reading files needed to boot". It's all text from there.

---

### Post by plucky on 2009-03-06
Did the "sudo update-initramfs -k all -u" update the "resume" UUID?

This ```
RESUME=UUID=0b1ce304-9f7f-447b-b750-cb422a02d22b
``` should read ```
RESUME=UUID=097ab7e1-5bc9-4b63-8f0d-e1462a6c3eae
``` or the same as the "swap" partition.

Good Luck

---

### Post by theozzlives on 2009-03-06
> **plucky said:**
> Did the "sudo update-initramfs -k all -u" update the "resume" UUID?

This ```
RESUME=UUID=0b1ce304-9f7f-447b-b750-cb422a02d22b
``` should read ```
RESUME=UUID=097ab7e1-5bc9-4b63-8f0d-e1462a6c3eae
``` or the same as the "swap" partition.

Good Luck

Man I could prolly dance circles around you in DOS, but I have no clue how to change the RESUME-UUID.

I figured out how to change it, but it's still doin the same thing... I don't think it's hurtin anything, it just don't make things as "pretty" as I'd like it.

---

### Post by theozzlives on 2009-03-06
I just realized when I was re-doing everything I made a 20 GB swap, in the process of fixing that now, duh!

---

### Post by theozzlives on 2009-03-06
```
ozzie@ozzie-laptop:~$ sudo fdisk -lu && sudo blkid -c /dev/null && cat /etc/fstab && cat /etc/initramfs-tools/conf.d/resume
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40001849    20000893+  83  Linux
/dev/sda2        40001850   308383739   134190945   83  Linux
/dev/sda3       308383740   312576704     2096482+   5  Extended
/dev/sda5       308383803   312576704     2096451   82  Linux swap / Solaris
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="36db3c4e-1ba5-48bf-8f7a-82f174f0b796" TYPE="ext3" 
/dev/sda2: UUID="3b519d3a-36f9-4b0c-ba4d-de096ad3fe82" TYPE="ext3" 
/dev/sda5: UUID="bfaf5249-ad33-49e3-b380-cdb02767e683" TYPE="swap" 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3b519d3a-36f9-4b0c-ba4d-de096ad3fe82 /home           ext3    relatime        0       2
# /dev/sda5
UUID=bfaf5249-ad33-49e3-b380-cdb02767e683 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
RESUME=UUID=bfaf5249-ad33-49e3-b380-cdb02767e683
```

Well everything seems as it should be, same problem! HUMPH!

---

### Post by unutbu on 2009-03-06
What is the output of ```

cat /proc/cmdline
```

---

### Post by theozzlives on 2009-03-06
> **unutbu said:**
> What is the output of ```

cat /proc/cmdline
```

root=UUID=36db3c4e-1ba5-48bf-8f7a-82f174f0b796 ro quiet splash vga=792

---

### Post by plucky on 2009-03-06
> [color=red]/dev/ramzswap0: TYPE="swap"[/color] 
/dev/sda1: UUID="36db3c4e-1ba5-48bf-8f7a-82f174f0b796" TYPE="ext3" 
/dev/sda2: UUID="3b519d3a-36f9-4b0c-ba4d-de096ad3fe82" TYPE="ext3" 
/dev/sda5: UUID="bfaf5249-ad33-49e3-b380-cdb02767e683" TYPE="swap" 


What is "[color=red]/dev/ramzswap0: TYPE="swap"[/color]? I assume it is to do with virtualbox.Would it be worth commenting it out to see if it makes a difference.

One last thing I can think of is ```
cat /etc/usplash.conf
```

---

### Post by theozzlives on 2009-03-06
```
ozzie@ozzie-laptop:~$ cat /etc/usplash.conf
# Usplash configuration file
xres=1024
yres=768

```

K, I'll comment that out

---

### Post by theozzlives on 2009-03-06
Well my box came to send in my laptop in to Dell, so keep posting ideas I still have 2 other computers. I just won't be able to give you any info from this one.

---

### Post by nuir on 2009-03-17
I had the same problem after changing the size of some partitions in my disk. The following solution worked for me:

1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart

Good luck!

---

### Post by theozzlives on 2009-03-17
```
[sudo] password for ozzie: 
/dev/sda1: UUID="36db3c4e-1ba5-48bf-8f7a-82f174f0b796" TYPE="ext3" 
/dev/sda2: UUID="3b519d3a-36f9-4b0c-ba4d-de096ad3fe82" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda3: UUID="FE3884CD3884867D" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="bfaf5249-ad33-49e3-b380-cdb02767e683" 
/dev/ramzswap0: TYPE="swap"
```

I don't have ntfs or swap anymore I just got sda1 and sda2, how do I change that. Apparently the system thinks the old partitions still exist.

---

### Post by theozzlives on 2009-03-17
well I fixed it, all I did was delete the contents of the resume file. I don't know if that did it or not, but it works now. Thanks for all your help.

---

