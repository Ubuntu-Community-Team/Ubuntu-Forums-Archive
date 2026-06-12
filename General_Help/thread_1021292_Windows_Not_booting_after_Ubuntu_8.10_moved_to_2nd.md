---
title: "Windows Not booting after Ubuntu 8.10 moved to 2nd HD"
date: 2008-12-25
forum: General Help
---

### Post by Fahim123 on 2008-12-25
Hi Guys,
  I bought new hard disk which is 250gb and my old one is 160gb i installed previously windows xp and ubuntu in my first Hd (160gb) now i fresh installed ubuntu 8.10 in my second Hd(250gb) everything went fine and i installed grub in 2nd HD now the problem is i cannot load selecting my windows xp or the Ubuntu which is in my Hd(160gb) how to make it to load again.Thanks in advance.

---

### Post by TeXtonyx on 2008-12-25
If the situation is actually as you describe, grub in the mbr
of the second drive, then if your bios is set to hd0 then you
should boot Ubuntu and XP just before. 

If your bios is set to boot hd1 (second drive) then apparently
your grub menu.lst doesn't have entries for ubuntu and xp, which
means you have to add entries for them. Did you have your first
drive unplugged when you installed 8.10 to the second drive?

I won't be around, but caljohnsmith, an expert in such matters, 
will usually help. I will drop in much later.
Anyway, if you need help with grub entries start with:
------------------------------------------------
caljohnsmith wrote:

"In order to get a clearer picture of your setup, how about opening 
a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
Code:

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your Windows booting problem might be."

------------------------------------------------------------

---

### Post by Fahim123 on 2008-12-25
Hi Guys,
   I cannot boot into my first hard drive i paste you my Results.Txt please take a look at it and let me know how to fix it.Thanks in advance.
/dev/sdc has no valid partition table.
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on boot drive #1 in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sdb2:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb3:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb4:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000209dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156248189    78124063+  83  Linux

/dev/sda: OK


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1da51da4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sdb2        81915435   163830869    40957717+   7  HPFS/NTFS
/dev/sdb3       163830870   245746304    40957717+   7  HPFS/NTFS
/dev/sdb4       245746305   312576704    33415200   83  Linux

/dev/sda: OK
partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb: OK


/dev/sda: OK
partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

/dev/sda1: UUID="a587b688-1fc0-4ce0-b924-99e3b8c755c3" TYPE="ext3" 
/dev/sdb1: UUID="EA8809C188098CEF" TYPE="ntfs" 
/dev/sdb2: UUID="60B02A76B02A52B8" TYPE="ntfs" 
/dev/sdb3: UUID="BC0C83820C833684" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb4: UUID="3680c59d-0946-4146-a9a8-1ce45f1716f9" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mohamed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mohamed)

sda1/boot/grub/menu.lst

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
# kopt=root=UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a587b688-1fc0-4ce0-b924-99e3b8c755c3

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
uuid		a587b688-1fc0-4ce0-b924-99e3b8c755c3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a587b688-1fc0-4ce0-b924-99e3b8c755c3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a587b688-1fc0-4ce0-b924-99e3b8c755c3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a587b688-1fc0-4ce0-b924-99e3b8c755c3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a587b688-1fc0-4ce0-b924-99e3b8c755c3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title		Ubuntu 8.10, kernel 2.6.27-10-generic (on /dev/sdb4)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode) (on /dev/sdb4)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro single 
initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title		Ubuntu 8.10, kernel 2.6.27-8-generic (on /dev/sdb4)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode) (on /dev/sdb4)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro single 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb4.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb4)
root		(hd1,3)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a587b688-1fc0-4ce0-b924-99e3b8c755c3 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda1/boot

total 23796
drwxr-xr-x  3 root root    4096 2008-12-25 18:34 .
drwxr-xr-x 20 root root    4096 2008-12-25 18:33 ..
-rw-r--r--  1 root root  507665 2008-11-05 05:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-21 07:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-05 05:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-21 07:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-25 18:33 grub
-rw-r--r--  1 root root 8198836 2008-12-25 18:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8198784 2008-12-25 18:34 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 04:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-05 05:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-21 07:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-05 05:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-21 07:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-05 05:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-21 07:46 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-25 18:33 .
drwxr-xr-x 3 root root   4096 2008-12-25 18:34 ..
-rw-r--r-- 1 root root    197 2008-12-25 17:58 default
-rw-r--r-- 1 root root     30 2008-12-25 17:58 device.map
-rw-r--r-- 1 root root   8108 2008-12-25 17:58 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-25 17:58 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-25 17:58 installed-version
-rw-r--r-- 1 root root   8712 2008-12-25 17:58 jfs_stage1_5
-rw-r--r-- 1 root root   6761 2008-12-25 18:33 menu.lst
-rw-r--r-- 1 root root   6677 2008-12-25 18:33 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-25 17:58 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-25 17:58 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-25 17:58 stage1
-rw-r--r-- 1 root root 121460 2008-12-25 17:58 stage2
-rw-r--r-- 1 root root   9556 2008-12-25 17:58 xfs_stage1_5

sdb1/boot.ini

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sdb4/boot/grub/menu.lst

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
# kopt=root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 ro  single
initrd		/boot/initrd.img-2.6.27-8-generic


title		Ubuntu 8.10, memtest86+
root		(hd0,3)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


sdb4/etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=3680c59d-0946-4146-a9a8-1ce45f1716f9 / ext3 relatime,errors=remount-ro 0 1
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda3 /media/New\040Volume ntfs-3g defaults,locale=en_HK.UTF-8 0 0

sdb4/boot

total 65732
drwxr-xr-x  3 root root    4096 2008-12-21 16:06 .
drwxr-xr-x 21 root root    4096 2008-12-21 16:04 ..
-rw-r--r--  1 root root  422838 2008-10-22 11:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507990 2008-11-21 21:46 abi-2.6.27-10-generic
-rw-r--r--  1 root root  508385 2008-12-20 01:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-05 05:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507735 2008-11-07 03:20 abi-2.6.27-8-generic
-rw-r--r--  1 root root   80062 2008-10-22 11:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91358 2008-11-21 21:46 config-2.6.27-10-generic
-rw-r--r--  1 root root   91358 2008-12-20 01:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-05 05:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-07 03:20 config-2.6.27-8-generic
drwxr-xr-x  2 root root    4096 2008-12-21 16:05 grub
-rw-r--r--  1 root root 7653639 2008-10-29 19:06 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7655775 2008-10-01 00:07 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8203303 2008-11-28 19:20 initrd.img-2.6.27-10-generic
-rw-r--r--  1 root root 8206639 2008-12-21 16:06 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8184436 2008-11-05 19:16 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8203983 2008-11-17 22:29 initrd.img-2.6.27-8-generic
-rw-r--r--  1 root root  124152 2008-09-12 04:11 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-10-22 11:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029828 2008-11-21 21:46 System.map-2.6.27-10-generic
-rw-r--r--  1 root root 1031799 2008-12-20 01:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-05 05:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029612 2008-11-07 03:20 System.map-2.6.27-8-generic
-rw-r--r--  1 root root    1074 2008-11-21 21:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r--  1 root root    1074 2008-12-20 01:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-05 05:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-07 03:22 vmcoreinfo-2.6.27-8-generic
-rw-r--r--  1 root root 1920760 2008-10-22 11:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2247280 2008-11-21 21:46 vmlinuz-2.6.27-10-generic
-rw-r--r--  1 root root 2248912 2008-12-20 01:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-05 05:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-07 03:20 vmlinuz-2.6.27-8-generic

sdb4/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-21 16:05 .
drwxr-xr-x 3 root root   4096 2008-12-21 16:06 ..
-rw-r--r-- 1 root root    197 2008-06-29 06:07 default
-rw-r--r-- 1 root root     15 2008-06-29 06:07 device.map
-rw-r--r-- 1 root root   8056 2008-06-29 06:07 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-06-29 06:07 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-06-29 06:07 installed-version
-rw-r--r-- 1 root root   8608 2008-06-29 06:07 jfs_stage1_5
-rw-r--r-- 1 root root   4936 2008-12-21 16:05 menu.lst
-rw-r--r-- 1 root root   4936 2008-12-21 16:04 menu.lst~
-rw-r--r-- 1 root root   7324 2008-06-29 06:07 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-06-29 06:07 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-06-29 06:07 stage1
-rw-r--r-- 1 root root 108356 2008-06-29 06:07 stage2
-rw-r--r-- 1 root root   9276 2008-06-29 06:07 xfs_stage1_5

StdErr Messages 

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 00: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 8cd: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 8cd: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 8cd: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 00: command not found

---

### Post by caljohnsmith on 2008-12-25
What happens when you choose the Windows or Ubuntu 8.10 (on /dev/sdb4) entries in your Grub menu? Do you get a Grub error, like error 22 for example? If that's the case, it looks like the reason would be because you are booting your 160 GB sdb drive on start up instead of the 250 GB sda drive. How about going into your BIOS and switch the boot order so that the 250 GB sda drive boots first on start up, and I think that will solve your problem; let me know how that goes or if you run into problems.

P.S. Merry Christmas, TeXtonyx, and to you too Fahim123. :)

---

### Post by Fahim123 on 2008-12-25
Hi Caljon,
  Thank you very much man its solved my problem i am now able to boot winxp and also my previous linux(ubunut 8.10) in my old HD160gb.Thank you so much

---

### Post by Fahim123 on 2008-12-25
Hi Caljohn,
  I forgot to say how it got solved according to your instruction i just changed the boot priority to 250gb. Thanks onceagain

---

### Post by caljohnsmith on 2008-12-25
Glad to hear that did the trick; cheers and have fun with Ubuntu. :)

---

