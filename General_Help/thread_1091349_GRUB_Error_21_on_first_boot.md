---
title: "GRUB Error 21 on first boot"
date: 2009-03-09
forum: General Help
---

### Post by yonni on 2009-03-09
Well, I literally just installed Ubuntu Intrpid Ibex on an old Dell Dimension 3000. The hard-disk setup is as follows:

FIRST DRIVE) An 80GB IDE hard disk with the windows XP installation and the rescue partitions that make Dell happy

SECOND DRIVE) A 160GB IDE disk in three partitions:
+ 80GB NTFS that's been there for a while, holding documents, media and the like
+ 1.5GB SWAP for ubuntu (the install wanted me to do it)
+ 78.5GB EXT3 for the Ubuntu install itself.

Everything seemed to be going happily until I tried to reboot after installation when all I get (after BIOS) is "Error 21" from GRUB during stage 1.5, which is fabulous 'cause now I can't get into either Windows or Ubuntu. Hooray! Just what I always wanted! :\

Googling reveals that the error is that GRUB can't find the boot drive (or something along those lines). I've been thinking, this computer has always booted from the first drive, as that's the only one that's ever had an OS on it. The boot order (in BIOS) looks something like: 1) CD-RW Drive, 2) HDD1
So that got me wondering, why doesn't the second drive show up in the boot order anywhere? I know on the back of an IDE drive there's a selector switch which can be set to "Cable Select", "Slave" or "Master", and I was thinking whether having this in the wrong position is stopping my computer from booting?

Maybe it needs to be on "Cable Select"? (not entirely sure what it's on atm)

Also, where would GRUB have installed itself? First or second disk (sorry for any terrible lack of knowledge of bootloaders I may have here)? Presumably if GRUB's starting it must be somewhere on the first disk, but shouldn't it be on the second if that's where I installed Ubuntu?


Finally, is there any way of using the WINDOWS bootloader to dual boot ubuntu and XP? I've dual booted Vista and OpenSUSE before and then GRUB was just a pain in the but too, what's so wrong with the windows bootloader?

Cheers guys, sorry for the essay, just thought you'd want as much information as I have

UPDATE:
Just opened up the case to inspect the drive setup. Appears that the First Disk is connected to the primary IDE ribbon cable with the jumper switch set to "Master", and the Second Disk and the DVD-RW drive are both on the secondary IDE ribbon cable with the jumper switches both set to "Cable Select"
So I'm still unsure as to why the Second disk hasn't shown up in the boot order menu when the DVD-RW drive does :Z

---

### Post by meierfra. on 2009-03-09
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by yonni on 2009-03-09
Here it is, for your viewing pleasure:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   148,874,354   148,761,900   7 HPFS/NTFS
/dev/sda3         148,890,420   156,232,124     7,341,705  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc57d43cf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sdb2         156,280,320   312,576,704   156,296,385   5 Extended
/dev/sdb5         156,280,383   159,284,474     3,004,092  82 Linux swap / Solaris
/dev/sdb6         159,284,538   312,576,704   153,292,167  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 249     3,967,487     3,967,239   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0B03" TYPE="vfat" 
/dev/sda2: UUID="AC30F68030F65136" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: UUID="48DCAF56DCAF3D56" LABEL="MaxtorP1" TYPE="ntfs" 
/dev/sdb5: UUID="584e0a96-4164-4c8d-b83b-3cb3310db123" TYPE="swap" 
/dev/sdb6: UUID="8c6c356b-10a1-496d-839d-a5bbcbc0780e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" UUID="3939-3163" TYPE="vfat" 

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
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8c6c356b-10a1-496d-839d-a5bbcbc0780e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c6c356b-10a1-496d-839d-a5bbcbc0780e

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
uuid		8c6c356b-10a1-496d-839d-a5bbcbc0780e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c6c356b-10a1-496d-839d-a5bbcbc0780e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8c6c356b-10a1-496d-839d-a5bbcbc0780e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c6c356b-10a1-496d-839d-a5bbcbc0780e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8c6c356b-10a1-496d-839d-a5bbcbc0780e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=8c6c356b-10a1-496d-839d-a5bbcbc0780e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=584e0a96-4164-4c8d-b83b-3cb3310db123 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 151.4GB: boot/grub/menu.lst
 151.5GB: boot/grub/stage2
 151.5GB: boot/initrd.img-2.6.27-7-generic
 151.5GB: boot/vmlinuz-2.6.27-7-generic
 151.5GB: initrd.img
 151.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 

```

EDIT:
sdc is the SD card that I connected to transfer files over (the drivers on the live CD don't appear to play ball with my wireless network card)

---

### Post by yonni on 2009-03-09
Ok, the problem must be in the fact that /boot/grub/ doesn't exist (referenced to under sdb6), does anyone know how I fix this when all I have access from is a live CD?

---

### Post by yonni on 2009-03-09
Ok, my bad, /boot/grub/ is there on that disk

---

### Post by meierfra. on 2009-03-09
Judging from RESULTS.txt it seems that grub is configured correctly. 
Is your SD card connected, while you try to boot Ubuntu? Sometimes  extra devices can mess up the boot order and confuse grub.

But  I think there is a problem with the Bios.

> The boot order (in BIOS) looks something like: 1) CD-RW Drive, 2) HDD1

Some bios have a  different place for setting the boot order of the individual hard drives.  Could that be the case with your bios?


You might  try changing some of the  setting in the bios.
Here is a thread with a similar problem:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html]("http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html")

If none of this leads to anything, I can show you how to restore the XP boot loader and add Ubuntu to the XP boot loader.

---

### Post by yonni on 2009-03-09
FIXED!

For other's reference, here's how I did it (details obviously change between BIOSs, but the general idea/terminology might be the same)

Poking around in the bios a bit more, there's a section for "Hard-Disk Drive Sequence" for which I get to order "System BIOS boot devices" and "USB device (not installed)", not much help there
There's also a "Drive Configuration" section. This identifies teh "Primary Master Drive" (my windows install drive), "Primary Slave Drive" (none), "Secondary Master Drive" (CD-ROM drive) and "Secondary Slave Drive"

I changed the "Secondary Slave Drive" (since the drive with ubuntu on is on the second connector of the secondary IDE cable) from "None" to "Auto" (at which it read "unknown device") after a restart it now reads "Hard drive" and GRUB works fine :)

Cheers guys for all of your help

---

### Post by meierfra. on 2009-03-09
> FIXED!

Good News.  Have fun with XP and Ubunutu. 
And thanks for letting us know how you solved the problem.

---

