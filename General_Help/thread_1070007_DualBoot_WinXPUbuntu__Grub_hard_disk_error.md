---
title: "DualBoot WinXP/Ubuntu : Grub hard disk error"
date: 2009-02-14
forum: General Help
---

### Post by StephGbzh on 2009-02-14
Hi everyone,

Today I tried to make my Grub menu sexier by installing grub-gfxboot on my dual boot system WinXP/Ubuntu. I somehow screwed up things and then managed to get part of my system back. I now need help to restore "bootability" of the Windows part.

What works : grub with nice background and fonts + booting Ubuntu from there.

What does not work : booting Windows XP.

I get this when trying to boot Win :
```

root (hd0,0)
  Filesystem type unknown, partition type 0x7
makeactive
chainloader +1

Grub HARD DISK ERROR
```

I suspect this command line to be the cause of this mess :

sudo grub-install /dev/sda

GParted can see all partitions correctly, even if the "Used" size of win partition is wrong : 3.30 Gb instead of 20Gb. Dolphin, however, can access all files and finds the correct size of 20Gb when asked (select all files, right click, Properties).

I already tried TestDisk (it repaired boot sector and so I got Ubuntu back), Super Grub Disk (did not really have much success with it) and Windows Recovery Console CD (chkdsk does not want to even *try* anything) to no avail.

Please help!

Here is the result of "sudo fdisk -l" :

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12551254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        8746    29294527+  83  Linux
/dev/sda3            8747       50052   331790445    f  W95 Ext'd (LBA)
/dev/sda5            8747       11178    19535008+  83  Linux
/dev/sda6           11179       11421     1951866   82  Linux swap / Solaris
/dev/sda7           11422       24298   103434471    7  HPFS/NTFS
/dev/sda8           24299       37175   103434471    7  HPFS/NTFS
/dev/sda9           37176       50052   103434471    7  HPFS/NTFS
```

And here is the result of boot_info_script024.sh :

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12551254

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   140,504,489    58,589,055  83 Linux
/dev/sda3         140,504,490   804,085,379   663,580,890   f W95 Ext d (LBA)
/dev/sda5         140,504,553   179,574,569    39,070,017  83 Linux
/dev/sda6         179,574,633   183,478,364     3,903,732  82 Linux swap / Solaris
/dev/sda7         183,478,428   390,347,369   206,868,942   7 HPFS/NTFS
/dev/sda8         390,347,433   597,216,374   206,868,942   7 HPFS/NTFS
/dev/sda9         597,216,438   804,085,379   206,868,942   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80C2F69090FA0800" LABEL="Edo" TYPE="ntfs" 
/dev/sda2: UUID="001c2698-4471-43de-94e2-0fab14fd5a30" TYPE="ext3" 
/dev/sda5: UUID="bff0d832-9fba-43bf-8e95-89ead8376920" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="c96c9ab7-452b-4a6a-b99d-e19d66ebd9c5" 
/dev/sda7: UUID="5EEF5DF820930BFB" LABEL="Alexandrie" TYPE="ntfs" 
/dev/sda8: UUID="0D407AC95621B5A1" LABEL="Byzance" TYPE="ntfs" 
/dev/sda9: UUID="5A401F141BB32DDC" LABEL="Tenochtitlan" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda8 on /media/Byzance type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/Alexandrie type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Edo type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /media/Tenochtitlan type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stephane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephane)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut

=========================== sda2/boot/grub/menu.lst: ===========================

gfxmenu /boot/grub/message

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
# kopt=root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root




=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=001c2698-4471-43de-94e2-0fab14fd5a30 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=bff0d832-9fba-43bf-8e95-89ead8376920 /home ext3 relatime 0 2
# Entry for /dev/sda6 :
UUID=c96c9ab7-452b-4a6a-b99d-e19d66ebd9c5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/Byzance ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda7 /media/Alexandrie ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda1 /media/Edo ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda9 /media/Tenochtitlan ntfs-3g defaults,locale=fr_FR.UTF-8 0 0

=================== sda2: Location of files loaded by Grub: ===================


  47.0GB: boot/grub/menu.lst
  47.1GB: boot/grub/stage2
  44.3GB: boot/initrd.img-2.6.24-23-generic
  44.2GB: boot/initrd.img-2.6.24-23-generic.bak
  44.3GB: boot/initrd.img-2.6.27-11-generic
  44.2GB: boot/initrd.img-2.6.27-9-generic
  44.3GB: boot/vmlinuz-2.6.24-23-generic
  44.3GB: boot/vmlinuz-2.6.27-11-generic
  44.2GB: boot/vmlinuz-2.6.27-9-generic
  44.3GB: initrd.img
  44.2GB: initrd.img.old
  44.3GB: vmlinuz
  44.2GB: vmlinuz.old 
```

If anybody has a clue about how I can make all this work again, please do not hesitate!
Even a total rollback to plain black and white grub menu would be accepted if it can dual boot :)

Stephane

---

### Post by olskar on 2009-02-14
> **StephGbzh said:**
> Hi everyone,

Today I tried to make my Grub menu sexier by installing grub-gfxboot on my dual boot system WinXP/Ubuntu. I somehow screwed up things and then managed to get part of my system back. I now need help to restore "bootability" of the Windows part.

What works : grub with nice background and fonts + booting Ubuntu from there.

What does not work : booting Windows XP.

I get this when trying to boot Win :
```

root (hd0,0)
  Filesystem type unknown, partition type 0x7
makeactive
chainloader +1

Grub HARD DISK ERROR
```

I suspect this command line to be the cause of this mess :

sudo grub-install /dev/sda

GParted can see all partitions correctly, even if the "Used" size of win partition is wrong : 3.30 Gb instead of 20Gb. Dolphin, however, can access all files and finds the correct size of 20Gb when asked (select all files, right click, Properties).

I already tried TestDisk (it repaired boot sector and so I got Ubuntu back), Super Grub Disk (did not really have much success with it) and Windows Recovery Console CD (chkdsk does not want to even *try* anything) to no avail.

Please help!

Here is the result of "sudo fdisk -l" :

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12551254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        8746    29294527+  83  Linux
/dev/sda3            8747       50052   331790445    f  W95 Ext'd (LBA)
/dev/sda5            8747       11178    19535008+  83  Linux
/dev/sda6           11179       11421     1951866   82  Linux swap / Solaris
/dev/sda7           11422       24298   103434471    7  HPFS/NTFS
/dev/sda8           24299       37175   103434471    7  HPFS/NTFS
/dev/sda9           37176       50052   103434471    7  HPFS/NTFS
```

And here is the result of boot_info_script024.sh :

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12551254

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   140,504,489    58,589,055  83 Linux
/dev/sda3         140,504,490   804,085,379   663,580,890   f W95 Ext d (LBA)
/dev/sda5         140,504,553   179,574,569    39,070,017  83 Linux
/dev/sda6         179,574,633   183,478,364     3,903,732  82 Linux swap / Solaris
/dev/sda7         183,478,428   390,347,369   206,868,942   7 HPFS/NTFS
/dev/sda8         390,347,433   597,216,374   206,868,942   7 HPFS/NTFS
/dev/sda9         597,216,438   804,085,379   206,868,942   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80C2F69090FA0800" LABEL="Edo" TYPE="ntfs" 
/dev/sda2: UUID="001c2698-4471-43de-94e2-0fab14fd5a30" TYPE="ext3" 
/dev/sda5: UUID="bff0d832-9fba-43bf-8e95-89ead8376920" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="c96c9ab7-452b-4a6a-b99d-e19d66ebd9c5" 
/dev/sda7: UUID="5EEF5DF820930BFB" LABEL="Alexandrie" TYPE="ntfs" 
/dev/sda8: UUID="0D407AC95621B5A1" LABEL="Byzance" TYPE="ntfs" 
/dev/sda9: UUID="5A401F141BB32DDC" LABEL="Tenochtitlan" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda8 on /media/Byzance type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/Alexandrie type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Edo type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /media/Tenochtitlan type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stephane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephane)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut

=========================== sda2/boot/grub/menu.lst: ===========================

gfxmenu /boot/grub/message

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
# kopt=root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=001c2698-4471-43de-94e2-0fab14fd5a30 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root




=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=001c2698-4471-43de-94e2-0fab14fd5a30 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=bff0d832-9fba-43bf-8e95-89ead8376920 /home ext3 relatime 0 2
# Entry for /dev/sda6 :
UUID=c96c9ab7-452b-4a6a-b99d-e19d66ebd9c5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda8 /media/Byzance ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda7 /media/Alexandrie ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda1 /media/Edo ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/sda9 /media/Tenochtitlan ntfs-3g defaults,locale=fr_FR.UTF-8 0 0

=================== sda2: Location of files loaded by Grub: ===================


  47.0GB: boot/grub/menu.lst
  47.1GB: boot/grub/stage2
  44.3GB: boot/initrd.img-2.6.24-23-generic
  44.2GB: boot/initrd.img-2.6.24-23-generic.bak
  44.3GB: boot/initrd.img-2.6.27-11-generic
  44.2GB: boot/initrd.img-2.6.27-9-generic
  44.3GB: boot/vmlinuz-2.6.24-23-generic
  44.3GB: boot/vmlinuz-2.6.27-11-generic
  44.2GB: boot/vmlinuz-2.6.27-9-generic
  44.3GB: initrd.img
  44.2GB: initrd.img.old
  44.3GB: vmlinuz
  44.2GB: vmlinuz.old 
```

If anybody has a clue about how I can make all this work again, please do not hesitate!
Even a total rollback to plain black and white grub menu would be accepted if it can dual boot :)

Stephane

Can this help?
[http://www.linuxquestions.org/questions/linux-newbie-8/dual-boot-problem-partition-tables-bad-204807/?highlight=Search+For](http://www.linuxquestions.org/questions/linux-newbie-8/dual-boot-problem-partition-tables-bad-204807/?highlight=Search+For)...

---

### Post by caljohnsmith on 2009-02-14
[QUOTE=StephGbzh]```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  [COLOR="Red"]Grub0.97 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

```[/QUOTE]
Looks like the problem is you accidentally installed Grub to the boot sector of your Windows partition. In order to fix it, how about booting your Windows Install CD, go to the "recovery console" and do:
```
fixboot
```
Then I think you should be fine, but let me know if you run into problems.

---

### Post by StephGbzh on 2009-02-15
@olskar : I tried to follow your link but the acclaimed solution in this thread points to a dead link on SuSe database, rather frustrating... thanks anyway

@caljohnsmith : I did what you suggest but fixboot wont work, I get this :
```
fixboot cannot find the system drive or the drive specified is not valid.
```

Then I tried chkdsk :
```
volume appears to contain one or more unrecoverable problems
```

And finally diskpart which shows only a C: partition with a size of 131072 Mb. My HD has a size of 640 Gb and no partition I made is 128 Gb. 
Could it be that the Windows XP CD I use has some sort of old Recovery Console that can't manage HD with a size of more than 128 Gb?

Thanks for your help

---

### Post by caljohnsmith on 2009-02-15
OK, from your Windows XP CD, how about before doing "fixboot", do:
```
map
```
That will show you the drive letters for all your partitions. Once you know the drive letter for the sda1 partition (for example "C"), then try:
```
fixboot C:
```
And do you still get an error?

---

### Post by StephGbzh on 2009-02-15
Well, I did this and "fixboot C:" worked much better than "fixboot" alone :-)

Anyway after reboot, I get a new message :

```
NTLDR is missing
```

and my computer sits there.

So I am posting from Ubuntu Live CD now and I am rather scared to have lost everything because GParted can now not see the partitions anymore! Only a big fat16 /dev/sda1 of 596.17 Gb...

Please tell me there is a way to get all this back!

---

### Post by caljohnsmith on 2009-02-15
That's not good, it sounds like fixboot may have done more harm than good for some reason. How about rerunning the Boot Info Script from your Live CD and posting the results again. That should hopefully give me enough enough to figure what happened to your system.

---

### Post by StephGbzh on 2009-02-15
Here it is :

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69737369

Partition  Boot         Start           End          Size  Id System

/dev/sda1     ? 1,869,771,365 2,038,460,886   168,689,522  69 Unknown
/dev/sda2     ? 1,701,519,481 3,571,400,945 1,869,881,465  73 Unknown
/dev/sda4                   0 3,435,113,471 3,435,113,472   0 Empty

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 08 01 00  |.<.MSDOS5.0.....|
00000010  02 00 02 03 51 f8 08 00  11 00 04 00 01 00 00 00  |....Q...........|
00000020  00 00 00 00 80 00 29 00  00 00 00 4e 4f 20 4e 41  |......)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 33 c9  |ME    FAT12   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c 01 72 1c 83 eb 3a  |8N$}$....<.r...:|
00000060  66 a1 1c 7c 26 66 3b 07  26 8a 57 fc 75 06 80 ca  |f..|&f;.&.W.u...|
00000070  02 88 56 02 80 c3 10 73  eb 33 c9 8a 46 10 98 f7  |..V....s.3..F...|
00000080  66 16 03 46 1c 13 56 1e  03 46 0e 13 d1 8b 76 11  |f..F..V..F....v.|
00000090  60 89 46 fc 89 56 fe b8  20 00 f7 e6 8b 5e 0b 03  |`.F..V.. ....^..|
000000a0  c3 48 f7 f3 01 46 fc 11  4e fe 61 bf 00 00 e8 e6  |.H...F..N.a.....|
000000b0  00 72 39 26 38 2d 74 17  60 b1 0b be a1 7d f3 a6  |.r9&8-t.`....}..|
000000c0  61 74 32 4e 74 09 83 c7  20 3b fb 72 e6 eb dc a0  |at2Nt... ;.r....|
000000d0  fb 7d b4 7d 8b f0 ac 98  40 74 0c 48 74 13 b4 0e  |.}.}....@t.Ht...|
000000e0  bb 07 00 cd 10 eb ef a0  fd 7d eb e6 a0 fc 7d eb  |.........}....}.|
000000f0  e1 cd 16 cd 19 26 8b 55  1a 52 b0 01 bb 00 00 e8  |.....&.U.R......|
00000100  3b 00 72 e8 5b 8a 56 24  be 0b 7c 8b fc c7 46 f0  |;.r.[.V$..|...F.|
00000110  3d 7d c7 46 f4 29 7d 8c  d9 89 4e f2 89 4e f6 c6  |=}.F.)}...N..N..|
00000120  06 96 7d cb ea 03 00 00  20 0f b6 c8 66 8b 46 f8  |..}..... ...f.F.|
00000130  66 03 46 1c 66 8b d0 66  c1 ea 10 eb 5e 0f b6 c8  |f.F.f..f....^...|
00000140  4a 4a 8a 46 0d 32 e4 f7  e2 03 46 fc 13 56 fe eb  |JJ.F.2....F..V..|
00000150  4a 52 50 06 53 6a 01 6a  10 91 8b 46 18 96 92 33  |JRP.Sj.j...F...3|
00000160  d2 f7 f6 91 f7 f6 42 87  ca f7 76 1a 8a f2 8a e8  |......B...v.....|
00000170  c0 cc 02 0a cc b8 01 02  80 7e 02 0e 75 04 b4 42  |.........~..u..B|
00000180  8b f4 8a 56 24 cd 13 61  61 72 0b 40 75 01 42 03  |...V$..aar.@u.B.|
00000190  5e 0b 49 75 06 f8 c3 41  bb 00 00 60 66 6a 00 eb  |^.Iu...A...`fj..|
000001a0  b0 4e 54 4c 44 52 20 20  20 20 20 20 0d 0a 4e 54  |.NTLDR      ..NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 ac bf cc 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
./boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
./boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
./boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2009-02-15
My gosh, that's terrible; the "fixboot" command somehow messed up and overwrote your MBR (Master Boot Record) which also contains the partition table. Fortunately we have the previous results from the Boot Info Script that you posted, so we can reconstruct your partition table. How about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Next be sure to reboot your Live CD, and then post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
And we can work from there.

---

### Post by StephGbzh on 2009-02-15
Here is what I get with the first command:

```
ubuntu@ubuntu:~/Desktop$ sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt

Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   ? 116387+ 126888-  10501-  84344761   69  Unknown
		start: (c,h,s) expected (1023,254,63) found (68,13,10)
		end: (c,h,s) expected (1023,254,63) found (288,115,43)
/dev/sda2   ? 105914+ 222309- 116395- 934940732+  73  Unknown
		start: (c,h,s) expected (1023,254,63) found (371,114,37)
		end: (c,h,s) expected (1023,254,63) found (366,32,33)
/dev/sda3   ?      0+      0-      0          0   74  Unknown
/dev/sda4          0  213825- 213826- 1717556736    0  Empty
		start: (c,h,s) expected (0,0,1) found (0,0,0)
		end: (c,h,s) expected (1023,254,63) found (0,0,0)
cannot build surrounding extended partition

sfdisk: bad input
ubuntu@ubuntu:~/Desktop$ 

```

Given the result, should I still do the commands you suggest after this?

Something strange is this : "blocks of 1024 bytes" whereas yesterday with the working drive, I had "Units = cylinders of 16065 * 512 = 8225280 bytes". All other figures match except this block size.

Anyway "sudo fdisk -l" gives this :

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by caljohnsmith on 2009-02-15
My mistake, sorry about that; I was on my way out for a little while so I put together the partition_table.txt file a little too quickly and gave the wrong number for your sda8 partition size. I corrected it and uploaded the new version to my previous post. Please download it and try again.

---

### Post by StephGbzh on 2009-02-15
Wow man, I thought you were trying to find a nice way to tell me everything was lost :lolflag:
Just kidding, thanks for your help and patience!

Anyway, this time the command worked much better, here is the output :

```
ubuntu@ubuntu:~/Desktop$ sudo sfdisk --no-reread /dev/sda < ~/Desktop/partition_table.txt

Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   ? 116387+ 126888-  10501-  84344761   69  Unknown
		start: (c,h,s) expected (1023,254,63) found (68,13,10)
		end: (c,h,s) expected (1023,254,63) found (288,115,43)
/dev/sda2   ? 105914+ 222309- 116395- 934940732+  73  Unknown
		start: (c,h,s) expected (1023,254,63) found (371,114,37)
		end: (c,h,s) expected (1023,254,63) found (366,32,33)
/dev/sda3   ?      0+      0-      0          0   74  Unknown
/dev/sda4          0  213825- 213826- 1717556736    0  Empty
		start: (c,h,s) expected (0,0,1) found (0,0,0)
		end: (c,h,s) expected (1023,254,63) found (0,0,0)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  81915434   81915372   7  HPFS/NTFS
/dev/sda2      81915435 140504489   58589055  83  Linux
/dev/sda3     140504490 804085379  663580890   f  W95 Ext'd (LBA)
/dev/sda4             0         -          0   0  Empty
/dev/sda5     140504553 179574569   39070017  83  Linux
/dev/sda6     179574633 183478364    3903732  82  Linux swap / Solaris
/dev/sda7     183478428 390347369  206868942   7  HPFS/NTFS
/dev/sda8     390347433 597216374  206868942   7  HPFS/NTFS
/dev/sda9     597216438 804085379  206868942   7  HPFS/NTFS
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~/Desktop$
```

And yes, we come back to the right partition table!

I post this and will reboot on the Live CD and execute the commands you gave me. See you in a few minutes!

---

### Post by StephGbzh on 2009-02-15
Let's go!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   140504489    29294527+  83  Linux
/dev/sda3       140504490   804085379   331790445    f  W95 Ext'd (LBA)
/dev/sda5       140504553   179574569    19535008+  83  Linux
/dev/sda6       179574633   183478364     1951866   82  Linux swap / Solaris
/dev/sda7       183478428   390347369   103434471    7  HPFS/NTFS
/dev/sda8       390347433   597216374   103434471    7  HPFS/NTFS
/dev/sda9       597216438   804085379   103434471    7  HPFS/NTFS
```

```
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 81915372, Id= 7, bootable
/dev/sda2 : start= 81915435, size= 58589055, Id=83
/dev/sda3 : start=140504490, size=663580890, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=140504553, size= 39070017, Id=83
/dev/sda6 : start=179574633, size=  3903732, Id=82
/dev/sda7 : start=183478428, size=206868942, Id= 7
/dev/sda8 : start=390347433, size=206868942, Id= 7
/dev/sda9 : start=597216438, size=206868942, Id= 7
```

```

ubuntu@ubuntu:~$ sudo parted /dev/sda print

Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End    Size   File system  Flags
 1      0,00kB  640GB  640GB  fat16             

Information: Don't forget to update /etc/fstab, if necessary.             

```

Oops, I don't like this last result.
Should I go on with the grub commands?

```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```

Here is the content of /etc/fstab :

```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
```

---

### Post by caljohnsmith on 2009-02-15
That's strange about the parted command, I hope I didn't miss something again with your partition table. Does the following command give the same result:
```
sudo parted -l
```
Note it is a small L, not a one. Also, go ahead and try the Grub commands and please post the results.

---

### Post by StephGbzh on 2009-02-15
As parted is in version 1.7.1 on my Ubuntu Live CD, this option -l does not exist. :-(

Here is the result of grub commands :

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2009-02-15
OK, don't worry about the parted command for now then; please reboot and let me know if you can at least boot into Ubuntu. We can work from there.

---

### Post by StephGbzh on 2009-02-15
YES!!!
Back to Ubuntu on my HD.
Windows still not bootable though.

The only diff in boot_info_script024.sh between yesterday and now is the the "Disk identifier".

```
diff RESULTS1.txt RESULTS2.txt
78c78
< Disk identifier: 0x12551254
---
> Disk identifier: 0x69737369
```

---

### Post by caljohnsmith on 2009-02-15
OK, let's try using "testdisk" to see if your sda1 Windows partition has a valid backup boot sector to use to fix the current boot sector. First make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda1 Windows partition, choose "Boot", then choose "Backup BS"; if testdisk gives you a warning that the boot sectors are not identical, then choose "Write". Let me know if testdisk lets you get that far, and if so, try booting Windows from Grub and let me know exactly what happens.

---

### Post by StephGbzh on 2009-02-15
OK, I launched TestDisk but instead of "Backup BS", I get "Rebuild BS" :

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  5098 254 63   81915372 [Edo]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                              Rebuild boot sector
```

So let's go for this "Rebuild BS" :

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  5098 254 63   81915372 [Edo]

filesystem size           81915372
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               5119710
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]

                           List directories and files
```

I can't do anything on this Boot Sector it seems. TestDisk thinks it's already OK.

---

### Post by meierfra. on 2009-02-15
caljohnsmith asked me to jump in, since he does not have access to the the relevant boot files right now. Download the attached file "XP_nine.txt" to your Desktop. Open a terminal and type

```
cd ~/Desktop
sudo dd if=XP_nine.txt of=/dev/sda1 bs=1 seek=80 skip=80
```

Reboot and hope for the best.

---

### Post by StephGbzh on 2009-02-15
Victory!

I am currently posting from my recovered Windows XP session!

Many thanks to both of you caljohnsmith and meierfra. for your patience, knowledge and dedication.

The dual boot is now fully functional again and as the icing on the cake, grub now has a beautiful background! :guitar:

As a note :
Windows tried to scare me one last time by saying it installed a new hardware and asking for a reboot. I think it is linked to the fact I mentioned earlier : the Disk Identifier changed.
So I rebooted and then it started a chkdsk which removed thousands of orphan files, recovered others and so on during 10 minutes.
Finally it started again and I think it is the last word of this story.

Thanks again!

PS : I don't know if/how I can add [SOLVED] to this thread title so feel free to do it for me.

---

### Post by caljohnsmith on 2009-02-15
That's great news, glad you can boot Windows again. Cheers and enjoy Ubuntu and Windows. :)

---

