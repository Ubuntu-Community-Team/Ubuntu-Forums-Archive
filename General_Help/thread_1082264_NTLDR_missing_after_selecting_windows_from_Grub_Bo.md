---
title: "NTLDR missing after selecting windows from Grub Boot menu"
date: 2009-02-27
forum: General Help
---

### Post by SheikhAmanAlam on 2009-02-27
here's my RESULT.txt file which John had asked me to put here.

i hope it gives sufficient info-

> 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM /wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 28878386 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09550954

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       530,144       530,082  82 Linux swap / Solaris
/dev/sda2             530,145   321,653,429   321,123,285   f W95 Ext d (LBA)
/dev/sda5             530,208    23,438,834    22,908,627   7 HPFS/NTFS
/dev/sda6    *     23,438,898    41,945,714    18,506,817  83 Linux
/dev/sda7          41,945,778   146,801,969   104,856,192   7 HPFS/NTFS
/dev/sda8         146,802,033   205,519,544    58,717,512   7 HPFS/NTFS
/dev/sda9         205,519,608   257,955,704    52,436,097   7 HPFS/NTFS
/dev/sda10        257,955,768   321,653,429    63,697,662   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897087 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,897,086     7,897,024   b W95 FAT32

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,948,542     3,948,480   b W95 FAT32

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AE58E4EF58E4B76D" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="C07823CE7823C1D0" LABEL="SysDisc" TYPE="ntfs" 
/dev/sda6: UUID="7c5bef73-f1db-465f-b71d-7ecc6b551336" TYPE="ext3" 
/dev/sda7: UUID="EA543D1E543CEEC7" LABEL="Installed" TYPE="ntfs" 
/dev/sda8: UUID="98ECD2D0ECD2A830" LABEL="Docs & Music" TYPE="ntfs" 
/dev/sda9: UUID="18B0E11BB0E0FFDC" LABEL="Videos & Photoes" TYPE="ntfs" 
/dev/sda10: UUID="4064EEE164EED924" LABEL="Uninstalled" TYPE="ntfs" 
/dev/sdb1: LABEL="THE_ORACLE" UUID="4031-C652" TYPE="vfat" 
/dev/sdc1: LABEL="ARSHI" UUID="84A4-B5D7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/installed type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda8 on /media/documents type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda9 on /media/videos+photos type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda10 on /media/uninstalled type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sheikhaman/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sheikhaman)
/dev/sdb1 on /media/THE_ORACLE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/ARSHI type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=3ZQ696 /Kernel=TUKernel.exe

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=3ZQ696-BAK




================================ sda5/boot.ini: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(0)\Windows

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(0)\Windows="Windows XP" /fastdetect




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
# kopt=root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title Windows XP
root (hd0,0)
makeactive
chainloader +1

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=060b07fc-b705-4f8d-9882-cf72da5a962a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5 /media/windows ntfs defaults,uid=0,gid=46,auto,rw.nouser.umask=007 0 1
/dev/sda7 /media/installed ntfs defaults,uid=0,gid=46,auto,rw.nouser.umask=007 0 1
/dev/sda8 /media/documents ntfs defaults,uid=0,gid=46,auto,rw.nouser.umask=007 0 1
/dev/sda9 /media/videos+photos ntfs defaults,uid=0,gid=46,auto,rw.nouser.umask=007 0 1
/dev/sda10 /media/uninstalled ntfs defaults,uid=0,gid=46,auto,rw.nouser.umask=007 0 1

=================== sda6: Location of files loaded by Grub: ===================


  14.7GB: boot/grub/menu.lst
  14.7GB: boot/grub/stage2
  14.7GB: boot/initrd.img-2.6.24-19-generic
  14.7GB: boot/initrd.img-2.6.24-19-generic.bak
  14.8GB: boot/initrd.img-2.6.24-23-generic
  14.7GB: boot/initrd.img-2.6.24-23-generic.bak
  14.7GB: boot/vmlinuz-2.6.24-19-generic
  14.7GB: boot/vmlinuz-2.6.24-23-generic
  14.8GB: initrd.img
  14.7GB: initrd.img.old
  14.7GB: vmlinuz
  14.7GB: vmlinuz.old


apart from this, the output of menu.lst and fdisk -lu is-



> 
/boot/grub/menu.lst output-


title Windows XP
root (hd0,0)
makeactive
chainloader +1

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7c5bef73-f1db-465f-b71d-7ecc6b551336 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



> 

fdisk -lu   output:-



Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09550954

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      530144      265041   82  Linux swap / Solaris
/dev/sda2          530145   321653429   160561642+   f  W95 Ext'd (LBA)
/dev/sda5          530208    23438834    11454313+   7  HPFS/NTFS
/dev/sda6   *    23438898    41945714     9253408+  83  Linux
/dev/sda7        41945778   146801969    52428096    7  HPFS/NTFS
/dev/sda8       146802033   205519544    29358756    7  HPFS/NTFS
/dev/sda9       205519608   257955704    26218048+   7  HPFS/NTFS
/dev/sda10      257955768   321653429    31848831    7  HPFS/NTFS

Disk /dev/sdb: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897087 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7897086     3948512    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 37)

Disk /dev/sdc: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     3948542     1974240    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 200, 18)




i hope some help to arrive.

---

### Post by caljohnsmith on 2009-02-27
OK, how about doing the following:
```
sudo sfdisk -A1 /dev/sda
sudo sfdisk -c /dev/sda 1 7
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda1/boot.ini /mnt/sda5/
gksudo gedit /boot/grub/menu.lst
```
Then delete your current Windows entry from your menu.lst, and add the following entry instead before the "automagic kernel" lines like:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
Then reboot, try Windows from your Grub menu, and let me know how far you get. We can work from there.

---

### Post by SheikhAmanAlam on 2009-02-27
Yes.
it did work.
now im into windows.

thanks a lot.
bt can u tell what had happened, and what did u do to make it ok?

---

### Post by Hobgoblin on 2009-02-28
sda5 is your Windows partition, grub was pointing at sda1 which I assume is a recovery partition.

Grub numbers drives/partitions from 0 so sda1 is (hd0,0) and sda5 is (hd0,4)

---

### Post by caljohnsmith on 2009-02-28
> **SheikhAmanAlam said:**
> 
bt can u tell what had happened, and what did u do to make it ok?
Well the first sfdisk command set the boot flag on your sda1 partition while removing the boot flag on all your other partitions, because only one primary partition should be flagged as bootable; you had the boot flag set on both sda1 and sda6. The second sfdisk command changed the sda1 partition file system ID from swap (82) back to NTFS (7), because you sda1 partition is actually NTFS (I don't know what you did to accidentally change the file system ID to swap). Your original menu.lst was booting Windows using (hd0,0), which is sda1, so that means your Windows boot files (boot.ini, ntldr, NTDETECT.COM) were all in your sda1 partition; yet Windows is actually installed to sda5. When you unintentionally deleted Windows' boot files in your sda1 partition, you could no longer boot Windows; that's why you got the "NTLDR missing" error. So what we did is set up your sda5 Windows partition so you could boot Windows directly from that partition, without having to boot Windows by putting the boot files in sda1. Anyway, I'm glad it all worked OK; cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

### Post by SheikhAmanAlam on 2009-03-02
ohh dear!!
ur such a genius!
an angel!
thanks a lot once again.

as im getting familiar with linux day by day, i'll be needing u at many stages.


well i need to contact u over email so that we can be frnds if u want.
i wont ask anythng else either i'll be blamed fr spamming! :-)

thnks a lot once again john!

---

### Post by kdjtar on 2009-04-23
Hi! I've got the same problem. Can you help me?

Here's my RESULT.txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total de 488397168 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0x2e7f2e7e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977   7 HPFS/NTFS
/dev/sda2          19,535,040   488,392,064   468,857,025   f W95 Ext d (LBA)
/dev/sda5          19,535,103   488,392,064   468,856,962   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total de 160086528 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0xf5aff5af

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   123,186,419   123,186,357   7 HPFS/NTFS
/dev/sdb2         123,186,420   160,071,659    36,885,240   5 Extended
/dev/sdb5         123,186,483   148,360,274    25,173,792  83 Linux
/dev/sdb6         148,360,338   160,071,659    11,711,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5A30F14930F12D1F" LABEL="OSTest" TYPE="ntfs" 
/dev/sda5: UUID="B40453E20453A5E0" LABEL="Backup" TYPE="ntfs" 
/dev/sdb1: UUID="86E060FFE060F6B9" LABEL="XP_x64" TYPE="ntfs" 
/dev/sdb5: UUID="508974ba-4f60-42ca-b0b4-0d6144e9322f" TYPE="reiserfs" 
/dev/sdb6: UUID="72e69f0f-4aa0-4bdf-aa0b-f243d60cd10b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type reiserfs (rw,relatime,notail)
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
/dev/sda5 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=obedi)
/dev/sdb1 on /media/XP_x64 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/OSTest type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
H:\ubnldr.mbr="UNetbootin" 

=========================== sdb5/boot/grub/menu.lst: ===========================

default 0
timeout 10

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
# kopt=root=UUID=508974ba-4f60-42ca-b0b4-0d6144e9322f ro locale=pt_BR

## default grub root device
## e.g. groot=(hd0,0)
# groot=508974ba-4f60-42ca-b0b4-0d6144e9322f

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

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=508974ba-4f60-42ca-b0b4-0d6144e9322f ro locale=pt_BR quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=508974ba-4f60-42ca-b0b4-0d6144e9322f ro locale=pt_BR  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Professional x64 Edition
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
makeactive


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=508974ba-4f60-42ca-b0b4-0d6144e9322f /               reiserfs notail,relatime 0       1
# /dev/sdb6
UUID=72e69f0f-4aa0-4bdf-aa0b-f243d60cd10b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Backup
/dev/sda5    /media/Backup    ntfs auto,rw,umask=000 1 0 

=================== sdb5: Location of files loaded by Grub: ===================


  68.6GB: boot/grub/menu.lst
  68.4GB: boot/grub/stage2
  68.9GB: boot/initrd.img-2.6.27-11-generic
  68.5GB: boot/initrd.img-2.6.27-7-generic
  68.5GB: boot/vmlinuz-2.6.27-11-generic
  68.5GB: boot/vmlinuz-2.6.27-7-generic
  68.9GB: initrd.img
  68.5GB: initrd.img.old
  68.5GB: vmlinuz
  68.5GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-04-24
Kdjtar, it looks like the problem is your Grub is configured to boot the wrong partition for Windows, and that's why you are getting a "NTLDR missing" error. How about trying the following:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your current Windows entry with:
```
title Windows XP  Professional x64 Edition
root (hd0,0)
chainloader +1
```
Reboot, try the new Windows entry from your Grub menu, and let me know what happens.

---

### Post by kdjtar on 2009-04-24
**caljohnsmith**, you're great! Thank you so much!
I must have been installed something that had messed with my menu.lst, as it suddenly stopped working.
Everything's great now. Thanks to you!

---

### Post by malachi1990 on 2009-06-15
I'm having a similar problem, though it also appears that there are Windows issues as well.  Can someone inform me as to what command to use to get a result.txt file like the OP had?

Thanks!

---

### Post by Gin&amp;Tonic on 2009-08-13
> **malachi1990 said:**
> I'm having a similar problem, though it also appears that there are Windows issues as well.  Can someone inform me as to what command to use to get a result.txt file like the OP had?

Thanks!


This?

---

