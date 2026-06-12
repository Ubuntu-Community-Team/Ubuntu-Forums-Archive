---
title: "[SOLVED] Error 17 AND Error 21"
date: 2009-01-05
forum: General Help
---

### Post by relaxedcrazyman on 2009-01-05
Hello, i have recently started using ubuntu, and i have it installed working fine. Until now. I tried to also install it on a 8GB Corsair thumbdrive. when the install was complete, i tried to boot from the thumbdrive to see if it would work, it did not, and booted to the next drive. When i unplugged the hdd that i have ubuntu installed on it and booted from the thumbdrive, i get GRUB Error 17. When i try to boot from my hdd that has windows installed to it, i get GRUB Error 21. I can still boot to my hdd ubuntu, but that is it. i tried booting the thumbdrive on another computer but i got the GRUB Error.

I tried using Super Grub, but couldnt figure out what to do with it. Please when responding keep in mind i am a super noober and dont really know what i am doing, so simple instructions please. 

Any ideas on how to fix my windows?

---

### Post by bumanie on 2009-01-05
I would suggest not worrying about the thumb drive at present - [Follow this ]("http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/")for installing a bootable ubuntu from a thumb drive. There are other methods, but I have always found this one to work.
For the grub 21 error can you please go to terminal and post the output of > sudo fdisk -luwithout the thumb drive connected. Grub error 21 can usually be fixed by reinstalling grub - as you can boot into ubuntu you should be able to do it from within ubuntu.

---

### Post by relaxedcrazyman on 2009-01-05
dunno if it makes any difference, but ubuntu and windows are installed on different drives.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1944523664   105000808+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by relaxedcrazyman on 2009-01-05
dunno if it makes any difference, but ubuntu and windows are installed on different drives.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1944523664   105000808+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2009-01-05
Is your Windows on the 160 GB drive or the 500 GB drive? It looks like Windows is on the 160 GB drive, but I could be wrong. If you want, you can restore a Windows MBR to the Windows drive by doing the following from the Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
That assumes Windows is on the 160 GB sda drive, which seems the most likely, but change sda in the above command if Windows is on a different drive. Also, it doesn't look like you had your thumb drive connected when you did the fdisk command, is that true? If you want help booting your thumb drive, how about posting the fdisk command again with your thumb drive connected. But in the meantime, let me know if the above commands allow you to boot directly into Windows when you boot the Windows drive.

---

### Post by relaxedcrazyman on 2009-01-05
it is on the 160 GB drive, and when you say use the Live CD i am guessing that means that i cant/shouldnt do it through my ubuntu install?

---

### Post by caljohnsmith on 2009-01-05
> **relaxedcrazyman said:**
> it is on the 160 GB drive, and when you say use the Live CD i am guessing that means that i cant/shouldnt do it through my ubuntu install?
My mistake, I shouldn't have implied that you can only do those commands from the Live CD; you can do them just as easily from your Ubuntu install. :)

---

### Post by relaxedcrazyman on 2009-01-06
[QUOTE=caljohnsmith;6502067]
```
sudo apt-get install lilo
sudo lilo -M  /dev/[COLOR="Blue"]sda[/COLOR] mbr
```



Worked great, thanks a million. that was 10000000000000000X easier then some of the stuff i was reading and trying.

---

### Post by relaxedcrazyman on 2009-01-14
I do believe that my BIOS can boot from USB



this is Boot Info Script:

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sde2: _________________________________________________________________________

    File system:       Extended Partition

sde5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1944523664   105000808+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: partition 1 does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

sfdisk -V /dev/sdc:

Warning: partitions 1 and 3 overlap

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52baa59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   490231807   245114880    7  HPFS/NTFS

sfdisk -V /dev/sdd:

Warning: partition 1 extends past end of disk

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

Disk /dev/sde: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63    15020774     7510356   83  Linux
/dev/sde2        15020775    15791894      385560    5  Extended
/dev/sde5        15020838    15791894      385528+  82  Linux swap / Solaris

sfdisk -V /dev/sde:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sde: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9CB06E70B06E5136" TYPE="ntfs" 
/dev/sdb1: UUID="4ADA3188DA317175" LABEL="TeraByte!" TYPE="ntfs" 
/dev/sdb5: UUID="30800993-881d-43bd-a0ff-484302ef057d" TYPE="ext3" 
/dev/sdb6: UUID="dcf48439-65c2-4cd8-bc54-782739303012" TYPE="swap" 
/dev/sdc: UUID="0E46FD0F46FCF7F3" TYPE="ntfs" 
/dev/sdd1: UUID="587E411E7E40F672" LABEL="External Maxtor" TYPE="ntfs" 
/dev/sde1: UUID="e0dbb36f-c96c-4915-911a-cd9a674a9b9d" TYPE="ext3" 
/dev/sde5: UUID="0613853c-adf0-442d-aa2d-f6e8f20269f6" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb5 on /media/sdb5 type ext3 (rw,errors=remount-ro)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/themaster/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=themaster)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)

================================== sda1/Boot: ==================================

total 800
drwxrwxrwx 1 root root   4096 2008-05-17 21:39 .
drwxrwxrwx 1 root root  36864 2009-01-08 23:28 ..
-rwxrwxrwx 1 root root  36864 2009-01-12 19:18 BCD
-rwxrwxrwx 1 root root 262144 2009-01-12 18:44 BCD.LOG
-rwxrwxrwx 2 root root      0 2004-01-01 01:15 BCD.LOG1
-rwxrwxrwx 2 root root      0 2004-01-01 01:15 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-05-12 14:35 bootstat.dat
drwxrwxrwx 1 root root      0 2008-05-17 21:39 cs-CZ
drwxrwxrwx 1 root root      0 2008-05-17 21:39 da-DK
drwxrwxrwx 1 root root      0 2008-05-17 21:39 de-DE
drwxrwxrwx 1 root root      0 2008-05-17 21:39 el-GR
drwxrwxrwx 1 root root      0 2008-05-17 21:39 en-US
drwxrwxrwx 1 root root      0 2008-05-17 21:39 es-ES
drwxrwxrwx 1 root root      0 2008-05-17 21:39 fi-FI
drwxrwxrwx 1 root root   4096 2008-05-17 21:39 Fonts
drwxrwxrwx 1 root root      0 2008-05-17 21:39 fr-FR
drwxrwxrwx 1 root root      0 2008-05-17 21:39 hu-HU
drwxrwxrwx 1 root root      0 2008-05-17 21:39 it-IT
drwxrwxrwx 1 root root      0 2008-05-17 21:39 ja-JP
drwxrwxrwx 1 root root      0 2008-05-17 21:39 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-18 23:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-05-17 21:39 nb-NO
drwxrwxrwx 1 root root      0 2008-05-17 21:39 nl-NL
drwxrwxrwx 1 root root      0 2008-05-17 21:39 pl-PL
drwxrwxrwx 1 root root      0 2008-05-17 21:39 pt-BR
drwxrwxrwx 1 root root      0 2008-05-17 21:39 pt-PT
drwxrwxrwx 1 root root      0 2008-05-17 21:39 ru-RU
drwxrwxrwx 1 root root      0 2008-05-17 21:39 sv-SE
drwxrwxrwx 1 root root      0 2008-05-17 21:39 tr-TR
drwxrwxrwx 1 root root      0 2008-05-17 21:39 zh-CN
drwxrwxrwx 1 root root      0 2008-05-17 21:39 zh-HK
drwxrwxrwx 1 root root      0 2008-05-17 21:39 zh-TW

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda5
UUID=30800993-881d-43bd-a0ff-484302ef057d  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=dcf48439-65c2-4cd8-bc54-782739303012  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdc2                                  /media/sdc2     ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sdb5                                  /media/sdb5     ext3         errors=remount-ro           0  0  
/dev/sdb6                                  /media/sdb6     swap         sw                          0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sdd1                                  /media/sdd1     ntfs         nls=iso8859-1,umask=000     0  0  

================================== sdb5/boot: ==================================

total 42116
drwxr-xr-x  3 root root    4096 2009-01-05 20:35 .
drwxr-xr-x 22 root root    4096 2009-01-08 23:28 ..
-rw-r--r--  1 root root  422838 2008-10-21 20:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root     512 2009-01-05 20:35 boot.0800
-rw-r--r--  1 root root  308326 2009-01-05 20:35 coffee.bmp
-rw-r--r--  1 root root   80062 2008-10-21 20:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
lrwxrwxrwx  1 root root      15 2009-01-05 20:35 debian.bmp -> /boot/sarge.bmp
-rw-r--r--  1 root root  153720 2009-01-05 20:35 debianlilo.bmp
drwxr-xr-x  2 root root    4096 2008-12-01 23:28 grub
-rw-r--r--  1 root root 7495563 2008-10-28 08:24 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7496453 2008-10-15 18:57 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8114321 2008-11-10 10:10 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8135704 2009-01-04 17:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root   23662 2009-01-05 20:35 sarge.bmp
-rw-r--r--  1 root root   24116 2009-01-05 20:35 sid.bmp
-rw-r--r--  1 root root  905617 2008-10-21 20:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-21 20:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

=============================== sdb5/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-12-01 23:28 .
drwxr-xr-x 3 root root   4096 2009-01-05 20:35 ..
-rw-r--r-- 1 root root    197 2008-10-07 19:47 default
-rw-r--r-- 1 root root     30 2008-10-07 19:47 device.map
-rw-r--r-- 1 root root   8056 2008-10-07 19:47 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-07 19:47 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-07 19:47 installed-version
-rw-r--r-- 1 root root   8608 2008-10-07 19:47 jfs_stage1_5
-rw-r--r-- 1 root root   5048 2008-12-01 23:28 menu.lst
-rw-r--r-- 1 root root   4624 2008-12-01 23:28 menu.lst~
-rw-r--r-- 1 root root   7324 2008-10-07 19:47 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-07 19:47 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-07 19:47 stage1
-rw-r--r-- 1 root root 108356 2008-10-07 19:47 stage2
-rw-r--r-- 1 root root   9276 2008-10-07 19:47 xfs_stage1_5

=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e0dbb36f-c96c-4915-911a-cd9a674a9b9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0dbb36f-c96c-4915-911a-cd9a674a9b9d

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
uuid		e0dbb36f-c96c-4915-911a-cd9a674a9b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0dbb36f-c96c-4915-911a-cd9a674a9b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e0dbb36f-c96c-4915-911a-cd9a674a9b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0dbb36f-c96c-4915-911a-cd9a674a9b9d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e0dbb36f-c96c-4915-911a-cd9a674a9b9d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=30800993-881d-43bd-a0ff-484302ef057d ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=e0dbb36f-c96c-4915-911a-cd9a674a9b9d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=0613853c-adf0-442d-aa2d-f6e8f20269f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sde1/boot: ==================================

total 11956
drwxr-xr-x  3 root root    4096 2008-12-15 21:35 .
drwxr-xr-x 20 root root    4096 2008-12-15 21:35 ..
-rw-r--r--  1 root root  507665 2008-10-24 01:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 01:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-15 21:36 grub
-rw-r--r--  1 root root 8184272 2008-12-15 21:35 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 01:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 01:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 01:29 vmlinuz-2.6.27-7-generic

=============================== sde1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2008-12-15 21:36 .
drwxr-xr-x 3 root root   4096 2008-12-15 21:35 ..
-rw-r--r-- 1 root root    197 2008-12-15 21:35 default
-rw-r--r-- 1 root root     60 2008-12-15 21:35 device.map
-rw-r--r-- 1 root root   8108 2008-12-15 21:35 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-15 21:35 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-15 21:36 installed-version
-rw-r--r-- 1 root root   8712 2008-12-15 21:35 jfs_stage1_5
-rw-r--r-- 1 root root   6943 2008-12-15 21:36 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-15 21:35 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-15 21:35 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-15 21:35 stage1
-rw-r--r-- 1 root root 121460 2008-12-15 21:36 stage2
-rw-r--r-- 1 root root   9556 2008-12-15 21:35 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdc

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  2f 60 38 3a 00 00 00 00  |......../`8:....|
00000030  00 00 0c 00 00 00 00 00  02 86 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f3 f7 fc 46 0f fd 46 0e  |...........F..F.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 07 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |om.ressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```




this is the fdisk for thumbdrive:

themaster@themaster-desktop:~$ sudo fdisk -lu 
[sudo] password for themaster: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1944523664   105000808+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52baa59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   490231807   245114880    7  HPFS/NTFS

Disk /dev/sde: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63    15020774     7510356   83  Linux
/dev/sde2        15020775    15791894      385560    5  Extended
/dev/sde5        15020838    15791894      385528+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-01-14
OK, it looks like your USB stick might be changing drive letters sometimes, so how about first doing again:
```
sudo fdisk -lu
```
Check which is the USB stick, and if it isn't sde, change only that in the commands that follow:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sde[/COLOR]
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands before doing "quit". Reboot, set your BIOS to boot the USB stick, and let me know what happens. We can work from there. :)

---

### Post by relaxedcrazyman on 2009-01-14
fdisk:

themaster@themaster-desktop:~$ sudo fdisk -lu
[sudo] password for themaster: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1944523664   105000808+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52baa59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   490231807   245114880    7  HPFS/NTFS

Disk /dev/sde: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63    15020774     7510356   83  Linux
/dev/sde2        15020775    15791894      385560    5  Extended
/dev/sde5        15020838    15791894      385528+  82  Linux swap / Solaris




GRUB:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> device (hd0) /dev/sde

grub> root (hd0,0)

grub> makeactive

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by relaxedcrazyman on 2009-01-14
THANKS!!! it works!!!

1 more question for ya, i opened another thread about this but got no responses, thought maybe you could help.

i have ubuntu installed on my 1tb harddrive on a 100gb partition, i wanted to copy the ubuntu install to my 500gb harddrive which it would use the whole thing and then reclaim the 1tb harddrive, any ideas?

---

### Post by caljohnsmith on 2009-01-14
> **relaxedcrazyman said:**
> THANKS!!! it works!!!

1 more question for ya, i opened another thread about this but got no responses, thought maybe you could help.

i have ubuntu installed on my 1tb harddrive on a 100gb partition, i wanted to copy the ubuntu install to my 500gb harddrive which it would use the whole thing and then reclaim the 1tb harddrive, any ideas?
Glad to hear that's all it took to get your USB stick booting OK. About your question, you could use Ubuntu's partition editor gparted to simply copy/paste your 100 GB Ubuntu partition from the 1 TB drive to the 500 GB drive; if I remember correctly, you have to copy the partition to unallocated space on the destination drive, or gparted won't let you do the copy/paste. If that works OK, you can reinstall Grub to the MBR of your 500 GB drive, and also you could resize the Ubuntu partition so it takes the whole drive if you wanted to. If I were in your shoes, I think I would instead keep the Ubuntu partition as 100 GB or even smaller, and then set up multiple data partitions where you can put all your personal files like music, videos, pictures, etc. That's just an idea, but you can do it how you want. Good luck and let me know how it goes. :)

---

### Post by relaxedcrazyman on 2009-01-14
well, the reason i wanted to move it to its own drive, is that i am getting horrible transfer rates between the partition and my other drives. i dont know if this is a problem with the different drive formats, or if it is because it is on a partition. any ideas?

---

### Post by caljohnsmith on 2009-01-14
> **relaxedcrazyman said:**
> well, the reason i wanted to move it to its own drive, is that i am getting horrible transfer rates between the partition and my other drives. i dont know if this is a problem with the different drive formats, or if it is because it is on a partition. any ideas?
Can you maybe provide some more details? When you say horrible transfer rate, do you mean when you are copying files from the Ubuntu partition to another drive, or is it vice-versa? Do you know what the transfer rates are, and under what circumstances does it happen? And is reading/writing just to your Ubuntu partition from the Ubuntu partition as fast as you would expect, or is that a problem too?

---

### Post by relaxedcrazyman on 2009-01-14
copying from ubuntu to the other part of the same drive, and to my other drives. when transferring from ubuntu partition to other drives i usually get about 5-9 mb/s, as opposed to when i do from my other drives to my other drives i usually get 22-30 mb/s


when i copy something to the ubuntu drive from the other drives it is around 22-30mb/s as well.


i just thought of this, what if i shrunk the partition ubuntu is on and just saved all my files and such to my other drives?

---

### Post by caljohnsmith on 2009-01-14
> **relaxedcrazyman said:**
> 
i just thought of this, what if i shrunk the partition ubuntu is on and just saved all my files and such to my other drives?
If you're mostly concerned with the transfer rate associated with copying/moving your personal files, then your idea of putting your personal files on a faster drive seems like it should work just fine. But if you are also concerned that your Ubuntu drive's data rate is affecting your Ubuntu performance significantly, then maybe moving your entire Ubuntu install to a faster drive might be worth it. It's up to you whether you think it is worth the effort.

---

### Post by relaxedcrazyman on 2009-01-14
first i just wanted to say, thanks for all your help and your speedy responses.


i think the problem i was having was that i was dling stuff to my ubuntu partition and then copying it else where, the speed of ubuntu itself is great. so i think that when i dl stuff, i will dl it to other drives. because of that, i think i want to shrink the size of my ubuntu install. how can i go about reducing it from 100gb to maybe 20gb(what would be a good size to leave the partition if i am only using it to boot and use ubuntu?) can i use gparted? how do i use gparted?

---

### Post by caljohnsmith on 2009-01-14
Sure, you should be able to use gparted to shrink your Ubuntu install, just make sure to do it from the Live CD; also, when you first open gparted on the Live CD (System > Admin > Partition Editor), right-click your swap partition and select "swapoff", and then gparted should give you full freedom to do whatever you want. I'm assuming that you would move all your personal files to a another drive/partition beforehand? If so, it seems like you should be safe doing the repartitioning since your important stuff will be elsewhere. Good luck and let me know how that goes.

---

### Post by relaxedcrazyman on 2009-01-14
well, it worked, kinda. i turned off the swap, and shrunk the volume, but now i have 85gb of unallocated space. how do i get it back with the original 1tb? can i do it safely?

---

### Post by caljohnsmith on 2009-01-14
> **relaxedcrazyman said:**
> well, it worked, kinda. i turned off the swap, and shrunk the volume, but now i have 85gb of unallocated space. how do i get it back with the original 1tb? can i do it safely?
I'm not quite understanding; you have sdb1, an NTFS partition, on your 1 TB drive in addition to your Ubuntu partition. If you shrunk the Ubuntu partition to leave 85 GB free, you could make that into a new logical partition in order to use that space. Or do you want to add that disk space to your sdb1 NTFS partition? That wouldn't be possible if you shrunk the Ubuntu partition from the end. To clarify your new partition arrangement, how about posting the output of:
```
sudo fdisk -lu
```

---

### Post by relaxedcrazyman on 2009-01-14
so the sdb1 is the tb drive where ubuntu is partitioned, i wanted to shrink ubuntu install by 85gb and put it back into the sdb1 1tb harddrive, if that makes sense. here is fdisk:

themaster@themaster-desktop:~$ sudo fdisk -lu
[sudo] password for themaster: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1734522048  1765238264    15358108+  83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52baa59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   490231807   245114880    7  HPFS/NTFS

---

### Post by caljohnsmith on 2009-01-14
OK, that's what I thought might have happened; you shrunk the Ubuntu sdb5 partition from the end, so you freed up space after Ubuntu, not before it, and the sdb1 NTFS partition is before it. Maybe the easiest way to accomplish what you want to do at this point is to simply copy your ~15 GB Ubuntu partition to the end of the freed space right before the swap partition (copy Ubuntu so it is right before the swap partition), and then you could delete the original Ubuntu partition once you've confirmed that the copy was successful. After that, you would have to shrink the sdb2 partition from the beginning in order to free up the space before it, and then finally you could add that space to your sdb1 NTFS partition. How about trying that and let me know how it goes.

---

### Post by relaxedcrazyman on 2009-01-14
i copied my ubuntu to right before the swap, the 85gb is still unallocated, i couldnt figure out how "to shrink the sdb2 partition from the beginning in order to free up the space before it, and then finally you could add that space to your sdb1 NTFS partition. How about trying that and let me know how it goes."

---

### Post by caljohnsmith on 2009-01-14
OK, how about posting the new output of:
```
sudo fdisk -lu
```
So I can see what you've done so far.

---

### Post by relaxedcrazyman on 2009-01-14
themaster@themaster-desktop:~$ sudo fdisk -lu
[sudo] password for themaster: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      1734521985  1953520064   109499040    5  Extended
/dev/sdb5      1913807385  1944523664    15358140   83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52baa59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   490231807   245114880    7  HPFS/NTFS

---

### Post by caljohnsmith on 2009-01-15
> **relaxedcrazyman said:**
> 

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1734521579   867259766    7  HPFS/NTFS
/dev/sdb2      [COLOR="Blue"]1734521985[/COLOR]  1953520064   109499040    5  Extended
/dev/sdb5      [COLOR="Blue"]1913807385[/COLOR]  1944523664    15358140   83  Linux
/dev/sdb6      1944523728  1953520064     4498168+  82  Linux swap / Solaris
```

OK, that looks great. As I've shown highlighted, if you move the starting point of sdb2 so that it comes right before the sdb5 Ubuntu partition, you will free up all that space that is before your Ubuntu partition so that you can then expand the sdb1 NTFS partition. So when you are in gparted, try shrinking sdb2 by moving its starting point to the right, so that it fits snugly up next to sdb5. Then you can move the end point of sdb1 to the right to expand sdb1 and take over all that freed space. How about trying that and let me know how it goes.

---

### Post by relaxedcrazyman on 2009-01-16
> **caljohnsmith said:**
> OK, that looks great. As I've shown highlighted, if you move the starting point of sdb2 so that it comes right before the sdb5 Ubuntu partition, you will free up all that space that is before your Ubuntu partition so that you can then expand the sdb1 NTFS partition. So when you are in gparted, try shrinking sdb2 by moving its starting point to the right, so that it fits snugly up next to sdb5. Then you can move the end point of sdb1 to the right to expand sdb1 and take over all that freed space. How about trying that and let me know how it goes.

I still cant figure out what i am doing wrong, sdb5 is unallocated space that comes right after the 827gb, and right before ubuntu, i cant figure out how to move it, and when i try to have the 827gb eat the unallocated space, i cant expand it to do so. what am i doing wrong here? i also tried to allocate the 85gb as a ntfs then absorb it into the 827gb but that didnt work eiter

---

### Post by caljohnsmith on 2009-01-16
> **relaxedcrazyman said:**
> I still cant figure out what i am doing wrong, sdb5 is unallocated space that comes right after the 827gb, and right before ubuntu, i cant figure out how to move it, and when i try to have the 827gb eat the unallocated space, i cant expand it to do so. what am i doing wrong here? i also tried to allocate the 85gb as a ntfs then absorb it into the 827gb but that didnt work eiter
Did you try moving the starting point of the sdb2 extended partition so that it is right next to the sdb5 partition starting point? How about posting a screen shot of your gparted screen so I can maybe get a better idea of what the problem is.

---

### Post by relaxedcrazyman on 2009-01-16
[IMG]http://www.hdimage.org/images/kxs9ck8r59g7agod4u0k_1.png[/IMG]
[IMG]http://www.hdimage.org/images/0c3yjzlgps20h57gst1w_2.png[/IMG]
[IMG]http://www.hdimage.org/images/8znof82eiven6460btv5_3.png[/IMG]
[IMG]http://www.hdimage.org/images/xhihgv0x9qrxpowdzmdi_4.png[/IMG]

---

### Post by relaxedcrazyman on 2009-01-16
i hope these work

[http://www.imagebam.com/image/5062cb23858126]("http://www.imagebam.com/image/5062cb23858126")

[http://www.imagebam.com/image/8248ef23858129]("http://www.imagebam.com/image/8248ef23858129")

[http://www.imagebam.com/image/65d76523858135]("http://www.imagebam.com/image/65d76523858135")

[http://www.imagebam.com/image/d9359723858137]("http://www.imagebam.com/image/d9359723858137")

---

### Post by caljohnsmith on 2009-01-16
It looks like you need to right-click your sdb6 swap partition and select "swapoff". Once you do that, click on sdb2, and shrink it towards the right so that it fits right up next to sdb5, and then you should be able to expand sdb1.

---

### Post by relaxedcrazyman on 2009-01-17
it took about 9 hours, but it worked, thanks a bundle for all your help. if you are ever in riverside, or san francisco, ill buy you a beer!
THANKS!!!

---

### Post by caljohnsmith on 2009-01-17
> **relaxedcrazyman said:**
> it took about 9 hours, but it worked, thanks a bundle for all your help. if you are ever in riverside, or san francisco, ill buy you a beer!
THANKS!!!
Congratulations on your final partitioning success. Cheers, and hope you don't run into any more major problems. :)

:popcorn:

---

