---
title: "adding Ubuntu to an existing GRUB"
date: 2008-12-21
forum: General Help
---

### Post by tjwoosta on 2008-12-21
i am struggling with adding ubuntu to my arch grub

i was running ubuntu before, then i decided to play with arch

i figured i would just overwrite GRUB because it was no big deal because i can just add ubuntu to the arch grub

i have tried everything and it still wont load 

i have even tried copying the ubuntu entry from the old menu.lst but nothing works

here is my new menu.lst (arch)
```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue
# splashimage /boot/grub/arch-boot.xpm.gz

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
# 
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro vga=791
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro
initrd /boot/kernel26-fallback.img

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet


```

here is the old menu.lst (ubuntu)

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
default		0

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
# kopt=root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5a3780cd-6bbd-420a-9860-b50cb57d5d33

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
# defoptions=quiet splash vga=771

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

i have tried everything i can think of

from...

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root   (hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/disk/by-uuid/5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

to

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root    (hd0,0)
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-9-generic
makedefault
boot
quiet

to everything in between

the error it ususally gives me is..
 error 15 


also im not sure of the significance but...

back when i was dual booting elive i had a similar issue where ubuntu wouldnt boot when i copied the ubuntu menu.lst entry into elives grub

but it would boot fine if i left the elive entry alone and just modified the kernel number

(i figured this out because ubuntu had a kernel update and i had to manually modify elives grub to point toward ubuntu's new kernel)

too bad i cant remember what the differences were between the two menu.lst's because i think if i set up my new grub the way elives grub was it might boot ubuntu


can somebody please shed some light on the situation

---

### Post by Jammanuser on 2008-12-21
> **tjwoosta said:**
> 

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro
initrd /boot/kernel26-fallback.img

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5a3780cd-6bbd-420a-9860-b50cb57d5d33
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5a3780cd-6bbd-420a-9860-b50cb57d5d33 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

[/CODE]



Try adding:

```
# (2) Ubuntu Linux
```

right before the title of Ubuntu 8.10...i suspect that that may fix it! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by caljohnsmith on 2008-12-21
So is Ubuntu on the first partition sda1? How about first installing Grub to the boot sector of your Ubuntu partition by doing the following:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
Or if Arch doesn't use "sudo" to execute commands as root, just use do whatever you need to in order to run "grub" as root user above. Next, add the following to your Arch menu.lst:
```
title  Ubuntu Grub Menu
root (hd0,0)
chainloader +1
```
Then reboot, select "Ubuntu Grub Menu" in your Arch Grub menu, and please let me know what happens. We can work from there if you want.

---

### Post by tjwoosta on 2008-12-21
> # (2) Ubuntu Linux

nope, tried, that does nothing  (notice how its commented out #)


> So is Ubuntu on the first partition sda1? How about first installing Grub to the boot sector of your Ubuntu partition by doing the following:

i know for a fact that ubuntu is located at sda1 or (hd0,0)

i also know for a fact that ubuntus partition is still intact (with /boot/grub/stage1) because i can mount it from arch

```

grub>
      root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub>
      setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type

grub>


```

```

[tj@myhost ~]$ cd /media/ubuntu/boot/grub/  
[tj@myhost grub]$ ls -a
.              installed-version  reiserfs_stage1_5
..             jfs_stage1_5       splashimages
default        menu.lst           stage1
device.map     menu.lst.backup    stage2
e2fs_stage1_5  menu.lst~          xfs_stage1_5
fat_stage1_5   minix_stage1_5
[tj@myhost grub]$ 



```

this is driving me nuts


i keep seeing that same "bad file or directory type" error over and over again with almost everything i try

---

### Post by caljohnsmith on 2008-12-21
Do you have Ubuntu Intrepid installed, or are you using an earlier version of Ubuntu? If sda1 is Intrepid, that could be the reason why you are having problems with those Grub commands in Arch. The reason is because Intrepid now formats its ext3 partitions to use a 256 byte inode size for the file system, as opposed to previous versions of Ubuntu that use a 128 byte inode size. How about booting your Intrepid Live CD if you have one, and then run the Grub commands from there. Let me know how it goes.

---

### Post by tjwoosta on 2008-12-21
youre a grub genius!

it worked!!

thank you


if you dont mind, could you please point me toward some of the documetation where you learned about this ?

---

### Post by caljohnsmith on 2008-12-21
> **tjwoosta said:**
> youre a grub genius!

it worked!!

thank you


if you dont mind, could you please point me toward some of the documetation where you learned about this ?
You're welcome, I'm glad to hear that worked. Here are a few good resources about Grub you might want to check out:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

If you have any specific questions regarding Grub, I would be happy to try and answer them; but the above links are a good place to start if you want to learn more about Grub. Cheers and have fun with Arch and Ubuntu. :)

---

