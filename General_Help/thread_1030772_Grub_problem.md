---
title: "Grub problem"
date: 2009-01-04
forum: General Help
---

### Post by winol5 on 2009-01-04
Hi.

When I start my computer I get:

GRUB loading, please wait
error 2

This after making the root (hdo,2) setup (hd0) thing, first I get the grub like shell

Grub>

I have linux in sda3, and windows in sda1 or hd0

---

### Post by caljohnsmith on 2009-01-04
In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by melojo on 2009-01-04
boot from the live cd and goto applications>accessories>terminal and type this.

```

sudo su

```

then
```

fdisk -l

```

post the ouput

This will give us more info

---

### Post by melojo on 2009-01-04
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

That is a great script!!

---

### Post by winol5 on 2009-01-04
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b7e17fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    60002774    30001356    7  HPFS/NTFS
/dev/sda2        60002775   234436544    87216885    5  Extended
/dev/sda3        64003023   234436544    85216761   83  Linux
/dev/sda5        60002901    64002959     2000029+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 3 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="020483070482FD43" TYPE="ntfs" 
/dev/sda3: UUID="96d62ef2-53d3-4267-8ced-fdf76d77ebce" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="56aa8cee-89cc-4b3f-b78b-0dfc21b77041" TYPE="swap" 
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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

gfxmenu /boot/grub/message.blusplash

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color light-green/green white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/start.xpm.gz

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
# kopt=root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96d62ef2-53d3-4267-8ced-fdf76d77ebce

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





# defoptions=quiet splash vga=786

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
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/memtest86+.bin
quiet

title Windows XP 
root (hd0,0) 
makeactive 
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=56aa8cee-89cc-4b3f-b78b-0dfc21b77041 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

================================== sda3/boot: ==================================

total 59284
drwxr-xr-x  3 root root    4096 2009-01-04 21:38 .
drwxr-xr-x 20 root root    4096 2008-12-28 19:16 ..
-rw-r--r--  1 root root  507990 2008-11-21 13:46 abi-2.6.27-10-generic
-rw-r--r--  1 root root  508385 2008-12-19 17:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507735 2008-11-06 19:20 abi-2.6.27-8-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91358 2008-11-21 13:46 config-2.6.27-10-generic
-rw-r--r--  1 root root   91358 2008-12-19 17:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-06 19:20 config-2.6.27-8-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2009-01-04 21:55 grub
-rw-r--r--  1 root root 8195258 2009-01-04 21:37 initrd.img-2.6.27-10-generic
-rw-r--r--  1 root root 8197899 2009-01-04 21:37 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8195211 2009-01-04 21:38 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8194765 2009-01-04 21:38 initrd.img-2.6.27-8-generic
-rw-r--r--  1 root root 8195536 2009-01-04 21:37 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029828 2008-11-21 13:46 System.map-2.6.27-10-generic
-rw-r--r--  1 root root 1031799 2008-12-19 17:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029612 2008-11-06 19:20 System.map-2.6.27-8-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1074 2008-11-21 13:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r--  1 root root    1074 2008-12-19 17:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-06 19:22 vmcoreinfo-2.6.27-8-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2247280 2008-11-21 13:46 vmlinuz-2.6.27-10-generic
-rw-r--r--  1 root root 2248912 2008-12-19 17:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-06 19:20 vmlinuz-2.6.27-8-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda3/boot/grub: ===============================

total 352
drwxr-xr-x 3 root root   4096 2009-01-04 21:55 .
drwxr-xr-x 3 root root   4096 2009-01-04 21:38 ..
-rw-r--r-- 1 root root    197 2009-01-04 21:49 default
-rw-r--r-- 1 root root     15 2008-12-28 04:59 device.map
-rw-r--r-- 1 root root   7444 2009-01-04 21:49 e2fs_stage1_5
-rw-r--r-- 1 root root   7268 2009-01-04 21:49 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 04:59 installed-version
-rw-r--r-- 1 root root   6580 2009-01-04 21:49 iso9660_stage1_5
-rw-r--r-- 1 root root   8064 2009-01-04 21:49 jfs_stage1_5
-rw-r--r-- 1 root root   4505 2009-01-04 21:55 menu.lst
-rw-r--r-- 1 root root   4462 2009-01-04 21:36 menu.lst~
-rw-r--r-- 1 root root   4369 2008-12-28 20:52 menu.lst.backup
-rw-r--r-- 1 1000 1000 127488 2006-07-18 22:12 message.blusplash
-rw-r--r-- 1 root root   6740 2009-01-04 21:49 minix_stage1_5
-rw-r--r-- 1 root root   9012 2009-01-04 21:49 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-30 18:26 splashimages
-rw-r--r-- 1 root root    512 2009-01-04 21:49 stage1
-rw-r--r-- 1 root root 100948 2009-01-04 21:49 stage2
-rw-r--r-- 1 root root   8700 2009-01-04 21:49 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
```

BTW I love this script xD

> **melojo said:**
> boot from the live cd and goto applications>accessories>terminal and type this.

```

sudo su

```

then
```

fdisk -l

```

post the ouput

This will give us more info

```
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b7e17fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3735    30001356    7  HPFS/NTFS
/dev/sda2            3736       14593    87216885    5  Extended
/dev/sda3            3985       14593    85216761   83  Linux
/dev/sda5            3736        3984     2000029+  82  Linux swap / Solaris

```

BTW i don't know if this affects but I have to do the fidsk thing with sudo, without it it just displayed "Cannot open /dev/sda"

---

### Post by caljohnsmith on 2009-01-04
[QUOTE=winol5]```
fdisk -lu /dev/sda:
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b7e17fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    60002774    30001356    7  HPFS/NTFS
[COLOR="Red"]/dev/sda2        60002775   234436544[/COLOR]    87216885    5  Extended
[COLOR="Red"]/dev/sda3        64003023   234436544[/COLOR]    85216761   83  Linux
/dev/sda5        60002901    64002959     2000029+  82  Linux swap / Solaris
```
[/QUOTE]
As noted by the above error highlighted in red, you have an empty partition, meaning that the extended partition or one of the EBRs (Extended Boot Records) incorrectly points to a partition that doesn't exist. Also, your sda3 primary partition is inside of your sda2 extended partition, so it should be a logical partition instead. So unfortunately the bottom line is that your partition table is corrupt. How about posting the output of:
```
sudo sfdisk -d /dev/sda
```
And we can work from there.

---

### Post by winol5 on 2009-01-04
done, thx

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 60002712, Id= 7, bootable
/dev/sda2 : start= 60002775, size=174433770, Id= 5
/dev/sda3 : start= 64003023, size=170433522, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 60002901, size=  4000059, Id=82

```

---

### Post by caljohnsmith on 2009-01-04
OK, first make sure you have all your important data on the drive backed up, download the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings that you don't need to be concerned about, but please post the output. Next reboot, and then do:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And please post the output. We can work from there.

---

### Post by caljohnsmith on 2009-01-04
> **melojo said:**
> That is a great script!!
I agree, and all the credit goes to forum member meierfra for creating that really useful script. It sure makes troubleshooting these types of problems so much easier. :)

---

### Post by winol5 on 2009-01-04
> **caljohnsmith said:**
> OK, first make sure you have all your important data on the drive backed up, download the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings that you don't need to be concerned about, but please post the output. Next reboot, and then do:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And please post the output. We can work from there.

```
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   3734    3735-  30001356    7  HPFS/NTFS
/dev/sda2       3735   14592   10858   87216885    5  Extended
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3       3984+  14592   10609-  85216761   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       3735+   3983     249-   2000029+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  60002774   60002712   7  HPFS/NTFS
/dev/sda2      60002775 234436544  174433770   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5      60002901  64002959    4000059  82  Linux swap / Solaris
/dev/sda6      64003023 234436544  170433522  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

I reboot in the live cd right? also the commands for grub were made kindly especifically for me, or should I adapt them?

---

### Post by caljohnsmith on 2009-01-04
Looks good, so so go ahead and reboot the Live CD; and yes, the Grub commands are specifically for your setup. :)

---

### Post by winol5 on 2009-01-04
> **caljohnsmith said:**
> Looks good, so so go ahead and reboot the Live CD; and yes, the Grub commands are specifically for your setup. :)

Thx, but I get the error 2 again :S (rebooted after making the grub commands)

---

### Post by caljohnsmith on 2009-01-04
> **winol5 said:**
> Thx, but I get the error 2 again :S (rebooted after making the grub commands)
Did the Grub commands say they completed successfully? If so, how about rerunning the script again from post #2 and posting the output.

---

### Post by winol5 on 2009-01-04
I think yes
```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

here:
```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b7e17fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    60002774    30001356    7  HPFS/NTFS
/dev/sda2        60002775   234436544    87216885    5  Extended
/dev/sda5        60002901    64002959     2000029+  82  Linux swap / Solaris
/dev/sda6        64003023   234436544    85216761   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="020483070482FD43" TYPE="ntfs" 
/dev/sda5: UUID="56aa8cee-89cc-4b3f-b78b-0dfc21b77041" TYPE="swap" 
/dev/sda6: UUID="96d62ef2-53d3-4267-8ced-fdf76d77ebce" SEC_TYPE="ext2" TYPE="ext3" 
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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

gfxmenu /boot/grub/message.blusplash

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color light-green/green white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/start.xpm.gz

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
# kopt=root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96d62ef2-53d3-4267-8ced-fdf76d77ebce

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





# defoptions=quiet splash vga=786

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
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		96d62ef2-53d3-4267-8ced-fdf76d77ebce
kernel		/boot/memtest86+.bin
quiet

title Windows XP 
root (hd0,0) 
makeactive 
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=96d62ef2-53d3-4267-8ced-fdf76d77ebce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=56aa8cee-89cc-4b3f-b78b-0dfc21b77041 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

================================== sda6/boot: ==================================

total 59284
drwxr-xr-x  3 root root    4096 2009-01-04 21:38 .
drwxr-xr-x 20 root root    4096 2008-12-28 19:16 ..
-rw-r--r--  1 root root  507990 2008-11-21 13:46 abi-2.6.27-10-generic
-rw-r--r--  1 root root  508385 2008-12-19 17:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507735 2008-11-06 19:20 abi-2.6.27-8-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91358 2008-11-21 13:46 config-2.6.27-10-generic
-rw-r--r--  1 root root   91358 2008-12-19 17:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-06 19:20 config-2.6.27-8-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2009-01-04 21:55 grub
-rw-r--r--  1 root root 8195258 2009-01-04 21:37 initrd.img-2.6.27-10-generic
-rw-r--r--  1 root root 8197899 2009-01-04 21:37 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8195211 2009-01-04 21:38 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8194765 2009-01-04 21:38 initrd.img-2.6.27-8-generic
-rw-r--r--  1 root root 8195536 2009-01-04 21:37 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029828 2008-11-21 13:46 System.map-2.6.27-10-generic
-rw-r--r--  1 root root 1031799 2008-12-19 17:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029612 2008-11-06 19:20 System.map-2.6.27-8-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1074 2008-11-21 13:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r--  1 root root    1074 2008-12-19 17:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-06 19:22 vmcoreinfo-2.6.27-8-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2247280 2008-11-21 13:46 vmlinuz-2.6.27-10-generic
-rw-r--r--  1 root root 2248912 2008-12-19 17:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-06 19:20 vmlinuz-2.6.27-8-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 352
drwxr-xr-x 3 root root   4096 2009-01-04 21:55 .
drwxr-xr-x 3 root root   4096 2009-01-04 21:38 ..
-rw-r--r-- 1 root root    197 2009-01-04 21:49 default
-rw-r--r-- 1 root root     15 2008-12-28 04:59 device.map
-rw-r--r-- 1 root root   7444 2009-01-04 21:49 e2fs_stage1_5
-rw-r--r-- 1 root root   7268 2009-01-04 21:49 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 04:59 installed-version
-rw-r--r-- 1 root root   6580 2009-01-04 21:49 iso9660_stage1_5
-rw-r--r-- 1 root root   8064 2009-01-04 21:49 jfs_stage1_5
-rw-r--r-- 1 root root   4505 2009-01-04 21:55 menu.lst
-rw-r--r-- 1 root root   4462 2009-01-04 21:36 menu.lst~
-rw-r--r-- 1 root root   4369 2008-12-28 20:52 menu.lst.backup
-rw-r--r-- 1 1000 1000 127488 2006-07-18 22:12 message.blusplash
-rw-r--r-- 1 root root   6740 2009-01-04 21:49 minix_stage1_5
-rw-r--r-- 1 root root   9012 2009-01-04 21:49 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-30 18:26 splashimages
-rw-r--r-- 1 root root    512 2009-01-04 21:49 stage1
-rw-r--r-- 1 root root 100948 2009-01-04 21:49 stage2
-rw-r--r-- 1 root root   8700 2009-01-04 21:49 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
```

---

### Post by caljohnsmith on 2009-01-04
OK, according to the output, Grub is installed correct to the MBR, and also your partition table is OK now. So if you are still getting a Grub error 2, sometimes that is because of how the HDD is set up in BIOS. How about going into your BIOS and let me know what HDD related settings you have, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, when Grub acts unpredictably in situations like this, sometimes using a different Grub version helps; so how about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), and see if you can use that to boot into Ubuntu. Let me know if that works OK.

---

### Post by winol5 on 2009-01-04
well I dont see anything about HD in my bios exept the star sequency of drives, is that what you mean?, I have run the disk with the fix gnu/linux it makes it{s magic and error 2 again :S

---

### Post by winol5 on 2009-01-04
I'm thinking in reinstalling my entire system... I have acces to the partion files through live cd what should I backup? I have also a virtualbox OS in ubuntu host

---

### Post by caljohnsmith on 2009-01-04
Reinstalling everything may or may not solve the problem, but you can give it a shot if you want. About what to back up, that's totally up to you, but you can't easily back up programs that are installed in Ubuntu (like VirtualBox). Good luck and let me know how it goes.

---

