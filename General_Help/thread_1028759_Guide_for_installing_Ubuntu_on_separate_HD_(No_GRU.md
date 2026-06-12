---
title: "Guide for installing Ubuntu on separate HD (No GRUB)"
date: 2009-01-02
forum: General Help
---

### Post by miocene on 2009-01-02
I had a bit of an issue installing ubuntu on my spare hd in the sense that GRUB overwrote the MBR on my Vista drive so I couldn't boot into windows.

What I will do this time is install ubuntu on my spare drive but disconnect my vista drive during the installation so the mbr is unaffected.

After this is done and my vista drive in reconnected would it be possible to boot into Vista or Ubuntu simply by choosing the drive to boot to in the setup utility of the BIOS?

Also, is there a decent guide (with screenshots) to help me through sorting it all out?

Thanks in advance.

---

### Post by bumanie on 2009-01-02
Yes, you can do it as you have planned and it should work OK by changing the first boot drive in bios each time you want to change OSes.

---

### Post by caljohnsmith on 2009-01-02
Just wanted to mention that you don't necessarily have to change your BIOS boot order every time you want to boot into either Ubuntu or Vista; you could for example set your BIOS to boot the Ubuntu drive, and then add Vista as an entry in your Grub menu so you can boot Vista from your Ubuntu drive. Or you could even add Ubuntu to your Vista boot manager if you wanted. Either way, you won't have to change your BIOS every time you want to boot the other OS, although that could certainly work if you prefer to do that. But if you want any help with the specifics of doing either of those scenarios, let me know.

---

### Post by miocene on 2009-01-04
> **caljohnsmith said:**
> Just wanted to mention that you don't necessarily have to change your BIOS boot order every time you want to boot into either Ubuntu or Vista; you could for example set your BIOS to boot the Ubuntu drive, and then add Vista as an entry in your Grub menu so you can boot Vista from your Ubuntu drive. Or you could even add Ubuntu to your Vista boot manager if you wanted. Either way, you won't have to change your BIOS every time you want to boot the other OS, although that could certainly work if you prefer to do that. But if you want any help with the specifics of doing either of those scenarios, let me know.

That would be really good actually. How do I go about achieving this?
I've got Ubuntu and Vista working as I'd said on separate drives and I currently choose the OS by changing the boot order in BIOS.

---

### Post by caljohnsmith on 2009-01-04
OK, in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Vista from Grub.

---

### Post by miocene on 2009-01-04
OK here we go:

```
============================= Boot Info Summary: ==============================

 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Drive sdh does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for its boot files.
 => Grub is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda2 already mounted or sda2 busy

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda3 already mounted or sda3 busy

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2           98304    21069823    10485760    7  HPFS/NTFS
/dev/sda3   *    21069824   624988159   301959168    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 3 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000064


sfdisk -V /dev/sdb:


sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/sdb: unrecognised partition table type

sfdisk: no partition table present.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   147010814    73505376   83  Linux
/dev/sdc2       147010815   153356489     3172837+   5  Extended
/dev/sdc5       147010878   153356489     3172806   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63    39070079    19535008+   b  W95 FAT32

sfdisk -V /dev/sdd:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdd: OK

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

Drive sdh: _____________________________________________________________________

fdisk -lu /dev/sdh:

sfdisk -V /dev/sdh:

/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading

blkid -c /dev/null: ____________________________________________________________

/dev/mapper/isw_bgdjcgdacf_ARRAY3: UUID="0E8CC0768CC059BB" LABEL="OS" TYPE="ntfs" 
/dev/mapper/isw_bgdjcgdacf_ARRAY2: UUID="1AFABD55FABD2E3F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/mapper/isw_bgdjcgdacf_ARRAY1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0307" TYPE="vfat" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0307" TYPE="vfat" 
/dev/sdc1: UUID="21e65992-35ab-4074-9369-886a52229904" TYPE="ext3" 
/dev/sdc5: UUID="aa93172f-83db-43c8-8fd2-4b019717bc5b" TYPE="swap" 
/dev/sdd1: UUID="495F-CE0C" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/harry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harry)
/dev/sdd1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/mapper/isw_bgdjcgdacf_ARRAY2 on /home/raid type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/mapper/isw_bgdjcgdacf_ARRAY3 on /home/raid type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=21e65992-35ab-4074-9369-886a52229904 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=21e65992-35ab-4074-9369-886a52229904 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=21e65992-35ab-4074-9369-886a52229904 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=21e65992-35ab-4074-9369-886a52229904 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=21e65992-35ab-4074-9369-886a52229904 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=21e65992-35ab-4074-9369-886a52229904 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aa93172f-83db-43c8-8fd2-4b019717bc5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 36464
drwxr-xr-x  3 root root    4096 2009-01-04 00:16 .
drwxr-xr-x 21 root root    4096 2009-01-03 16:47 ..
-rw-r--r--  1 root root  422607 2008-04-10 17:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   79964 2008-04-10 17:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-03 16:47 grub
-rw-r--r--  1 root root 7888822 2009-01-03 00:29 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 2008-04-22 19:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7734037 2009-01-04 00:16 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7499766 2009-01-03 16:47 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 17:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1904248 2008-04-10 17:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic

=============================== sdc1/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-03 16:47 .
drwxr-xr-x 3 root root   4096 2009-01-04 00:16 ..
-rw-r--r-- 1 root root    197 2009-01-03 00:29 default
-rw-r--r-- 1 root root     15 2009-01-03 00:29 device.map
-rw-r--r-- 1 root root   8056 2009-01-03 00:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-03 00:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 00:29 installed-version
-rw-r--r-- 1 root root   8608 2009-01-03 00:29 jfs_stage1_5
-rw-r--r-- 1 root root   4703 2009-01-03 16:47 menu.lst
-rw-r--r-- 1 root root   4265 2009-01-03 16:47 menu.lst~
-rw-r--r-- 1 root root   7324 2009-01-03 00:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-03 00:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 00:29 stage1
-rw-r--r-- 1 root root 108356 2009-01-03 00:29 stage2
-rw-r--r-- 1 root root   9276 2009-01-03 00:29 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  41 4e 00 62 00 66 00 61  00 6e 00 0f 00 3f 2e 00  |AN.b.f.a.n...?..|
00000010  4d 00 44 00 4d 00 00 00  ff ff 00 00 ff ff ff ff  |M.D.M...........|
00000020  4e 42 46 41 4e 20 20 20  4d 44 4d 20 00 2e d2 4e  |NBFAN   MDM ...N|
00000030  67 36 67 36 00 00 ba 73  8c 35 15 50 24 82 00 00  |g6g6...s.5.P$...|
00000040  41 4e 00 62 00 53 00 76  00 63 00 0f 00 e5 2e 00  |AN.b.S.v.c......|
00000050  4d 00 44 00 4d 00 00 00  ff ff 00 00 ff ff ff ff  |M.D.M...........|
00000060  4e 42 53 56 43 20 20 20  4d 44 4d 20 00 2e d2 4e  |NBSVC   MDM ...N|
00000070  67 36 67 36 00 00 ba 73  8c 35 26 50 98 14 01 00  |g6g6...s.5&P....|
00000080  41 4e 00 62 00 74 00 68  00 65 00 0f 00 53 72 00  |AN.b.t.h.e...Sr.|
00000090  6d 00 2e 00 4d 00 44 00  4d 00 00 00 00 00 ff ff  |m...M.D.M.......|
000000a0  4e 42 54 48 45 52 4d 20  4d 44 4d 20 00 2e d2 4e  |NBTHERM MDM ...N|
000000b0  67 36 67 36 00 00 bb 73  8c 35 49 50 54 bc 00 00  |g6g6...s.5IPT...|
000000c0  41 4e 00 69 00 63 00 2e  00 6d 00 0f 00 c1 64 00  |AN.i.c...m....d.|
000000d0  6d 00 00 00 ff ff ff ff  ff ff 00 00 ff ff ff ff  |m...............|
000000e0  4e 49 43 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |NIC     MDM ...N|
000000f0  67 36 67 36 00 00 bb 73  8c 35 61 50 80 a6 03 00  |g6g6...s.5aP....|
00000100  4e 49 43 38 32 35 34 58  4d 44 4d 20 08 2e d2 4e  |NIC8254XMDM ...N|
00000110  67 36 67 36 00 00 bb 73  8c 35 d6 50 3b 46 01 00  |g6g6...s.5.P;F..|
00000120  41 50 00 61 00 72 00 61  00 6c 00 0f 00 ac 6c 00  |AP.a.r.a.l....l.|
00000130  65 00 6c 00 2e 00 6d 00  64 00 00 00 6d 00 00 00  |e.l...m.d...m...|
00000140  50 41 52 41 4c 4c 45 4c  4d 44 4d 20 00 2e d2 4e  |PARALLELMDM ...N|
00000150  67 36 67 36 00 00 bb 73  8c 35 ff 50 7d ba 00 00  |g6g6...s.5.P}...|
00000160  41 50 00 63 00 69 00 2e  00 6d 00 0f 00 40 64 00  |AP.c.i...m...@d.|
00000170  6d 00 00 00 ff ff ff ff  ff ff 00 00 ff ff ff ff  |m...............|
00000180  50 43 49 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |PCI     MDM ...N|
00000190  67 36 67 36 00 00 bc 73  8c 35 17 51 63 39 00 00  |g6g6...s.5.Qc9..|
000001a0  41 50 00 65 00 72 00 63  00 32 00 0f 00 e7 41 00  |AP.e.r.c.2....A.|
000001b0  64 00 61 00 2e 00 6d 00  64 00 00 00 6d 00 00 00  |d.a...m.d...m...|
000001c0  50 45 52 43 32 41 44 41  4d 44 4d 20 00 2e d2 4e  |PERC2ADAMDM ...N|
000001d0  67 36 67 36 00 00 bc 73  8c 35 1f 51 d2 82 00 00  |g6g6...s.5.Q....|
000001e0  50 4d 20 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |PM      MDM ...N|
000001f0  67 36 67 36 00 00 bc 73  8c 35 30 51 6b 36 00 00  |g6g6...s.50Qk6..|
00000200

Unknown BootLoader  on /dev/sda2

00000000  c8 6a 8f c6 4c af 0e 56  37 96 7a a1 98 3a b3 0c  |.j..L..V7.z..:..|
00000010  42 35 2b e1 39 a2 e2 04  cd be 07 b5 80 5c fc 70  |B5+.9........\.p|
00000020  7f cd f6 d6 37 c1 f4 3d  c8 5e 58 8f 86 34 5b 06  |....7..=.^X..4[.|
00000030  68 fd f4 6e 7e 40 57 71  d3 be 1b 9c 89 00 57 f9  |h..n~@Wq......W.|
00000040  21 1d 00 8a 06 ed 0c 56  49 d4 c1 a2 66 71 17 57  |!......VI...fq.W|
00000050  2d 7c 5e 6a b4 49 56 a4  35 11 aa 28 fc be 77 30  |-|^j.IV.5..(..w0|
00000060  86 80 6b af 37 48 9a ac  dc 69 66 14 0e 6f 0c f3  |..k.7H...if..o..|
00000070  94 bb 35 97 fb 09 26 0a  a6 e8 e9 87 4f e0 8d 07  |..5...&.....O...|
00000080  ef c2 bd 13 44 b7 a7 55  27 88 7a e7 86 04 69 0b  |....D..U'.z...i.|
00000090  2d 32 9d 66 95 3d 75 95  59 26 a8 18 d0 f7 7b b9  |-2.f.=u.Y&....{.|
000000a0  0f fe fc e1 15 7d d5 d5  81 84 e7 bc 1a bc e7 c9  |.....}..........|
000000b0  b0 f4 41 ef 0b cf 43 c1  c7 ca f3 0d 81 84 c9 bc  |..A...C.........|
000000c0  74 00 1c 06 fd 40 87 a1  8c a9 dd c2 55 13 1c 98  |t....@......U...|
000000d0  d0 6b 85 b6 15 c6 a6 ae  0d cb 03 34 0d 71 2c 3c  |.k.........4.q,<|
000000e0  32 68 bb df 7e 85 e3 1e  dc a0 98 d8 e8 86 62 ad  |2h..~.........b.|
000000f0  d5 cf cc 14 7f c8 c1 8b  bf 46 7a a1 10 93 72 6f  |.........Fz...ro|
00000100  87 7f 9b 8a ec 95 11 60  53 98 0d 35 92 4c c0 09  |.......`S..5.L..|
00000110  61 8e 3c c8 ca d3 b3 a8  02 ec a9 41 4a 1c 0a a0  |a.<........AJ...|
00000120  68 ff f3 90 09 1b 41 f8  01 70 b0 10 09 a3 88 f9  |h.....A..p......|
00000130  c1 f9 97 11 22 1f 03 51  96 b1 3c 7e c8 47 f8 7d  |...."..Q..<~.G.}|
00000140  58 e0 fa e3 d2 00 f9 c1  3b a3 a1 68 94 34 be d5  |X.......;..h.4..|
00000150  aa b4 9a c2 c3 48 8e 03  f3 e9 34 a4 f2 e4 b2 66  |.....H....4....f|
00000160  38 14 83 21 fc 42 98 e4  7a 97 ab 30 23 f6 8d f1  |8..!.B..z..0#...|
00000170  5d bb 63 3f 06 18 36 97  3d 67 18 8a 0e e0 bd 2e  |].c?..6.=g......|
00000180  18 86 d9 8a 1a e3 d1 80  ba 65 27 f4 39 98 91 e4  |.........e'.9...|
00000190  1a 46 2b d5 9c a2 53 2b  82 3d 49 30 a1 a1 ad 13  |.F+...S+.=I0....|
000001a0  ec dd e4 64 7c d7 7c e3  23 4f 7a 73 c9 7b ca ec  |...d|.|.#Ozs.{..|
000001b0  8b 66 e1 86 0f cf ff 32  cd 9e 0f e0 15 ec 10 37  |.f.....2.......7|
000001c0  ac 25 5c c0 82 c0 5d 34  ca 2a b3 a9 be 42 f2 53  |.%\...]4.*...B.S|
000001d0  93 9c d0 85 a4 a2 d2 97  1a 68 56 55 79 a1 e4 7f  |.........hVUy...|
000001e0  52 f8 14 ac 7a 01 c3 b8  e1 e1 7f 42 32 8c ef 01  |R...z......B2...|
000001f0  1a 81 bf 12 03 eb 6d 1f  61 f3 dc e4 0b 27 b6 c2  |......m.a....'..|
00000200

Unknown BootLoader  on /dev/sda3

00000000  ef ce dd ef 1d 54 29 ac  60 4f e5 63 df 51 5c 93  |.....T).`O.c.Q\.|
00000010  4e 08 74 e5 fd de e8 bd  52 8f df b7 9c d4 e0 b1  |N.t.....R.......|
00000020  c5 cd 05 14 18 f0 51 71  e6 08 ed d6 b4 e7 f6 d3  |......Qq........|
00000030  64 da ec 64 d8 52 69 d3  0a 0e 38 94 29 93 93 63  |d..d.Ri...8.)..c|
00000040  a1 e0 bd ee 1c 40 25 90  94 f9 d7 04 e2 33 6d 99  |.....@%......3m.|
00000050  95 c1 42 2e 9f 8b f7 8a  11 bd 21 f1 28 bf f9 27  |..B.......!.(..'|
00000060  98 c1 71 88 f4 64 df 24  15 5f b7 c5 fe 2c 78 f1  |..q..d.$._...,x.|
00000070  45 8e 0a 3b ea 59 0a 41  e0 3f c5 06 08 40 7e 84  |E..;.Y.A.?...@~.|
00000080  05 7f d1 e7 d5 89 03 f9  2c 2d 29 74 c6 74 f0 3c  |........,-)t.t.<|
00000090  07 f6 e3 e1 2b f0 18 21  7d 4d c8 a3 ea f7 3a 06  |....+..!}M....:.|
000000a0  85 b8 19 c1 e3 c2 86 d9  ff 80 7f 01 84 b0 6b e5  |..............k.|
000000b0  2a 41 f0 bf f9 12 95 ab  52 0c 10 41 bf ed dc b0  |*A......R..A....|
000000c0  f8 d0 7f 07 66 e5 0c 82  cf ce 01 21 91 2a bb c3  |....f......!.*..|
000000d0  55 ea ad b9 7a 23 78 02  dc e5 eb c4 6f c2 db 0c  |U...z#x.....o...|
000000e0  89 e1 98 f9 f0 a3 26 37  1c 47 21 bf c2 68 ae 00  |......&7.G!..h..|
000000f0  5d 52 4a 14 7f 39 89 19  25 12 cb 81 9d 14 b6 48  |]RJ..9..%......H|
00000100  5e 25 7f f6 b4 4f 07 7e  36 64 28 db 5c 14 1e e6  |^%...O.~6d(.\...|
00000110  ad 85 af 12 f2 b2 1d 19  fa a5 63 ef 50 42 03 a3  |..........c.PB..|
00000120  be b7 18 e9 35 1f f6 15  0e ce ee 9f 51 8e 0a 28  |....5.......Q..(|
00000130  9f f6 56 46 91 58 f7 39  62 0d 1c 0c 3b 72 e9 e7  |..VF.X.9b...;r..|
00000140  75 c3 1d b5 0a db de e9  61 c1 19 63 6a 24 88 45  |u.......a..cj$.E|
00000150  ca ce 2b 1d 19 0b 23 50  55 a7 6a ef 1f 83 1f 2e  |..+...#PU.j.....|
00000160  1e 17 13 05 1f 79 da f7  bf 58 3a af 4e 06 61 62  |.....y...X:.N.ab|
00000170  71 23 a1 fe 13 31 41 61  e1 d0 c0 29 0f 9f b0 94  |q#...1Aa...)....|
00000180  02 4f 19 10 df 3e e2 72  45 70 8e bc 2c cd 9f 98  |.O...>.rEp..,...|
00000190  c9 d3 7d 71 c1 46 65 e0  2e bc 41 37 b8 78 5d 73  |..}q.Fe...A7.x]s|
000001a0  a0 90 6c 63 4d 36 93 27  68 5a a8 19 44 56 5e 08  |..lcM6.'hZ..DV^.|
000001b0  75 5d c9 ea a0 ba d8 a1  66 b5 82 20 0c 06 bf 03  |u]......f.. ....|
000001c0  c5 d6 da a0 47 00 80 65  0a c0 f8 34 55 b2 da 22  |....G..e...4U.."|
000001d0  17 ef 1b 58 56 e0 a2 ae  df c1 8c 9d 02 f6 b2 77  |...XV..........w|
000001e0  e1 96 0b 84 6b 60 b1 af  10 db 97 cc 51 da 6c 21  |....k`......Q.l!|
000001f0  83 c0 40 93 ef 40 62 f1  eb 6a 94 f5 b5 cc 7d 2f  |..@..@b..j....}/|
00000200


=============================== StdErr Messages: ===============================

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading
Disk /dev/sdb doesn't contain a valid partition table
me type
```

---

### Post by caljohnsmith on 2009-01-04
OK, it looks like you have Windows Vista on a RAID setup with drives sda and sdb, is that true? That might complicate things, but how about first opening up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add at the very bottom of the file:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot your Ubuntu drive, try both Vista entries from your Grub menu, and hopefully one will work (probably the first one, but it's hard to say). If not, let me know exactly what happens when you try them, and we can work from there. :)

---

### Post by miocene on 2009-01-04
OK that didn't work out well.
I selected the 1st Vista to boot to from grub having done what you had said above. It then entered the recovery thingy (my raid array is partitioned into 2 - one for Vista and everything, and a small recovery partition)
I quit the recovery immeditely as this was clearly not the right thing to boot to and rebooted the system.
It then failed to boot to either Vista or Ubuntu regardless of which drive was at the top of the boot list.
Luckily I mamnaged to repair the windows MBR using the Vista CD so I can not boot into windows.

However, now I can't boot into Ubuntu - whenever I choose to boot from the ubuntu drive I get a message on booting up of "operating system not found"

help, I've lost ubuntu

---

### Post by caljohnsmith on 2009-01-04
I sincerely apologize, because looking over the script output that you posted, I see now that Vista is most likely on the third partition and not the first partition, which as you found out is your recovery partition. So to find out what state Ubuntu is in, how about rerunning the script again from post #5 and post the results again. We can work from there.

---

### Post by miocene on 2009-01-04
That's going to be quite tricky as I can't boot into Ubuntu.
Will it still work from the Live CD?

---

### Post by caljohnsmith on 2009-01-04
> **miocene said:**
> That's going to be quite tricky as I can't boot into Ubuntu.
Will it still work from the Live CD?
Yes, I should have mentioned that; but I'm thinking that probably all that happened is the Vista CD overwrote the Ubuntu MBR, so before you post the results of the script again, how about trying this first:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
If that completes without errors, go ahead and try booting your Ubuntu drive again. If that doesn't work, then please post the output of the script and we can go from there.

---

### Post by miocene on 2009-01-04
OK here's the GRUB output:

```
grub> root (hd2,0)

grub> setup (hd2)

Error 17: Cannot mount selected partition

grub> 
```



And here's the results.txt:

```
============================= Boot Info Summary: ==============================

 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       98304    21069823    10485760    7  HPFS/NTFS
/dev/sda3        21069824   624988159   301959168    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 3 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000064


sfdisk -V /dev/sdb:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63       96389       48163+   6  FAT16
/dev/sdc2           98304    21069823    10485760    7  HPFS/NTFS
/dev/sdc3   *    21069824   624988159   301959168    7  HPFS/NTFS

sfdisk -V /dev/sdc:

Warning: partition 3 extends past end of disk

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0307" TYPE="vfat" 
/dev/sdc1: UUID="21e65992-35ab-4074-9369-886a52229904" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

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

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  41 4e 00 62 00 66 00 61  00 6e 00 0f 00 3f 2e 00  |AN.b.f.a.n...?..|
00000010  4d 00 44 00 4d 00 00 00  ff ff 00 00 ff ff ff ff  |M.D.M...........|
00000020  4e 42 46 41 4e 20 20 20  4d 44 4d 20 00 2e d2 4e  |NBFAN   MDM ...N|
00000030  67 36 67 36 00 00 ba 73  8c 35 15 50 24 82 00 00  |g6g6...s.5.P$...|
00000040  41 4e 00 62 00 53 00 76  00 63 00 0f 00 e5 2e 00  |AN.b.S.v.c......|
00000050  4d 00 44 00 4d 00 00 00  ff ff 00 00 ff ff ff ff  |M.D.M...........|
00000060  4e 42 53 56 43 20 20 20  4d 44 4d 20 00 2e d2 4e  |NBSVC   MDM ...N|
00000070  67 36 67 36 00 00 ba 73  8c 35 26 50 98 14 01 00  |g6g6...s.5&P....|
00000080  41 4e 00 62 00 74 00 68  00 65 00 0f 00 53 72 00  |AN.b.t.h.e...Sr.|
00000090  6d 00 2e 00 4d 00 44 00  4d 00 00 00 00 00 ff ff  |m...M.D.M.......|
000000a0  4e 42 54 48 45 52 4d 20  4d 44 4d 20 00 2e d2 4e  |NBTHERM MDM ...N|
000000b0  67 36 67 36 00 00 bb 73  8c 35 49 50 54 bc 00 00  |g6g6...s.5IPT...|
000000c0  41 4e 00 69 00 63 00 2e  00 6d 00 0f 00 c1 64 00  |AN.i.c...m....d.|
000000d0  6d 00 00 00 ff ff ff ff  ff ff 00 00 ff ff ff ff  |m...............|
000000e0  4e 49 43 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |NIC     MDM ...N|
000000f0  67 36 67 36 00 00 bb 73  8c 35 61 50 80 a6 03 00  |g6g6...s.5aP....|
00000100  4e 49 43 38 32 35 34 58  4d 44 4d 20 08 2e d2 4e  |NIC8254XMDM ...N|
00000110  67 36 67 36 00 00 bb 73  8c 35 d6 50 3b 46 01 00  |g6g6...s.5.P;F..|
00000120  41 50 00 61 00 72 00 61  00 6c 00 0f 00 ac 6c 00  |AP.a.r.a.l....l.|
00000130  65 00 6c 00 2e 00 6d 00  64 00 00 00 6d 00 00 00  |e.l...m.d...m...|
00000140  50 41 52 41 4c 4c 45 4c  4d 44 4d 20 00 2e d2 4e  |PARALLELMDM ...N|
00000150  67 36 67 36 00 00 bb 73  8c 35 ff 50 7d ba 00 00  |g6g6...s.5.P}...|
00000160  41 50 00 63 00 69 00 2e  00 6d 00 0f 00 40 64 00  |AP.c.i...m...@d.|
00000170  6d 00 00 00 ff ff ff ff  ff ff 00 00 ff ff ff ff  |m...............|
00000180  50 43 49 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |PCI     MDM ...N|
00000190  67 36 67 36 00 00 bc 73  8c 35 17 51 63 39 00 00  |g6g6...s.5.Qc9..|
000001a0  41 50 00 65 00 72 00 63  00 32 00 0f 00 e7 41 00  |AP.e.r.c.2....A.|
000001b0  64 00 61 00 2e 00 6d 00  64 00 00 00 6d 00 00 00  |d.a...m.d...m...|
000001c0  50 45 52 43 32 41 44 41  4d 44 4d 20 00 2e d2 4e  |PERC2ADAMDM ...N|
000001d0  67 36 67 36 00 00 bc 73  8c 35 1f 51 d2 82 00 00  |g6g6...s.5.Q....|
000001e0  50 4d 20 20 20 20 20 20  4d 44 4d 20 00 2e d2 4e  |PM      MDM ...N|
000001f0  67 36 67 36 00 00 bc 73  8c 35 30 51 6b 36 00 00  |g6g6...s.50Qk6..|
00000200

Unknown BootLoader  on /dev/sda2

00000000  c8 6a 8f c6 4c af 0e 56  37 96 7a a1 98 3a b3 0c  |.j..L..V7.z..:..|
00000010  42 35 2b e1 39 a2 e2 04  cd be 07 b5 80 5c fc 70  |B5+.9........\.p|
00000020  7f cd f6 d6 37 c1 f4 3d  c8 5e 58 8f 86 34 5b 06  |....7..=.^X..4[.|
00000030  68 fd f4 6e 7e 40 57 71  d3 be 1b 9c 89 00 57 f9  |h..n~@Wq......W.|
00000040  21 1d 00 8a 06 ed 0c 56  49 d4 c1 a2 66 71 17 57  |!......VI...fq.W|
00000050  2d 7c 5e 6a b4 49 56 a4  35 11 aa 28 fc be 77 30  |-|^j.IV.5..(..w0|
00000060  86 80 6b af 37 48 9a ac  dc 69 66 14 0e 6f 0c f3  |..k.7H...if..o..|
00000070  94 bb 35 97 fb 09 26 0a  a6 e8 e9 87 4f e0 8d 07  |..5...&.....O...|
00000080  ef c2 bd 13 44 b7 a7 55  27 88 7a e7 86 04 69 0b  |....D..U'.z...i.|
00000090  2d 32 9d 66 95 3d 75 95  59 26 a8 18 d0 f7 7b b9  |-2.f.=u.Y&....{.|
000000a0  0f fe fc e1 15 7d d5 d5  81 84 e7 bc 1a bc e7 c9  |.....}..........|
000000b0  b0 f4 41 ef 0b cf 43 c1  c7 ca f3 0d 81 84 c9 bc  |..A...C.........|
000000c0  74 00 1c 06 fd 40 87 a1  8c a9 dd c2 55 13 1c 98  |t....@......U...|
000000d0  d0 6b 85 b6 15 c6 a6 ae  0d cb 03 34 0d 71 2c 3c  |.k.........4.q,<|
000000e0  32 68 bb df 7e 85 e3 1e  dc a0 98 d8 e8 86 62 ad  |2h..~.........b.|
000000f0  d5 cf cc 14 7f c8 c1 8b  bf 46 7a a1 10 93 72 6f  |.........Fz...ro|
00000100  87 7f 9b 8a ec 95 11 60  53 98 0d 35 92 4c c0 09  |.......`S..5.L..|
00000110  61 8e 3c c8 ca d3 b3 a8  02 ec a9 41 4a 1c 0a a0  |a.<........AJ...|
00000120  68 ff f3 90 09 1b 41 f8  01 70 b0 10 09 a3 88 f9  |h.....A..p......|
00000130  c1 f9 97 11 22 1f 03 51  96 b1 3c 7e c8 47 f8 7d  |...."..Q..<~.G.}|
00000140  58 e0 fa e3 d2 00 f9 c1  3b a3 a1 68 94 34 be d5  |X.......;..h.4..|
00000150  aa b4 9a c2 c3 48 8e 03  f3 e9 34 a4 f2 e4 b2 66  |.....H....4....f|
00000160  38 14 83 21 fc 42 98 e4  7a 97 ab 30 23 f6 8d f1  |8..!.B..z..0#...|
00000170  5d bb 63 3f 06 18 36 97  3d 67 18 8a 0e e0 bd 2e  |].c?..6.=g......|
00000180  18 86 d9 8a 1a e3 d1 80  ba 65 27 f4 39 98 91 e4  |.........e'.9...|
00000190  1a 46 2b d5 9c a2 53 2b  82 3d 49 30 a1 a1 ad 13  |.F+...S+.=I0....|
000001a0  ec dd e4 64 7c d7 7c e3  23 4f 7a 73 c9 7b ca ec  |...d|.|.#Ozs.{..|
000001b0  8b 66 e1 86 0f cf ff 32  cd 9e 0f e0 15 ec 10 37  |.f.....2.......7|
000001c0  ac 25 5c c0 82 c0 5d 34  ca 2a b3 a9 be 42 f2 53  |.%\...]4.*...B.S|
000001d0  93 9c d0 85 a4 a2 d2 97  1a 68 56 55 79 a1 e4 7f  |.........hVUy...|
000001e0  52 f8 14 ac 7a 01 c3 b8  e1 e1 7f 42 32 8c ef 01  |R...z......B2...|
000001f0  1a 81 bf 12 03 eb 6d 1f  61 f3 dc e4 0b 27 b6 c2  |......m.a....'..|
00000200

Unknown BootLoader  on /dev/sda3

00000000  ef ce dd ef 1d 54 29 ac  60 4f e5 63 df 51 5c 93  |.....T).`O.c.Q\.|
00000010  4e 08 74 e5 fd de e8 bd  52 8f df b7 9c d4 e0 b1  |N.t.....R.......|
00000020  c5 cd 05 14 18 f0 51 71  e6 08 ed d6 b4 e7 f6 d3  |......Qq........|
00000030  64 da ec 64 d8 52 69 d3  0a 0e 38 94 29 93 93 63  |d..d.Ri...8.)..c|
00000040  a1 e0 bd ee 1c 40 25 90  94 f9 d7 04 e2 33 6d 99  |.....@%......3m.|
00000050  95 c1 42 2e 9f 8b f7 8a  11 bd 21 f1 28 bf f9 27  |..B.......!.(..'|
00000060  98 c1 71 88 f4 64 df 24  15 5f b7 c5 fe 2c 78 f1  |..q..d.$._...,x.|
00000070  45 8e 0a 3b ea 59 0a 41  e0 3f c5 06 08 40 7e 84  |E..;.Y.A.?...@~.|
00000080  05 7f d1 e7 d5 89 03 f9  2c 2d 29 74 c6 74 f0 3c  |........,-)t.t.<|
00000090  07 f6 e3 e1 2b f0 18 21  7d 4d c8 a3 ea f7 3a 06  |....+..!}M....:.|
000000a0  85 b8 19 c1 e3 c2 86 d9  ff 80 7f 01 84 b0 6b e5  |..............k.|
000000b0  2a 41 f0 bf f9 12 95 ab  52 0c 10 41 bf ed dc b0  |*A......R..A....|
000000c0  f8 d0 7f 07 66 e5 0c 82  cf ce 01 21 91 2a bb c3  |....f......!.*..|
000000d0  55 ea ad b9 7a 23 78 02  dc e5 eb c4 6f c2 db 0c  |U...z#x.....o...|
000000e0  89 e1 98 f9 f0 a3 26 37  1c 47 21 bf c2 68 ae 00  |......&7.G!..h..|
000000f0  5d 52 4a 14 7f 39 89 19  25 12 cb 81 9d 14 b6 48  |]RJ..9..%......H|
00000100  5e 25 7f f6 b4 4f 07 7e  36 64 28 db 5c 14 1e e6  |^%...O.~6d(.\...|
00000110  ad 85 af 12 f2 b2 1d 19  fa a5 63 ef 50 42 03 a3  |..........c.PB..|
00000120  be b7 18 e9 35 1f f6 15  0e ce ee 9f 51 8e 0a 28  |....5.......Q..(|
00000130  9f f6 56 46 91 58 f7 39  62 0d 1c 0c 3b 72 e9 e7  |..VF.X.9b...;r..|
00000140  75 c3 1d b5 0a db de e9  61 c1 19 63 6a 24 88 45  |u.......a..cj$.E|
00000150  ca ce 2b 1d 19 0b 23 50  55 a7 6a ef 1f 83 1f 2e  |..+...#PU.j.....|
00000160  1e 17 13 05 1f 79 da f7  bf 58 3a af 4e 06 61 62  |.....y...X:.N.ab|
00000170  71 23 a1 fe 13 31 41 61  e1 d0 c0 29 0f 9f b0 94  |q#...1Aa...)....|
00000180  02 4f 19 10 df 3e e2 72  45 70 8e bc 2c cd 9f 98  |.O...>.rEp..,...|
00000190  c9 d3 7d 71 c1 46 65 e0  2e bc 41 37 b8 78 5d 73  |..}q.Fe...A7.x]s|
000001a0  a0 90 6c 63 4d 36 93 27  68 5a a8 19 44 56 5e 08  |..lcM6.'hZ..DV^.|
000001b0  75 5d c9 ea a0 ba d8 a1  66 b5 82 20 0c 06 bf 03  |u]......f.. ....|
000001c0  c5 d6 da a0 47 00 80 65  0a c0 f8 34 55 b2 da 22  |....G..e...4U.."|
000001d0  17 ef 1b 58 56 e0 a2 ae  df c1 8c 9d 02 f6 b2 77  |...XV..........w|
000001e0  e1 96 0b 84 6b 60 b1 af  10 db 97 cc 51 da 6c 21  |....k`......Q.l!|
000001f0  83 c0 40 93 ef 40 62 f1  eb 6a 94 f5 b5 cc 7d 2f  |..@..@b..j....}/|
00000200

Unknown BootLoader  on /dev/sdc2

00000000  a4 81 00 00 1b 1e 00 00  56 c0 60 49 53 c0 60 49  |........V.`IS.`I|
00000010  53 c0 60 49 00 00 00 00  00 00 01 00 10 00 00 00  |S.`I............|
00000020  00 00 00 00 00 00 00 00  02 b0 43 00 03 b0 43 00  |..........C...C.|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 98 b3 1b 9b  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  ed 41 00 00 00 10 00 00  53 c0 60 49 53 c0 60 49  |.A......S.`IS.`I|
00000090  53 c0 60 49 00 00 00 00  00 00 02 00 08 00 00 00  |S.`I............|
000000a0  00 00 00 00 00 00 00 00  0d f9 43 00 00 00 00 00  |..........C.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  00 00 00 00 99 b3 1b 9b  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  a4 81 00 00 00 00 00 00  53 c0 60 49 53 c0 60 49  |........S.`IS.`I|
00000110  53 c0 60 49 00 00 00 00  00 00 01 00 00 00 00 00  |S.`I............|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 9a b3 1b 9b  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  a4 81 00 00 00 00 00 00  53 c0 60 49 53 c0 60 49  |........S.`IS.`I|
00000190  53 c0 60 49 00 00 00 00  00 00 01 00 00 00 00 00  |S.`I............|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 9b b3 1b 9b  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: sda1/??: binary operator expected
boot_info_script.txt: line 485: [: sda1/üëe?ïe?p.ïe?: binary operator expected
boot_info_script.txt: line 485: [: sda1/üëe?ïe?p.ïe?: binary operator expected
boot_info_script.txt: line 485: [: sda1/eïçh.*é?: binary operator expected
boot_info_script.txt: line 485: [: sda1/eïçh.*é?: binary operator expected
boot_info_script.txt: line 485: [: sda1/?èe?ïmï.ë?: binary operator expected
boot_info_script.txt: line 485: [: sda1/?èe?ïmï.ë?: binary operator expected
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: sda1/e°*pâ?.êe?: binary operator expected
boot_info_script.txt: line 485: [: sda1/e°*pâ?.êe?: binary operator expected
boot_info_script.txt: line 485: [: sda1/m9à?: binary operator expected
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
boot_info_script.txt: line 485: [: too many arguments
Disk /dev/sdb doesn't contain a valid partition table
me type
/dev/sdc2: unknown volume type
/dev/sdc3: unknown volume type 
```

---

### Post by caljohnsmith on 2009-01-04
Unfortunately it looks like the Vista recovery partition completely overwrote your Ubuntu sdc drive with new Windows/recovery partitions. Did you have any really important data on the Ubuntu drive that you need to recover? It will be difficult if you do, but you implied in your first post that Ubuntu is a relatively new install; so can you reinstall Ubuntu to that drive? It looks like that's about the only option since the Windows recovery partition completely overwrote that drive.

---

### Post by miocene on 2009-01-04
Oh damn.
Well I didn't have anything important on it but its a bit of a hassle. I don't know how the Windows recovery thing did that as I quit straight away.

I think I'll wait and install 8.10 when I get it downloaded. Got to find a blank CD now.

Thanks anyways

---

