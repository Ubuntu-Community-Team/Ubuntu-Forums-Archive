---
title: "GRUB Error 21 - sometimes"
date: 2009-05-08
forum: General Help
---

### Post by gazer22 on 2009-05-08
Each time I shutdown and then power on the computer, I get:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 21

```

If I then hit the power button to shut down, and then again to start it again, booting works fine, and 9.04 starts up as expected.

The process repeats upon next shutdown (but not reboots).

[COLOR="DarkRed"]**11 May 2009: Disabling "Quick Boot" in the BIOS fixes the problem, though it does increase the boot time.**[/COLOR]

So far, I've tried to re-install grub from the live-cd ([http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")), but that made no difference.

In summary, my system has three drives.  The first (sda) has an older ubuntu install, which no longer works (the 9.04 upgrade failed rather drastically) and a windows partition.

The second (sdb) has my old /home directory

The third (sdc) has the new 9.04 install and /home directory, which is what I'd like to boot into.

Results from [boot_info_script032.sh]("https://sourceforge.net/projects/bootinfoscript/") here:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa475a475

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2          30,716,280   390,700,799   359,984,520   f W95 Ext d (LBA)
/dev/sda5          30,716,343   153,597,464   122,881,122   7 HPFS/NTFS
/dev/sda6         153,597,528   153,902,699       305,172  83 Linux
/dev/sda7         153,902,763   164,136,104    10,233,342  83 Linux
/dev/sda8         164,136,168   168,232,679     4,096,512  82 Linux swap / Solaris
/dev/sda9         168,232,743   169,260,839     1,028,097  83 Linux
/dev/sda10        169,260,903   390,700,799   221,439,897  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a9c6c08

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   310,488,254   310,488,192  83 Linux
/dev/sdb2         310,488,255   312,576,704     2,088,450  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b528

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     8,000,369     8,000,307  82 Linux swap / Solaris
/dev/sdc2           8,000,370 1,953,520,064 1,945,519,695   5 Extended
/dev/sdc5           8,000,433   207,993,554   199,993,122  83 Linux
/dev/sdc6         207,993,618 1,953,520,064 1,745,526,447  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="500CDB600CDB3FA0" LABEL="Windows Disk" TYPE="ntfs" 
/dev/sda5: UUID="C410414310413DA4" LABEL="Data Disk" TYPE="ntfs" 
/dev/sda6: UUID="f4c6b778-ca0a-4433-97ea-739afae40f28" TYPE="ext3" 
/dev/sda7: UUID="5ca9b6ad-0a0f-487d-b84b-29c219887992" TYPE="ext3" 
/dev/sda8: LABEL="SWAP-sda8" UUID="b4f28365-28b1-43b3-a5e2-703c389819f9" TYPE="swap" 
/dev/sda9: UUID="43c4b0a9-7f76-43c4-9f9f-6738bfd27a1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="5ee98120-36a8-4551-b6c4-ad3f8fe8bc0e" TYPE="ext3" 
/dev/sdb1: LABEL="/" UUID="ff357d91-218a-43e6-98e8-bc3cd5c4a08e" TYPE="ext3" 
/dev/sdb2: LABEL="SWAP-sdb2" UUID="6f73d43c-a0f7-4658-85b6-e393265eb9f9" TYPE="swap" 
/dev/sdc1: UUID="16c934c4-e48a-4ae6-a7e3-6b04eebaf630" TYPE="swap" 
/dev/sdc5: UUID="f3cf09d4-ee21-49a5-bd73-36b2907c12b2" TYPE="ext4" 
/dev/sdc6: UUID="195def18-5913-4239-bc3b-e6bf0d5870ad" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sdc6 on /home type ext4 (rw,relatime)
/dev/sdb1 on /home2 type ext3 (rw,relatime)
/dev/sda7 on /root_old type ext3 (rw,relatime)
/dev/sda10 on /usr_old type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jkarpick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jkarpick)
/dev/sda6 on /boot_old type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


============================= sda6/grub/menu.lst: =============================

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
timeout		6

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

title		New 1TB Hard Drive
root        (hd2,0)
chainloader +1


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
# kopt=root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro

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
# defoptions=splash

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro  single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda6: Location of files loaded by Grub: ===================


  78.7GB: grub/menu.lst
  78.7GB: grub/stage2
  78.7GB: initrd.img-2.6.24-23-generic
  78.7GB: initrd.img-2.6.24-23-generic.bak
  78.6GB: initrd.img-2.6.27-11-generic
  78.6GB: initrd.img-2.6.28-11-generic
  78.7GB: vmlinuz-2.6.24-23-generic
  78.6GB: vmlinuz-2.6.27-11-generic
  78.6GB: vmlinuz-2.6.28-11-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f4c6b778-ca0a-4433-97ea-739afae40f28 /boot           ext3    relatime        0       2
# /dev/sdb1
UUID=ff357d91-218a-43e6-98e8-bc3cd5c4a08e /home           ext3    relatime        0       2
# /dev/sda9
UUID=43c4b0a9-7f76-43c4-9f9f-6738bfd27a1f /tmp            ext3    relatime        0       2
# /dev/sda10
UUID=5ee98120-36a8-4551-b6c4-ad3f8fe8bc0e /usr            ext3    relatime        0       2
# /dev/sda8
UUID=b4f28365-28b1-43b3-a5e2-703c389819f9 none            swap    sw              0       0
# /dev/sdb2
UUID=6f73d43c-a0f7-4658-85b6-e393265eb9f9 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdc5/boot/grub/menu.lst: ===========================

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
#timeout		10
timeout		4

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
# kopt=root=UUID=f3cf09d4-ee21-49a5-bd73-36b2907c12b2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3cf09d4-ee21-49a5-bd73-36b2907c12b2

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
# defoptions=splash

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f3cf09d4-ee21-49a5-bd73-36b2907c12b2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f3cf09d4-ee21-49a5-bd73-36b2907c12b2 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f3cf09d4-ee21-49a5-bd73-36b2907c12b2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f3cf09d4-ee21-49a5-bd73-36b2907c12b2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f3cf09d4-ee21-49a5-bd73-36b2907c12b2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro single 
initrd		/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro single 
initrd		/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro splash 
initrd		/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda7)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 ro single 
initrd		/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 9.04, memtest86+ (on /dev/sda7)
root		(hd0,5)
kernel		/memtest86+.bin  
savedefault
boot


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=f3cf09d4-ee21-49a5-bd73-36b2907c12b2 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=195def18-5913-4239-bc3b-e6bf0d5870ad /home           ext4    relatime        0       2
# /home2 was on /dev/sdb1 during installation
UUID=ff357d91-218a-43e6-98e8-bc3cd5c4a08e /home2          ext3    relatime        0       2
# /root_old was on /dev/sda7 during installation
UUID=5ca9b6ad-0a0f-487d-b84b-29c219887992 /root_old       ext3    relatime        0       2
# /usr_old was on /dev/sda10 during installation
UUID=5ee98120-36a8-4551-b6c4-ad3f8fe8bc0e /usr_old        ext3    relatime        0       2
# swap was on /dev/sda8 during installation
UUID=b4f28365-28b1-43b3-a5e2-703c389819f9 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=6f73d43c-a0f7-4658-85b6-e393265eb9f9 none            swap    sw              0       0
# swap was on /dev/sdc1 during installation
UUID=16c934c4-e48a-4ae6-a7e3-6b04eebaf630 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/menu.lst
   5.8GB: boot/grub/stage2
  24.0GB: boot/initrd.img-2.6.28-11-generic
   5.9GB: boot/vmlinuz-2.6.28-11-generic
  24.0GB: initrd.img.old
   5.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  08 6c 9c 1a 00 00 80 01  |.........l......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 80 ac 81 12 00 fe  |......?.........|
000001d0  ff ff 82 fe ff ff bf ac  81 12 02 de 1f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda8

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200

Unknown BootLoader  on sdb2

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200


```

---

### Post by caljohnsmith on 2009-05-08
According to the Boot Info Script, you have Grub installed to the MBR (Master Boot Record) of your 200 GB sda drive, but Grub is configured to look on the 5th partition on the 3rd boot drive for its boot files; that of course would be your sdc drive. Note that a Grub error 21 is "Selected disk does not exist", so that would suggest that your sdc drive does not become ready/accessible quick enough at power-on when Grub on the sda drive looks for its boot files on the sdc drive.

I notice that you have another Ubuntu 9.04 install on sda7 with a boot partition in sda6; how would you feel about having Grub use the boot partition in sda6 for its boot files rather than having Grub look on the sdc drive on start up? That should fix your Grub problem. All you would need to do is add a boot option to the menu.lst in sda6 in order to boot your Ubuntu on sdc5. If that sounds good to you, how about doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then reboot, and see if you can boot into your Ubuntu install on sda7. See if you can get that far, and we can work from there if you want.

John

---

### Post by gazer22 on 2009-05-08
> **caljohnsmith said:**
> ...

I notice that you have another Ubuntu 9.04 install on sda7 with a boot partition in sda6; how would you feel about having Grub use the boot partition in sda6 for its boot files rather than having Grub look on the sdc drive on start up? That should fix your Grub problem. All you would need to do is add a boot option to the menu.lst in sda6 in order to boot your Ubuntu on sdc5. If that sounds good to you, how about doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then reboot, and see if you can boot into your Ubuntu install on sda7. See if you can get that far, and we can work from there if you want.

John

That definitely gets me booting into the bad 9.04 install on sda7.  (For some reason, the mouse & keyboard don't work after that boots up.  The /var/cache got deleted there, which caused all sorts of problems...)

I tried adding a line to the grub menu on sda6:
```

title New 9.04
root (hd2,0)
chainloader +1

```
(also tried (hd2,4) )

Trying that gives:
```
Error 21: Selected disk does not exist
```

Is there a way to get that to work?

Thanks.

---

### Post by caljohnsmith on 2009-05-08
Is your Ubuntu on sda7 an upgrade or was it a fresh install? If it was a fresh install, how about trying the following entry to boot Ubuntu on sdc5:
```
title Ubuntu 9.04 on sdc5
uuid f3cf09d4-ee21-49a5-bd73-36b2907c12b2
configfile /boot/grub/menu.lst
```
Let me know if that works or not.

John

---

### Post by gazer22 on 2009-05-08
> **caljohnsmith said:**
> Is your Ubuntu on sda7 an upgrade or was it a fresh install?
It is a failed upgrade, hence its mostly non-working status.  (The root partition filled up during the upgrade process, then things bombed out).


> **caljohnsmith said:**
>  If it was a fresh install, how about trying the following entry to boot Ubuntu on sdc5:
```
title Ubuntu 9.04 on sdc5
uuid f3cf09d4-ee21-49a5-bd73-36b2907c12b2
configfile /boot/grub/menu.lst
```
Let me know if that works or not.


Tried it anyway :o .  It now throws an Error 15:
```
Error 15: File not found
```

-g

---

### Post by caljohnsmith on 2009-05-08
The fact that you got another Grub error 21 when you tried those entries in your post #3 concerns me, because that would mean the sdc drive was not accessible; that would suggest it is not simply a matter of time for the sdc drive to become accessible. How about rebooting, and when you get the Grub menu on start up, press "c" to get the Grub command line, and do:
```
grub> geometry (hd1)
```
That should list your sdb drive, so it should show two partitions, the first one type "83" and the second one of type "82". If that works, try:
```
grub> geometry (hd2)
```
An that should list your sdc drive, which has three partitions. If that instead gives you a Grub error 21, try pressing CTRL-ALT-DELETE to reboot the computer, and again try the above geometry command. Let me know if you can get the geometry (hd2) command to show your sdc drive or not.

John

---

### Post by gazer22 on 2009-05-08
> **caljohnsmith said:**
> The fact that you got another Grub error 21 when you tried those entries in your post #3 concerns me, ... when you get the Grub menu on start up, press "c" to get the Grub command line, and do:
```
grub> geometry (hd1)
```
That should list your sdb drive, so it should show two partitions, the first one type "83" and the second one of type "82". If that works, try:
```
grub> geometry (hd2)
```
An that should list your sdc drive, which has three partitions. If that instead gives you a Grub error 21, try pressing CTRL-ALT-DELETE to reboot the computer, and again try the above geometry command. Let me know if you can get the geometry (hd2) command to show your sdc drive or not.


Weird.  I put the following in menu.lst on sda6:
```

title New Ubuntu Hard Drive
root (hd2,4)
chainloader +1

```

grub is configured: root (hd0,5)

From a cold start, grub throws an Error 21, and does the same for the "geometry (hd2)" command.

From a warm re-start, grub now throws an Error 13: Invalid or unsupported executable format, and "geometry (hd2)" shows the partitions on my new drive.

---

### Post by caljohnsmith on 2009-05-08
> **gazer22 said:**
> 
From a cold start, grub throws an Error 21, and does the same for the "geometry (hd2)" command.

From a warm re-start, grub now throws an Error 13: Invalid or unsupported executable format, and "geometry (hd2)" shows the partitions on my new drive.
Those results are actually entirely consistent with the previous Grub error 21 you were getting from your first post. It looks like the bottom line is that your sdc drive does not become accessible to Grub until you do a warm restart. That behavior sounds like it could be some strange BIOS quirk, because Grub relies solely on your BIOS on start up in order to access your drives. 

You might want to check the manufacturer's website of your motherboard to see if there is an upgrade available for your BIOS, because it seems like your BIOS could be the problem. In the meantime, if you want to boot your new Ubuntu using the entry you gave in your previous post, you'll first need to install Grub to the boot sector of the Ubuntu partition by doing the following:
```
sudo grub
grub> root (hd2,4)
grub> setup (hd2,4)
grub> quit
```
Let me know if that works or not.

John

---

### Post by gazer22 on 2009-05-09
Well, I've upgraded the BIOS and disconnected all of the other drives, but no cigar.

The motherboard is an MSI K8NGM2-FID w/ NVidia GeForce 6150 & nForce 430

BIOS upgraded to 3.8 from 3.6.  The new bios is dated 2008-10-28.

The drive is a new Seagate 1TB Barricuda, SATAII.

Re-jiggered grub (via ubuntu install disk) to root (hd0,4) and setup (hd0) now that the drive is the only one in the system.

Unfortunately, same symptoms persist.  The system will start from a warm state, but not a cold start.

I think my next step is to get in touch with MSI?

Thanks.

---

### Post by caljohnsmith on 2009-05-09
> **gazer22 said:**
> 
I think my next step is to get in touch with MSI?

It sounds like that might be about your only option at this point; I'm doubtful MSI's tech support will be able to help you, but it's certainly worth a try. I just did a quick Google search on your motherboard, and it looks like [MSI has their own forums]("http://forum-en.msi.com/index.php?PHPSESSID=a6f7c4c2a6203a754262e65104de049d") where you could ask about your particular issue; at least in my experience, sometimes you'll get better support in a company's forums from other users than you will from a company's own tech support. Anyway, good luck and keep me posted if you come up with anything.

John

---

### Post by gazer22 on 2009-05-11
Well, I found a work-around that actually works:
[INDENT]**Disable "Quick Boot" in the BIOS**[/INDENT]

This makes the boot-up process take longer (and you get to watch it count your memory!), which allows the drive to spin up in time for the BIOS to recognize it.

Kind of annoying, but at least it looks like my system is booting reliably (if a bit slower) now.

---

