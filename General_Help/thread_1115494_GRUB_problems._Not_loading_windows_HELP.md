---
title: "GRUB problems. Not loading windows HELP"
date: 2009-04-03
forum: General Help
---

### Post by iliveinthedark on 2009-04-03
So I thought I'd be smart and try to expand one of my partitions by deleting one that i dont use and adding it to another. Neither of these partitions that i tried to play with contained either my filesystem or windows. I was not able to do anything except delete a partition and convert it to unallocated space. i realize it has something to do with using  a live cd... ANYWAY

I cant start up windows now. The drive and everything i need is still there. I can access it from ubuntu. I tried everything. I'm at wits end. i keep getting error 12. I've tried editing menu.lst, using the super grub program thing that i couldnt get to load on a usb drive. I tried following numerous instructionals with no result. 

I even managed to screw up my xserver and now no graphics work on my intrepid which i'm sure i can fix later but I need to use windows here within a couple days due to work.

Here's my menu.lst 

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1



my fdisk:

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          64      514048+  83  Linux
/dev/sda2              65        6721    53472352+   5  Extended
/dev/sda3            6722        6852     1052257+  82  Linux swap / Solaris
/dev/sda5              65        2022    15727603+   7  HPFS/NTFS
/dev/sda6            2023        3980    15727603+  83  Linux
/dev/sda7            3981        6721    22017051    7  HPFS/NTFS

Disk /dev/sdb: 995 MB, 995474944 bytes
4 heads, 8 sectors/track, 60758 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60759      972139+   e  W95 FAT16 (LBA)



anyone??

---

### Post by 3Miro on 2009-04-03
Attempt one:

Backup your grub/menu.lst file, and edit it:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_mybackup
sudo pico /boot/grub/menu.lst

```

Now go to the windows section and try changing
```
root (hd0,4)
```
to either 3, 5, 6, 7. Someone with more knowledge than me can guess the right one without trying (I would try 3 first).

Now comes the bad news (I really hope you don't get that problem, but you might). After Grub, windows starts its own boot-loader and it might be messed up again. Once I had to edit the:
```
C:\boot.ini
```
file on my windows, but I cannot remember what the deal was. (back it up in either case) Windows uses another partition naming scheme and I cannot tell you how exactly it works.

---

### Post by iliveinthedark on 2009-04-03
None of those worked. I had tried them before, and i just tried them again from the grub loader editor during startup. I got error 12 - invalid something or another again and again.

my thoughts- it's not recognizing the start up files for windows. But i have no idea how to continue on the hypothesis. 

I'll edit whatever i need from any file. I really need windows.

---

### Post by 3Miro on 2009-04-03
Can you mount the windows partition, I hope it is not corrupt.

---

### Post by iliveinthedark on 2009-04-03
Yes. I can mount it. I can access and edit all the files and everything on it.

---

### Post by meierfra. on 2009-04-03
It looks like you deleted or formated the partition containing the  XP boot files.

To fix your problem follow this [tutorial]("http://ubuntuforums.org/showthread.php?t=813628")

In Step 1 use /dev/sda5  

In Step 3 use partition(3)

In Step 4 use 

title XP
rootnoverify (hd0,4)
chainloader +1

---

### Post by iliveinthedark on 2009-04-03
That made a noticeable difference. I now don't see any error. Except it just freezes at the "Starting Up" text screen.

In my Windows partition, there are two different NTLDR files. one with lower case and one with uppercase. the upper case is the newer one that came with the new NTDETECT.COM file. I'll try restarting with one or the other.

---

### Post by meierfra. on 2009-04-03
```
Except it just freezes at the "Starting Up" text screen.
```

That means you have to do the last step (step 5) from the tutorial.

---

### Post by iliveinthedark on 2009-04-03
When i do this, i enter Rebuild BS and the only options given to me are [dump], [list], and [quit] there is no write option

---

### Post by meierfra. on 2009-04-03
> When i do this, i enter Rebuild BS and the only options given to me are [dump][list] and [quit] there is no write option

Strange. That means that your boot sector is correct. But the "starting up" usually is a sure sign for a corrupted boot sector.

I don't think that the two ntldrs could cause "a starting up" error, but I still suggest to rename one of them.

Also lets  have a closer look at your system:

 download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by iliveinthedark on 2009-04-04
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders, total 114270345 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     1,028,159     1,028,097  83 Linux
/dev/sda2           1,028,160   107,972,864   106,944,705   5 Extended
/dev/sda5           1,028,223    32,483,429    31,455,207   7 HPFS/NTFS
/dev/sda6          32,483,493    63,938,699    31,455,207  83 Linux
/dev/sda7          63,938,763   107,972,864    44,034,102   7 HPFS/NTFS
/dev/sda3         107,972,865   110,077,379     2,104,515  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 995 MB, 995474944 bytes
4 heads, 8 sectors/track, 60758 cylinders, total 1944287 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              8     1,944,286     1,944,279   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5a98797d-a028-4e9a-b8f7-0c2bca9ecef9" TYPE="ext3" 
/dev/sda3: UUID="c55c21c4-91e0-4420-9e4c-e6ed3630784c" TYPE="swap" 
/dev/sda5: UUID="472A32C065EEA086" LABEL="Windows" TYPE="ntfs" 
/dev/sda6: UUID="32110098-9cc9-49cd-93a7-a3e7bce9310a" TYPE="ext3" 
/dev/sda7: UUID="6F0B0E891285A5E0" LABEL="Documents" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" UUID="5924-DC83" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/sda1 type ext3 (rw,relatime)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joe)
/dev/scd1 on /media/U3 System type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=a5f6dd20-d14d-49d5-8ffd-f0d1c4d712de ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=a5f6dd20-d14d-49d5-8ffd-f0d1c4d712de ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=a5f6dd20-d14d-49d5-8ffd-f0d1c4d712de ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/menu.lst
    .2GB: grub/stage2
    .0GB: initrd.img-2.6.22-14-generic
    .0GB: initrd.img-2.6.22-14-generic.bak
    .0GB: vmlinuz-2.6.22-14-generic

================================ sda5/boot.ini: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(3)\Windows

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(3)\Windows="Windows XP" /fastdetect




=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		XP
rootnoverify	(hd0,4)
chainloader	+1

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=32110098-9cc9-49cd-93a7-a3e7bce9310a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=5a98797d-a028-4e9a-b8f7-0c2bca9ecef9 /media/sda1     ext3    defaults,relatime        0       2
# /dev/sda4
UUID=0FEE34A352C4ABE9 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=472A32C065EEA086 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=6F0B0E891285A5E0 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=c55c21c4-91e0-4420-9e4c-e6ed3630784c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

=================== sda6: Location of files loaded by Grub: ===================


  18.1GB: boot/grub/menu.lst
  18.1GB: boot/grub/stage2
  18.2GB: boot/initrd.img-2.6.22-14-generic
  18.2GB: boot/initrd.img-2.6.22-14-generic.bak
  18.1GB: boot/initrd.img-2.6.24-19-generic
  18.1GB: boot/initrd.img-2.6.24-19-generic.bak
  18.2GB: boot/initrd.img-2.6.27-11-generic
  18.1GB: boot/initrd.img-2.6.27-7-generic
  18.2GB: boot/initrd.img-2.6.27-9-generic
  18.2GB: boot/vmlinuz-2.6.22-14-generic
  18.1GB: boot/vmlinuz-2.6.24-19-generic
  18.1GB: boot/vmlinuz-2.6.27-11-generic
  18.1GB: boot/vmlinuz-2.6.27-7-generic
  18.2GB: boot/vmlinuz-2.6.27-9-generic
  18.2GB: initrd.img
  18.2GB: initrd.img.old
  18.1GB: vmlinuz
  18.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 20 01 00  |.<.DOK01.02.. ..|
00000010  02 00 02 00 00 f8 ee 00  08 00 04 00 08 00 00 00  |................|
00000020  d7 aa 1d 00 80 01 29 83  dc 24 59 00 00 00 00 00  |......)..$Y.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


```

---

### Post by meierfra. on 2009-04-04
I can't find anything wrong.  Did you just install Ubuntu? Did you deleted or format any fat or ntfs partition during the installation?  Or did you clone the XP partition?  I'm a little puzzled why you would have an "ntldr" file on your XP partition.

But I still think there is something wrong with the extended XP boot sector. (testdisk only checks for certain errors) So lets see what  happens if we replace  the whole extended boot sector:
Download the attached file "XP_nine.txt" to your desktop. Open a terminal
and type


```
 sudo dd if=~/Desktop/XP_nine.txt of=/dev/sda5 bs=1 seek=80 skip=80

```

Be very careful with the "dd" command. If it runs for more than just a couple of seconds, stop the process with "ctrl+C".

---

### Post by iliveinthedark on 2009-04-04
These are the results:

4528+0 records in
4528+0 records out
4528 bytes (4.5 kB) copied, 0.0209573 s, 216 kB/s


I installed ubuntu november of 2007. It was part of a huge repartitioning of the harddrive. I recently tried to delete an ntfs partition that was created during that repartitioning for the re-installation of Dell Media Center, which never occurred. 

The fat drive that keeps being listed as sdb1 is my thumbdrive.i tried to load a super grub program on it. I could never get it to work.

---

### Post by meierfra. on 2009-04-04
Ok. Reboot and try to boot  XP.

---

### Post by iliveinthedark on 2009-04-04
Well, i must have mega-effed my 3d card by going into ubuntu recovery earlier today because it wont work in windows now. but i got in.

Thank you for all your work on this problem. if i could give you a credit rating, it would be a good one.

---

### Post by meierfra. on 2009-04-04
> but i got in.

Great.  
There have been many people who used the same   tutorial, but this is the first time that the whole extended boot sector had to be replaced.  
Maybe  there is something wrong with your XP partition.  You might consider running "chkdsk /r C:" in the Windows command line.

What are you using /dev/sda1 for?  It looks like it used to be a boot partition, but you are not using it as boot partition anymore. 


Good luck with your 3d card.

---

### Post by iliveinthedark on 2009-04-05
I believe it was supposed to be my boot partition. My buddy who's partition logic i was following must not have noticed it wasn't being used.

I'll have to try to find tutorial to correctly reconfigure my partitions without disrupting any boot processes or deleting any data.

---

### Post by meierfra. on 2009-04-05
> I'll have to try to find tutorial to correctly reconfigure my partitions without disrupting any boot processes or deleting any data.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

