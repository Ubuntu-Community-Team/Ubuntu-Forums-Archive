---
title: "Grub Problems"
date: 2009-03-25
forum: General Help
---

### Post by Gortzilla on 2009-03-25
I have Windows XP, Windows 7 Beta, Ubuntu 8.10, and Ubuntu Ultimate (8.10) installed. The first three are on the first drive, and Ubuntu Ultimate on the second drive. My configuration worked up until yesterday when I got home. When I turned on my computer Gurb wouldn't boot. I could still boot a live CD, and figured a simple reconfiguration of Grub was all that was needed. I did:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit 
```
I thought this was the configuration before hand. After reboot, I got my Grub list, but could only boot Ubuntu Ultimate. Trying the Windows Bootloader(which I use to then choose the Windows OS) resulted in an error 13 "Invaild or unsupported executable format". Trying my Ubuntu 8.10 (on /dev/sda5) resulted in an error 22 partition error. I would like to restore functionality to the Grub menu again. Thanks for any help.
This isn't my first time with Grub issues :oops:
Last time Boot Info Script proved useful. Here is the result.txt when run from Ubuntu Ultimate.
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 337440840 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97d997d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   309,620,744   309,620,682   7 HPFS/NTFS
/dev/sda2         309,620,745   488,392,064   178,771,320   5 Extended
/dev/sda5         309,620,808   387,439,604    77,818,797  83 Linux
/dev/sda6         387,439,668   486,271,484    98,831,817   7 HPFS/NTFS
/dev/sda7         486,271,548   488,392,064     2,120,517  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001cfaf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   136,729,214   136,729,152  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="8AF09098F0908BD7" TYPE="ntfs" 
/dev/sda5: UUID="2dc38d9a-42e7-4ee9-b385-3956efd268f7" TYPE="ext3" 
/dev/sda6: UUID="02E3F86477312125" TYPE="ntfs" 
/dev/sda7: UUID="2380fd1a-3486-4568-98db-c585573a7c0b" TYPE="swap" 
/dev/sdb1: UUID="f1088cd1-5ed6-41d3-86f2-a740dde93e71" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tim)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/black light-green/black

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
# kopt=root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro

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
# defoptions=splash vga=769 quiet

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro splash vga=769 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro splash vga=769 quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro splash vga=769 quiet 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, kernel 2.6.24-21-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro splash vga=769 quiet 
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2dc38d9a-42e7-4ee9-#b385-3956efd268f7 ro  single
#initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 
root		(hd0,0)
savedefault
makeactive
chainloader	+1




=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8a9ff822-37de-4625-82a9-4d70557bf25d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 172.8GB: boot/grub/menu.lst
 184.1GB: boot/grub/stage2
 172.8GB: boot/initrd.img-2.6.24-21-generic
 172.8GB: boot/initrd.img-2.6.24-21-generic.bak
 172.8GB: boot/initrd.img-2.6.27-11-generic
 172.7GB: boot/initrd.img-2.6.27-7-generic
 172.8GB: boot/initrd.img-2.6.27-9-generic
 172.8GB: boot/vmlinuz-2.6.24-21-generic
 172.8GB: boot/vmlinuz-2.6.27-11-generic
 172.7GB: boot/vmlinuz-2.6.27-7-generic
 172.7GB: boot/vmlinuz-2.6.27-9-generic
 172.8GB: initrd.img
 172.8GB: initrd.img.old
 172.8GB: vmlinuz
 172.7GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f1088cd1-5ed6-41d3-86f2-a740dde93e71

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
uuid		f1088cd1-5ed6-41d3-86f2-a740dde93e71
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f1088cd1-5ed6-41d3-86f2-a740dde93e71
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f1088cd1-5ed6-41d3-86f2-a740dde93e71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f1088cd1-5ed6-41d3-86f2-a740dde93e71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f1088cd1-5ed6-41d3-86f2-a740dde93e71
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
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro splash vga=769 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro splash vga=769 quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2dc38d9a-42e7-4ee9-b385-3956efd268f7 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f1088cd1-5ed6-41d3-86f2-a740dde93e71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=2380fd1a-3486-4568-98db-c585573a7c0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  24.2GB: boot/grub/menu.lst
  24.2GB: boot/grub/stage2
  24.2GB: boot/initrd.img-2.6.27-11-generic
  24.2GB: boot/initrd.img-2.6.27-7-generic
  24.2GB: boot/vmlinuz-2.6.27-11-generic
  24.2GB: boot/vmlinuz-2.6.27-7-generic
  24.2GB: initrd.img
  24.2GB: initrd.img.old
  24.2GB: vmlinuz
  24.2GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-03-25
It seems your computer is booting from the second hard drive.  Setting your bios to boot from the first hard drive (the 250 GB drive  with the three OSs) should solve your problem.

---

### Post by Gortzilla on 2009-03-25
Thank you. I didn't think of changing that, since it worked with the 500GB as the boot before. Silly me for not trying a simple solution. Thanks again.

---

### Post by meierfra. on 2009-03-25
> Thanks again.
You are welcome. Have fun with all your OSs.

---

