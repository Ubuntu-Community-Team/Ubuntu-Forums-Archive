---
title: "[Boot Problem] XP ntldr issue when using grub, but not when booting from disk"
date: 2009-04-28
forum: General Help
---

### Post by Crethaln on 2009-04-28
Hey, I realize that most of you are thinking "oh god, not another noobie boot thread", but i HAVE already crawled the web a bit, and haven't found anything that exactly matches my problem.

So, the issue is pretty basic.  I have Ubuntu 9.04 on one HD, formatted as ext3, and booting via grub.  XP pro is on a seperate disk, formatted as NTFS.  The problem is, that when i choose XP from the grub loader, i get the ageold "ntldr not found, hit C+A+D to restart".  However, when i boot from the XP disk, i have no such issues.  I have no problems using grub to boot into Ubuntu

I checked through my menu.lst, and from what i have gathered from the internet and my own installation, the references appear correct.  Below is the relevant text


## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

As for the device mappings, they are as follows
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sde
(hd5)    /dev/sdh

Any ideas/suggestions?

---

### Post by Crethaln on 2009-04-28
nobody? anybody?
*bursts into Queen*
...can an-y-body help MEEEEE (voice cracks)....sombody to love

---

### Post by Crethaln on 2009-04-28
Below is the result I get from running the bootinfo script

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /Boot/BCD /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 1. But according to the info from fdisk, 
                       sdg1 starts at sector 247. According to the info in 
                       the boot sector, sdg1 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b7d8b7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   606,999,959   606,999,897  83 Linux
/dev/sda2         606,999,960   625,137,344    18,137,385   5 Extended
/dev/sda5         607,000,023   625,137,344    18,137,322  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001ea5b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd734b49e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d546806

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,638,405,089 1,638,405,027   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 2040 MB, 2040528896 bytes
29 heads, 28 sectors/track, 4908 cylinders, total 3985408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3f8c3f8

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                 247     3,985,407     3,985,161   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3e570927-4ab0-41ad-a7aa-91fbd017d5cd" TYPE="ext3" 
/dev/sda5: UUID="8f26e064-df64-4d41-9493-9ed437c55a66" TYPE="swap" 
/dev/sdb1: UUID="00000000440F6E2F" LABEL="Games" TYPE="ntfs" 
/dev/sdc1: UUID="6070818F70816D1A" LABEL="Boot and Downloads" TYPE="ntfs" 
/dev/sdd1: UUID="2A3C8D6E3C8D35BB" LABEL="Media" TYPE="ntfs" 
/dev/sdg1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/teaguejd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=teaguejd)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=teaguejd)
/dev/sdg1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Boot and Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3e570927-4ab0-41ad-a7aa-91fbd017d5cd

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3e570927-4ab0-41ad-a7aa-91fbd017d5cd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3e570927-4ab0-41ad-a7aa-91fbd017d5cd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8f26e064-df64-4d41-9493-9ed437c55a66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  18.1GB: boot/grub/menu.lst
  18.1GB: boot/grub/stage2
  18.2GB: boot/initrd.img-2.6.28-11-generic
  18.1GB: boot/vmlinuz-2.6.28-11-generic
  18.2GB: initrd.img
  18.1GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```

---

### Post by Crethaln on 2009-04-29
Still no succor? Am i in the wrong forum?

---

### Post by logos34 on 2009-04-29
the drive mapping only reflects the order at the time of installation...maybe sdc disk is now seen in second place instead of third. So try

> title Microsoft Windows XP Professional
rootnoverify (hd**1**,0)
savedefault
makeactive
map (hd0) (hd**1**)
map (hd**1**) (hd0)
chainloader +1

or maybe its fourth, in which case try (hd3,0)...etc etc

---

