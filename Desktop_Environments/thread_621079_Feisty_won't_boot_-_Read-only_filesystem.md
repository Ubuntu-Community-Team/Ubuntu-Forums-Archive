---
title: "Feisty won't boot - Read-only filesystem"
date: 2007-11-23
forum: Desktop Environments
---

### Post by NickTheDaemon on 2007-11-23
Feisty won't boot on my PC anymore....  

I have Windows XP installed on the primary sata drive (250Gb) and Feisty Fawn 7;04 installed on the secondary sata drive (40Gb).    I use GRUB to determine which OS to select.     Both XP and Feisty were working fine until I tried running Feisty a few days ago.  Upon booting Feisty, I see a lot of messages stating that certain command (e.g. mkdir, bin/sh) failed because the filesystem is a  "Read-only file system".   The system then tries to create an error log and never really launches.

I've run fsck on the  /dev/sdb1 filesystem, but I still get the same messages.     I've tried selecting the kernel with recovery mode and still get the same error messages.    I even tried a previous kernel with the same results.    Any suggestions besides a reinstall? 

Thanks

Contents of fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=37f6b02c-bc7c-4a48-8dc3-811cdb2869fe none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

Contents of mtab file:

/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Contents of menu.lst

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
# kopt=root=UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash noapic

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=521d5a40-e5ce-45ff-b4e7-26af8c23575f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by banewman on 2007-11-23
If feisty won't boot then how did you get those files to post here?
Did you change the partitions?
What were you doing before the system started not booting?
Obviously more info needed here - please. :)

---

### Post by NickTheDaemon on 2007-11-23
I am able to boot using the Ubuntu CD, but not from the hard drive.     From there I was able to post the mtab, menu.lst and fstab files.     No changes have been made to the partitions or Ubuntu.    This is why I ran the fsck thinking that the hard drive or filesystem was the problem.   On other postings suggested when you see errors=remount-ro it means a problem with the hard drive. 

[http://ubuntuforums.org/showthread.php?t=315850](http://ubuntuforums.org/showthread.php?t=315850)

If you need any other info, please let me know
Thanks

---

### Post by NickTheDaemon on 2007-12-20
I started the ubuntu in recovery mode:

typed in command sudo mount -o remount,rw /   so I could edit files in the filesystem

Changed both mtab and fstab errors=continue

and still the file system comes up in read-only mode.....  so I changed them back.

I saw one of the messages during bootup     mkdir: cannot create directory '/var/run/network' Read only file system.

so I manually created the /var/run/network directory in recovery mode as root, rebooted in recovery mode.  It gets passed this error by I still see others.... such as /var/run/screen..   According to other postings /var/run/network is created by /etc/init.d/loopback on startup

What else besides filesystem or hard drive errors could cause the filesystem to be mounted as read only?

Does anyone know of anything else to try?   Is there a way I can capture the start up log?  


Thanks

---

### Post by khanh_coltech on 2007-12-21
I've a same error.
i can not boot in normal mode.
I started ubuntu in recovery mode, after started "NFS comon utilities", it show:
**Give root password for maintenance or tune control-D to continue.**
I tuned control-D and it boot normally.

---

### Post by smartboyathome on 2007-12-21
> **khanh_coltech said:**
> I've a same error.
i can not boot in normal mode.
I started ubuntu in recovery mode, after started "NFS comon utilities", it show:
**Give root password for maintenance or tune control-D to continue.**
I tuned control-D and it boot normally.

I have that weird error too, but oddly enough it is only on my Toshiba laptop which can't boot to livecd anyway. :lolflag:

---

### Post by khanh_coltech on 2007-12-22
up  ^

---

### Post by Prospero2006 on 2007-12-22
boot the live cd and run fsck -a on the hard drive in question

---

### Post by NickTheDaemon on 2007-12-22
Thank you for the responses.

I booted using the live CD as suggested and unmounted the filesystem 
sudo unmount /dev/sdb1

Then
sudo fsck -a /dev/sdb1  which gave me:
fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 126771/4685824 files, 812857/9357854 blocks

I then ran sudo fsck -rfv /dev/sdb1 which gave me:
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  126771 inodes used (2.71%)
     677 non-contiguous inodes (0.5%)
         # of inodes with ind/dind/tind blocks: 5112/46/0
  812857 blocks used (8.69%)
       0 bad blocks
       1 large file

   98897 regular files
   14420 directories
     133 character device files
      26 block device files
       3 fifos
     384 links
   13270 symbolic links (12174 fast symbolic links)
      13 sockets
--------
  127146 files

  
sudo fdisk -l    

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1196     9606838+   c  W95 FAT32 (LBA)
/dev/sda2   *        1197       30400   234581130    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
[B]/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris[/B]


From what I can tell there doesn't appear to be problems with the filesystem.   This only checks /dev/sdb1 .. does swap need to be checked as well (/dev/sdb5 see contents of fstab file in prior post) or do I have a problem with the startup scripts?    Also, as other posts have suggested to force a fsck by the system, code touch /forcefsck.     I've done that but when Ubuntu starts it I don't see any evidence that it ran a fsck and the forcefsck file created by the touch still exists.  ??

Also, I the last dmesg file created was in November, but I don't see a new one being created.   Possibly because the filesystem is read-only?

Thanks again

---

### Post by NickTheDaemon on 2007-12-28
I figured I spent enough time on this problem and decided for a clean install...

Downloaded the latest version of Ubuntu (Gusty 7.10) and created a live CD.  

Using GParted from the Gutsy CD, I ran a Check on the filesystem (one last time) and no errors were found. 

Using GParted, I saw that only 3.26Gb were being used of the 35.7GB -/dev/sdb1 which contained both root and /home.  So I decided to move the /home directory onto its own partition so that there are any problems in the future I can reinstall again.  Using Resize/Move, I shrunk the root partition to 11.72Gb and created a new partition for the /home directory.  I copied the the data from the old /home directory to the new /home on the newly created partition.

Installed Gutsy, reformated the root partition,  and left the /home and swap as-is.

Every thing appears to be working now.    I wish I could have determined the cause of the read-only filesystem problem.....................

---

### Post by Ux64 on 2008-01-21
> **NickTheDaemon said:**
> I figured I spent enough time on this problem and decided for a clean install...


Let's see, if I spent more than 5 days with this problem. Then I'll do something serous to fix it.

---

