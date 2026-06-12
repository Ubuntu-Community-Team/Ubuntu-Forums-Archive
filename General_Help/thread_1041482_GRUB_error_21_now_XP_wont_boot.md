---
title: "GRUB error 21 now XP wont boot"
date: 2009-01-16
forum: General Help
---

### Post by Pulsewave on 2009-01-16
Hello World.
.
I tried to install Ubuntu 8.10 to a 1GB USB disk disk.
.
After the installation my main system a dual boot XP and Ubuntu 8.10 wont not boot unless i had the USB stick inserted. GRUB Error 21 if the USB was not inserted.
.
After googling i found some GRUB commands that allowed me to boot my Ubuntu partitions again but nada for the XP partition. Tried booting with Windows rescue disk and FIXMBR but that did not help either.
.
My fdisk -l :
.
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd993237a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38912   281844360    5  Extended
/dev/sda5            3825       19122   122881153+   7  HPFS/NTFS
/dev/sda6           19123       25496    51199123+  83  Linux
/dev/sda7           25497       26164     5365678+  82  Linux swap / Solaris
/dev/sda8           26165       38912   102398278+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8e3c8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
.
My menu.lst :
.
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Micro$oft Window$ XP Profe$$ional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
.
Anyone have any ideas how to get my XP partition to boot again.
.
Thanks In Advance.

---

### Post by DeMus on 2009-01-16
> **Pulsewave said:**
> Hello World.
.
I tried to install Ubuntu 8.10 to a 1GB USB disk disk.
.
After the installation my main system a dual boot XP and Ubuntu 8.10 wont not boot unless i had the USB stick inserted. GRUB Error 21 if the USB was not inserted.
.
After googling i found some GRUB commands that allowed me to boot my Ubuntu partitions again but nada for the XP partition. Tried booting with Windows rescue disk and FIXMBR but that did not help either.
.
My fdisk -l :
.
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd993237a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38912   281844360    5  Extended
/dev/sda5            3825       19122   122881153+   7  HPFS/NTFS
/dev/sda6           19123       25496    51199123+  83  Linux
/dev/sda7           25497       26164     5365678+  82  Linux swap / Solaris
/dev/sda8           26165       38912   102398278+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8e3c8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
.
My menu.lst :
.
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Micro$oft Window$ XP Profe$$ional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
.
Anyone have any ideas how to get my XP partition to boot again.
.
Thanks In Advance.


It looks to me that you installed grub on your USB disk. When this disk is not present, nothing will boot.
To boot XP again you can start the PC with the XP cd in the drive, boot from the cd.
Choose recover and choose into which Windows you want to boot, probably the one on C:\
You'll stay in a kind of DOS window, type the command fixmbr and reboot, this time from your harddisk.
Mind you, this is only to boot XP. To also boot Ubuntu you have to restore grub. How this is done is something I also would like to know.
One way is to re-install Ubuntu and this time place grub on the MBR of your first hard disk. But this is not a nice way.

DeMus

---

### Post by caljohnsmith on 2009-01-16
What exactly happens when you boot Windows from Grub? Do you get any errors? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by Pulsewave on 2009-01-16
Hello John.
.
Here are the results from  sudo bash boot_info_script_011.sh :
.
```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda1 
                       and looks at sector 395881585 of the same hard drive 
                       for the stage2 file and on partition #6 for 
                       /boot/grub/menu.lst .
    Mounting failed:
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of /dev/sda5 and 
                       looks at sector 1237591 on boot drive #3 for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: you must specify the filesystem type

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda6 
                       and looks at sector 395979913 of the same hard drive 
                       for the stage2 file and on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

sda8: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd993237a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sda2        61432560   625121279   281844360    5  Extended
/dev/sda5        61432623   307194929   122881153+   7  HPFS/NTFS
/dev/sda6       307194993   409593239    51199123+  83  Linux
/dev/sda7       409593303   420324659     5365678+  82  Linux swap / Solaris
/dev/sda8       420324723   625121279   102398278+  83  Linux

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8e3c8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641   83  Linux

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda6: UUID="fade327a-fa80-4cff-8760-dbd1940f535c" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="9d91f728-0de0-4d6b-bf8c-fdd495aaf435" 
/dev/sda8: UUID="88080a35-6c60-432a-b009-de0b61ca5960" TYPE="ext3" 
/dev/sdb1: UUID="da4ddfb0-77da-4059-a45b-d4805ae444b3" TYPE="ext3" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /data type ext3 (rw,relatime)
/dev/sda8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamesb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamesb)

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
# kopt=root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fade327a-fa80-4cff-8760-dbd1940f535c

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
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=fade327a-fa80-4cff-8760-dbd1940f535c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		fade327a-fa80-4cff-8760-dbd1940f535c
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Micro$oft Window$ XP Profe$$ional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=fade327a-fa80-4cff-8760-dbd1940f535c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=da4ddfb0-77da-4059-a45b-d4805ae444b3 /data           ext3    relatime        0       2
# /dev/sda8
UUID=88080a35-6c60-432a-b009-de0b61ca5960 /home           ext3    relatime        0       2
# /dev/sda7
UUID=9d91f728-0de0-4d6b-bf8c-fdd495aaf435 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 12828
drwxr-xr-x  3 root root    4096 2008-12-23 23:31 .
drwxr-xr-x 22 root root    4096 2008-12-23 23:31 ..
-rw-r--r--  1 root root  503560 2008-11-21 10:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-21 10:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-15 22:58 grub
-rw-r--r--  1 root root 8664969 2008-12-23 15:44 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 06:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-21 10:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-21 10:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339712 2008-11-21 10:30 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-15 22:58 .
drwxr-xr-x 3 root root   4096 2008-12-23 23:31 ..
-rw-r--r-- 1 root root    197 2009-01-15 22:57 default
-rw-r--r-- 1 root root     30 2008-12-23 15:11 device.map
-rw-r--r-- 1 root root   8108 2009-01-15 22:57 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-15 22:57 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-15 22:57 installed-version
-rw-r--r-- 1 root root   8712 2009-01-15 22:57 jfs_stage1_5
-rw-r--r-- 1 root root   4663 2009-01-15 22:58 menu.lst
-rw-r--r-- 1 root root   4663 2009-01-15 22:43 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-15 22:57 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-15 22:57 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-15 22:57 stage1
-rw-r--r-- 1 root root 121460 2009-01-15 22:57 stage2
-rw-r--r-- 1 root root   9556 2009-01-15 22:57 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
/dev/sda5: unknown volume type
```

The exact error i get is once the GRUB menu list is displayed. I select the Ubuntu partition and Ubuntu will start. If i select the XP partition, it flashes a brief message "error in stage 2" and displays the GRUB menu again.
.
Thanks In Advance.

---

### Post by bfrie on 2009-01-16
I have the same problem.

I installed ubuntu 8.10 on its own partition. The other partition has winxp.

I failed to have grub installed properly. When I turn on my computer all I get is grub>. So I cannot boot winxp or ubuntu.

What have I failed to do properly? I thought the liveCD from which I loaded ubuntu would do all the correct loading.

Thanks for your assistance.

[email]bfrie@mts.net[/email]

............

My script.txt is as follows:

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdb1 
                       and looks at sector 36734719 of the same hard drive 
                       for the stage2 file and on partition #1 for 
                       /boot/grub/menu.lst .
    Operating System:  
    Boot files/dirs:   /Boot /boot /BOOT /boot/grub

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  LILO
    Boot sector info:  LILO is installed in boot sector of /dev/sdb2 and 
                       looks at sector 61498119 of /dev/sdb for the "map" 
                       file, but the "map" file was not found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sdb3: _________________________________________________________________________

    File system:       swap

sdb4: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf68df68d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4427069a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    61432559    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2   *    61432560    62492849      530145   83  Linux
/dev/sdb3        62492850    82975724    10241437+  82  Linux swap / Solaris
/dev/sdb4        82975725   234436544    75730410   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7238A99938A95CBB" TYPE="ntfs" 
/dev/sdb1: LABEL="^B" UUID="3086-FF80" TYPE="vfat" 
/dev/sdb2: UUID="7b549b1f-5518-4272-9400-4b090a58c4c7" TYPE="ext2" 
/dev/sdb3: UUID="370aa2ab-c3c1-434c-9a1b-1f599a3155d4" TYPE="swap" 
/dev/sdb4: UUID="3be004c3-c0ca-453e-9a06-7c39beb7c9dc" TYPE="reiserfs" 
/dev/loop0: TYPE="squashfs" 

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
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


================================== sdb1/Boot: ==================================

total 48
drwx------  3 ubuntu root 16384 2009-01-13 21:34 .
drwx------ 29 ubuntu root 16384 1970-01-01 00:00 ..
drwx------  2 ubuntu root 16384 2009-01-13 21:34 grub

================================== sdb1/boot: ==================================

total 48
drwx------  3 ubuntu root 16384 2009-01-13 21:34 .
drwx------ 29 ubuntu root 16384 1970-01-01 00:00 ..
drwx------  2 ubuntu root 16384 2009-01-13 21:34 grub

================================== sdb1/BOOT: ==================================

total 48
drwx------  3 ubuntu root 16384 2009-01-13 21:34 .
drwx------ 29 ubuntu root 16384 1970-01-01 00:00 ..
drwx------  2 ubuntu root 16384 2009-01-13 21:34 grub

=============================== sdb1/boot/grub: ===============================

total 320
drwx------ 2 ubuntu root  16384 2009-01-13 21:34 .
drwx------ 3 ubuntu root  16384 2009-01-13 21:34 ..
-rwx------ 1 ubuntu root    197 2009-01-13 21:34 default
-rwx------ 1 ubuntu root     45 2009-01-13 21:34 device.map
-rwx------ 1 ubuntu root   8108 2009-01-13 21:34 e2fs_stage1_5
-rwx------ 1 ubuntu root   7856 2009-01-13 21:34 fat_stage1_5
-rwx------ 1 ubuntu root     16 2009-01-13 21:34 installed-version
-rwx------ 1 ubuntu root   8712 2009-01-13 21:34 jfs_stage1_5
-rwx------ 1 ubuntu root   7352 2009-01-13 21:34 minix_stage1_5
-rwx------ 1 ubuntu root   9756 2009-01-13 21:34 reiserfs_stage1_5
-rwx------ 1 ubuntu root    512 2009-01-13 21:34 stage1
-rwx------ 1 ubuntu root 121460 2009-01-13 21:34 stage2
-rwx------ 1 ubuntu root   9556 2009-01-13 21:34 xfs_stage1_5

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=7b549b1f-5518-4272-9400-4b090a58c4c7 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb4
UUID=8efa89a1-7143-46c8-b5f3-0a27fd73d8c4 /home           reiserfs relatime        0       2
# /dev/sdb1
UUID=1168-13E3  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=370aa2ab-c3c1-434c-9a1b-1f599a3155d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb2/boot: ==================================

total 2035
drwxr-xr-x  2 root root    1024 2009-01-09 20:40 .
drwxr-xr-x 21 root root    1024 2009-01-09 20:40 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=3be004c3-c0ca-453e-9a06-7c39beb7c9dc /               reiserfs notail,relatime 0       1
# /dev/sdb3
UUID=370aa2ab-c3c1-434c-9a1b-1f599a3155d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb4/boot: ==================================

total 4320
drwxr-xr-x  2 root root     296 2009-01-15 22:18 .
drwxr-xr-x 21 root root     592 2009-01-15 22:11 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== StdErr Messages: ===============================

hexdump: stdin: Illegal seek

---

### Post by caljohnsmith on 2009-01-16
**Pulsewave**, I believe I see your problem; at some point you accidentally installed Grub to the boot sector of your Windows partition. In the future, you might want to be careful not to do "setup (hd0,0)" in the Grub command line, or you will install Grub to the boot sector of your Windows partition as you did. But anyway, to fix the problem, if you have a Windows Install CD, boot that, go to the "recovery console" and do:
```
fixboot

```
Hopefully that will be all it takes to get Windows booting again. Let me know how that goes.

---

### Post by caljohnsmith on 2009-01-16
**Bfrie**, it looks like you tried to set up a boot partition (sdb1) on your Ubuntu drive, but it is formatted as FAT32; you need to use a linux file system like ext3 for your boot partition. Also, it looks like you have the Ubuntu main install on both sdb2 and sdb4. Since it is a new install, I would suggest deleting all your partitions to start over, and then manually set up the partitions you need. You can do that with the partition editor under System > Admin > Partition Editor. Also, if you want to use a boot partition, it doesn't need to be bigger than ~200 MB. How about trying that, and then when you go through the Ubuntu installer again, click on the "advanced" button near the end of the installation process, and specify to have Grub installed to /dev/sdb (your Ubuntu drive). Let me know how that goes or if you run into problems.

---

### Post by Pulsewave on 2009-01-16
John you beauty.
.
I could kiss you :P
.
Problem solved.

---

