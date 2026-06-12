---
title: "[SOLVED] Unable to boot form HDD?"
date: 2009-01-03
forum: General Help
---

### Post by Matt Baessler on 2009-01-03
I recently acquired a Compaq Presario AMD Athlon XP 2200+ with 755.6 MB Ram, 80GB HDD, ATI Radon 9200 PCI 128MB, IEEE 1394 and USB 2.0 extensions, CD-RW/DVD-+RW and CD-RW Drives. 

If I am missing, any system info necessary to solve the problem let me know. 

The installation is GNOME 2.24.1, Ubuntu 8.10 (intrepid) Release, Linux Kernel 2.6.27-7- generic.

I will try to provide as much info as possible but I am no expert and new to Linux and Ubuntu. 

The Ubuntu Live CD runs great and my card even supports the eye candy well. The Installation seemed to work just fine I did a full Install, as it seemed the easiest to do. I was then prompted to take out the CD and restart which I did. I have my HDD set as the master but Ubuntu does not boot Instead after a few minutes I get a disk boot failure. I am unsure what to make of this as when booted by the Live CD the HDD appears with all the Installed files so It is obviously recognizing the HDD. Is this a hardware issue, is there something in my bios I should do or is this more related toward grub (I can see the grub files that were installed if that helps).

Looked around the forums a bit and figured this my help...

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d61807c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156312449    78156193+  83  Linux
/dev/sda2       156312450   160826714     2257132+   5  Extended
/dev/sda5       156312513   160826714     2257101   82  Linux swap / Solaris

```

---

### Post by jerome1232 on 2009-01-03
It sounds to me like your bios is setup to only boot off of a cdrom disk and not the hdd.

Go into you bios and make sure it's set to boot off of a hard drive, the menu's will vary wildly depending on what bios you have so I can't really give a step by step guide on how to do it.

---

### Post by semi_fiction on 2009-01-03
Did you manually set up the partition layout?

If you did, did you remember to make a partition mounted at "/boot"?

---

### Post by Matt Baessler on 2009-01-03
Thanks for replying I just tried setting the Boot Device Priority for both first and second as the HDD the third is CDROM and the forth is LAN yet still no luck with it booting from the HDD.

Edit: No I didn't manually install it I just did the basic full install I didn't want to mess up any thing.

More info I'm continuing my search for an answer and tried this code in the Terminal...

```
sudo grub
grub> find /boot/grub/stage1
```

I'm wandering if It gives me an "Error 15: File not found" does it mean grub is missing or am I just confusing myself?

Even more info if it helps I saw some post that requested the menu.lst!!

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
# kopt=root=UUID=808e03b4-1867-4d57-8c6b-c853da323e58 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=808e03b4-1867-4d57-8c6b-c853da323e58

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		808e03b4-1867-4d57-8c6b-c853da323e58
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=808e03b4-1867-4d57-8c6b-c853da323e58 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		808e03b4-1867-4d57-8c6b-c853da323e58
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=808e03b4-1867-4d57-8c6b-c853da323e58 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		808e03b4-1867-4d57-8c6b-c853da323e58
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

---

### Post by Matt Baessler on 2009-01-04
Ok, so I tried wiping the HDD and trying a seconded time but still no luck just the same as before. If any one could help me I would greatly appreciate it I really want ubuntu as my desktop.

More info form boot_info_script....

```

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d61807c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156312449    78156193+  83  Linux
/dev/sda2       156312450   160826714     2257132+   5  Extended
/dev/sda5       156312513   160826714     2257101   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="467406f1-1ea5-4f75-94c2-2aa0c2c6f57f" TYPE="ext3" 
/dev/sda5: UUID="ad2b42da-01b7-4ab5-b05d-b55d45c741b6" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=467406f1-1ea5-4f75-94c2-2aa0c2c6f57f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=467406f1-1ea5-4f75-94c2-2aa0c2c6f57f

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		467406f1-1ea5-4f75-94c2-2aa0c2c6f57f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=467406f1-1ea5-4f75-94c2-2aa0c2c6f57f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		467406f1-1ea5-4f75-94c2-2aa0c2c6f57f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=467406f1-1ea5-4f75-94c2-2aa0c2c6f57f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		467406f1-1ea5-4f75-94c2-2aa0c2c6f57f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=467406f1-1ea5-4f75-94c2-2aa0c2c6f57f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ad2b42da-01b7-4ab5-b05d-b55d45c741b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2009-01-04 01:51 .
drwxr-xr-x 20 root root    4096 2009-01-04 01:51 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-04 01:51 grub
-rw-r--r--  1 root root 8180046 2009-01-04 01:51 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-04 01:51 .
drwxr-xr-x 3 root root   4096 2009-01-04 01:51 ..
-rw-r--r-- 1 root root    197 2009-01-04 01:51 default
-rw-r--r-- 1 root root     15 2009-01-04 01:51 device.map
-rw-r--r-- 1 root root   8108 2009-01-04 01:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-04 01:51 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-04 01:51 installed-version
-rw-r--r-- 1 root root   8712 2009-01-04 01:51 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-04 01:51 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-04 01:51 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-04 01:51 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-04 01:51 stage1
-rw-r--r-- 1 root root 121460 2009-01-04 01:51 stage2
-rw-r--r-- 1 root root   9556 2009-01-04 01:51 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

Does this mean I missing the grub boot loader? If so how do I get the missing boot loader?

Should I use Super Grub Boot Disk to try and fix this?

---

### Post by caljohnsmith on 2009-01-04
According to everything that the script reported, you have Grub properly installed to your sda drive, so you should be able to boot it. Since you can't, it sounds like you could have an issue with how the drive is set up in BIOS. Was there previously an OS on that drive (maybe like Windows) that booted OK? Have you ever booted successfully from that drive? How about going into your BIOS and let us know what HDD-related settings you have, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. That might help pinpoint your problem.

---

### Post by Matt Baessler on 2009-01-04
Thanks for the reply!

I was a little worried when the script showed "Boot sector type: No Boot Loader." Anyway, The history is a bit cloudy as the HDD is not mine I would guess it had XP installed before. I have never booted form this HDD it was wiped when I got it. If I need a new HDD do you have any suggestions on brand and such? 

```

Primary Master
--------------
IDE HDD Auto-Detection [Press Enter]

IDE Primary Master [Auto]
Access Mode [Auto] (I can choose form Auto, Large, LBA, CHS)

Capacity: 82 GB

Cylinder: 39420
Head: 16
Precomp: 0
Landing Zone: 39419
Sector: 255
Transfer Mode: UDMA 5

```

First Boot Device [Hard Disk]
Second Boot Device [Hard Disk]
Third Boot Device [CDROM]
Fourth Boot Device [LAN]

It says detecting IDE drives so I guess its IDE

Local Bus IDE Adapter is set to Both

---

### Post by caljohnsmith on 2009-01-04
OK, under the "Access mode" setting in your BIOS, how about choosing LBA, and if that doesn't change anything, also try "large". If neither of those help your booting problems, then go ahead and change it back to Auto and let me know.

---

### Post by buccaneere on 2009-01-04
> **Matt Baessler said:**
>  I have my HDD set as the master but Ubuntu does not boot 

Since the drive mounts while on Live CD boot, I'm bettin' you should double check the jumper...

---

### Post by Matt Baessler on 2009-01-04
Nope still got a Disk Boot Failure for LBA and Large.

Its got 2 so its a with No ATA-Compatible Slave should it just be one?

Edit: It was the Jumper!! Thank you all for your support I learned a lot form this!

---

