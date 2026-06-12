---
title: "grub ide sata ext4 boot priority, put ide at rest"
date: 2009-05-09
forum: General Help
---

### Post by Claus7 on 2009-05-09
Hello,

maybe the right title for this thread might be: put an old ide at rest, while being able to use it if need arises.

The story: two hdd, one ata ide ,the second a sata one installed via a pci card.

The ouput of sudo fdisk -l is:
> **Disk /dev/sda: 60.0 GB**, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xced7ced7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        5991    17406427+  83  Linux
/dev/sda3            5992        7202     9727357+   b  W95 FAT32
/dev/sda4            7203        7299      779152+  82  Linux swap / Solaris

**Disk /dev/sdb: 250.0 GB**, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009285f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+  83  Linux
/dev/sdb2              13        2444    19535040   83  Linux
/dev/sdb3            2445        2748     2441880   82  Linux swap / Solaris
/dev/sdb4            2749       30401   222122722+  83  Linux

The sdb one has jaunty as os with **ext4** in all its partitions. What I would like to do is somehow be able to remove the ide drive without grub complaining. 

The output of the command:
```
grub> find /boot/grub/stage1
```
is: 
(hd0,1)

The error I get when I try to unplug the ide is:
GRUB Hard Disk Error

Is there a way that I can boot from my jaunty hdd without having connected the ide drive? Yet, I would like to be able to use ide drive without having to change anything.

Thank you,
Regards!

---

### Post by caljohnsmith on 2009-05-09
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about booting your Jaunty Live CD, download the **Boot Info Script** to the desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Claus7 on 2009-05-09
Hello,

the result of your detailed answer is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 88892144 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xced7ced7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560    96,245,414    34,812,855  83 Linux
/dev/sda3          96,245,415   115,700,129    19,454,715   b W95 FAT32
/dev/sda4         115,700,130   117,258,434     1,558,305  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009285f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       192,779       192,717  83 Linux
/dev/sdb2             192,780    39,262,859    39,070,080  83 Linux
/dev/sdb3          39,262,860    44,146,619     4,883,760  82 Linux swap / Solaris
/dev/sdb4          44,146,620   488,392,064   444,245,445  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1C7CCF167CCEE99A" TYPE="ntfs" 
/dev/sda2: UUID="79ca4ca3-da35-4d9c-b44d-68767485469f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="4e5407e7-dc3a-49f8-b260-48919a726189" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="85383296-9875-4ffa-b7e7-6e404b0355e9" 
/dev/sdb1: UUID="ed0d689d-aade-4e32-95d4-e30e4324aa9d" TYPE="ext4" 
/dev/sdb2: UUID="9fcfc5ba-461e-4f8d-a302-679ede23196d" TYPE="ext4" 
/dev/sdb3: TYPE="swap" UUID="aaffe8e6-5164-4487-887d-f95e441f5451" 
/dev/sdb4: UUID="ed92ac69-c468-48d3-a50d-acb3f00b0345" TYPE="ext4" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sda2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-386

title		Ubuntu 8.04.2, kernel 2.6.24-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro single
initrd		/boot/initrd.img-2.6.24-23-386

title		Ubuntu 8.04.2, kernel 2.6.15-53-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-53-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro quiet splash
initrd		/boot/initrd.img-2.6.15-53-386

title		Ubuntu 8.04.2, kernel 2.6.15-53-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-53-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro single
initrd		/boot/initrd.img-2.6.15-53-386

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2 -- converted during upgrade to edgy
UUID=79ca4ca3-da35-4d9c-b44d-68767485469f / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb1 -- converted during upgrade to edgy
UUID=1C7CCF167CCEE99A /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb3 -- converted during upgrade to edgy
UUID=4e5407e7-dc3a-49f8-b260-48919a726189 /media/alternate ext3 defaults 0 0
# /dev/hdb4 -- converted during upgrade to edgy
UUID=85383296-9875-4ffa-b7e7-6e404b0355e9 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sdb1         /media/sdb1  auto  rw,user,noauto     0       0

#device           mount point  fstype options  
/dev/sdc1        /media/usb0    auto rw,exec,noauto,users     0   0

/dev/sdc2        /media/usb1    auto rw,exec,auto,users     0   0



=================== sda2: Location of files loaded by Grub: ===================


  38.0GB: boot/grub/menu.lst
  45.5GB: boot/grub/stage2
  37.4GB: boot/initrd.img-2.6.15-53-386
  43.7GB: boot/initrd.img-2.6.24-23-386
  38.0GB: boot/initrd.img-2.6.24-23-386.bak
  42.1GB: boot/vmlinuz-2.6.15-53-386
  42.0GB: boot/vmlinuz-2.6.24-23-386
  43.7GB: initrd.img
  37.4GB: initrd.img.old
  42.0GB: vmlinuz
  42.1GB: vmlinuz.old

============================= sdb1/grub/menu.lst: =============================

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
# kopt=root=UUID=9fcfc5ba-461e-4f8d-a302-679ede23196d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed0d689d-aade-4e32-95d4-e30e4324aa9d

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ed0d689d-aade-4e32-95d4-e30e4324aa9d
kernel		/vmlinuz-2.6.28-11-generic root=UUID=9fcfc5ba-461e-4f8d-a302-679ede23196d ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ed0d689d-aade-4e32-95d4-e30e4324aa9d
kernel		/vmlinuz-2.6.28-11-generic root=UUID=9fcfc5ba-461e-4f8d-a302-679ede23196d ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ed0d689d-aade-4e32-95d4-e30e4324aa9d
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-386 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-386 (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro single 
initrd		/boot/initrd.img-2.6.24-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.15-53-386 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-53-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro quiet splash 
initrd		/boot/initrd.img-2.6.15-53-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.15-53-386 (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-53-386 root=UUID=79ca4ca3-da35-4d9c-b44d-68767485469f ro single 
initrd		/boot/initrd.img-2.6.15-53-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-11-generic

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=9fcfc5ba-461e-4f8d-a302-679ede23196d /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=ed0d689d-aade-4e32-95d4-e30e4324aa9d /boot           ext4    relatime        0       2
# /home was on /dev/sdb4 during installation
UUID=ed92ac69-c468-48d3-a50d-acb3f00b0345 /home           ext4    relatime        0       2
# swap was on /dev/sda4 during installation
UUID=85383296-9875-4ffa-b7e7-6e404b0355e9 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=aaffe8e6-5164-4487-887d-f95e441f5451 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  0b 17 2f ff 0c 18 30 ff  0d 19 31 ff 0d 19 31 ff  |../...0...1...1.|
00000010  0e 1a 32 ff 0f 1b 33 ff  0f 1c 32 ff 0b 1a 2d ff  |..2...3...2...-.|
00000020  0b 1b 2c ff 0d 19 2b ff  18 22 34 ff 16 1e 2f ff  |..,...+.."4.../.|
00000030  1d 21 33 ff 21 24 33 ff  00 00 0b ff 00 03 0f ff  |.!3.!$3.........|
00000040  3a 48 54 ff 3a 4a 56 ff  40 53 5b ff 42 55 5d ff  |:HT.:JV.@S[.BU].|
00000050  47 5c 64 ff 42 5a 60 ff  4c 66 6c ff 4d 67 6d ff  |G\d.BZ`.Lfl.Mgm.|
00000060  52 6c 72 ff 59 72 76 ff  5e 77 7b ff 67 7c 7e ff  |Rlr.Yrv.^w{.g|~.|
00000070  6b 80 82 ff 70 83 86 ff  72 86 8b ff 74 8a 90 ff  |k...p...r...t...|
00000080  74 8b 93 ff 75 8f 95 ff  78 92 98 ff 78 95 99 ff  |t...u...x...x...|
00000090  79 96 9a ff 7b 97 98 ff  7d 96 98 ff 7d 95 95 ff  |y...{...}...}...|
000000a0  7e 93 94 ff 79 8b 8a ff  71 7f 7e ff 85 8d 8c ff  |~...y...q.~.....|
000000b0  be c4 c3 ff f2 f4 f4 ff  fd ff ff ff fb fb fb ff  |................|
000000c0  fc fc fc ff fc fc fc ff  fc fc fc ff fc fd fb ff  |................|
000000d0  fb fc fa ff fa fb f7 ff  f9 fa f6 ff f6 f7 f3 ff  |................|
000000e0  f4 f5 f1 ff f9 fb f5 ff  f3 f5 ef ff cd cf c9 ff  |................|
000000f0  a7 a9 a3 ff b6 b8 b2 ff  dc e2 dd ff ed fb fa ff  |................|
00000100  e0 f1 f4 ff ce e1 e6 ff  bc cf d7 ff ad c0 cd ff  |................|
00000110  9b b2 c2 ff 82 99 af ff  6d 85 9d ff 54 6c 88 ff  |........m...Tl..|
00000120  45 5d 7b ff 37 4e 6e ff  37 4d 70 ff 3c 52 75 ff  |E]{.7Nn.7Mp.<Ru.|
00000130  3d 53 76 ff 3d 50 75 ff  3b 4e 73 ff 3d 53 77 ff  |=Sv.=Pu.;Ns.=Sw.|
00000140  3d 53 77 ff 42 58 7b ff  60 76 99 ff 5e 75 95 ff  |=Sw.BX{.`v..^u..|
00000150  3b 53 71 ff 32 47 66 ff  2d 43 5f ff 38 4d 68 ff  |;Sq.2Gf.-C_.8Mh.|
00000160  42 58 71 ff 52 69 7f ff  5f 76 8c ff 68 7d 92 ff  |BXq.Ri.._v..h}..|
00000170  6a 7f 94 ff 6c 82 94 ff  6f 84 9a ff 61 73 92 ff  |j...l...o...as..|
00000180  5e 6f 90 ff 5d 6d 8a ff  59 6b 82 ff 54 68 79 ff  |^o..]m..Yk..Thy.|
00000190  5e 72 7d ff 7f 95 9a ff  a4 b9 ba ff bd d2 d0 ff  |^r}.............|
000001a0  c3 d6 d3 ff c6 d6 d5 ff  c0 cd cf ff b0 b8 bf ff  |................|
000001b0  94 9b a4 ff 7b 7f 8a ff  68 6e 7b ff 4d 57 68 ff  |....{...hn{.MWh.|
000001c0  48 55 65 ff 3d 4a 5a ff  48 55 65 ff 3b 48 58 ff  |HUe.=JZ.HUe.;HX.|
000001d0  5b 68 78 ff ae ba cc ff  a9 b5 c7 ff 96 a2 b4 ff  |[hx.............|
000001e0  77 83 95 ff 7d 89 9b ff  81 8d 9f ff 5f 6b 7d ff  |w...}......._k}.|
000001f0  52 5e 70 ff 4c 58 6a ff  2d 38 4c ff 0d 1a 30 ff  |R^p.LXj.-8L...0.|
00000200
```

Regards!

---

### Post by caljohnsmith on 2009-05-09
OK, how about doing the following commands:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And please post the output before typing "quit". Then remove your IDE drive and try booting your Jaunty drive again; let me know what happens this time, and we can work from there.

John

---

### Post by Claus7 on 2009-05-09
Hello,

the output is as follows:

```
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.
```

In the first command, as you can see, I do not get anything as output.

edit: reboot without ide will follow
It worked! I do not believe that is was so easy. It rebooted and while doing so, it said that it did from (hd(0,0)). Before it was from (hd(1,0)). Now my life is tremendously more quiet and I think better for the life of my old hdd.

Thank you for your responses,
Regards!

---

### Post by caljohnsmith on 2009-05-09
Glad to hear those Grub commands are all it took to get your SATA drive booting properly; cheers and have fun with your new Ubuntu install. :)

John

---

