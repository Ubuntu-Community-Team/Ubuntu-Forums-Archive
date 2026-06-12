---
title: "Boot Management , Usb Capabilities for grub ? ubuntu ?"
date: 2009-02-15
forum: General Help
---

### Post by paducahguy on 2009-02-15
I have bought recently a usb microdrive that is oh.. say 16 gigabytes ... though I can't seem to find ANY boot managers to install to it through windows or linux...  I was hoping it was a possibility that someone would know where i might find such a program or have a url for me to find such information on how to set this up on my thumb drive ? 

I was also curious if it was possible for ubuntu to auto detect through grub boot capable partitions like windows or other linux installs because I seem to remember windows will auto install the windows partition as long as it is pre-existing though if you install windows later it won't do it ... so i am pondering how I can get this done ? 

Thanks in advance to anyone who helps me out with these issues....

---

### Post by caljohnsmith on 2009-02-15
So what is your ultimate goal? You want to install a boot manager to your USB drive, but are you going to install any OSes to the USB drive? Or do you want your USB drive to just boot your OSes on your HDD? Also, it would be good to check, but does your BIOS support booting USB devices?

---

### Post by paducahguy on 2009-02-15
i just want to be able to boot the drives that have an os on them... i am basically wanting to create a "boot strap aka boot loader" that detects the drives and partitions on a system and or probes for the boot capable operating systems installed....

---

### Post by caljohnsmith on 2009-02-15
I don't know of any boot manager that on start up will go through all your drives/partitions and automatically detect your OSes. What you could do is install Grub to your USB drive, and then set up a generic menu.lst that includes booting several partitions on different drives. Or if you learn to use the Grub CLI a little, you could use that on start up to help figure out what drives and partitions are present in order to help figure out what to boot. For instance, in the Grub CLI you could do:
```
grub> geometry (hd0)
```
And that gives you the size of the 1st boot drive (hd0) and a list of all its partitions.

---

### Post by paducahguy on 2009-02-15
well that's what i was thinking but i can't figure out how to edit my menu.lst to include my windows partition to boot .. here's what i DO have so far to at least make it show the partition...

-------

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
color cyan/blue white/blue

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
# kopt=root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d0c0fe44-a161-4a93-ab25-c127e53aebc4

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
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/memtest86+.bin
quiet

title		Windows
root		(hd0,2) makeactive chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST


---------------

The windows drive is on /dev/sda2 yet i can't figure out what else to put there as it's been quite a while since i've had to edit these files.

---

### Post by caljohnsmith on 2009-02-15
I think it would help to first get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by paducahguy on 2009-02-15
this is the boot summary my friend...  i hope this helps 

---------------------


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BUFFALO INC. LinkStation series 
                       LS-GL(IESADA)
    Boot files/dirs:   /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   436,534,244   436,534,182  83 Linux
/dev/sda2         436,534,245   499,476,914    62,942,670   7 HPFS/NTFS
/dev/sda3         499,476,915 1,948,218,614 1,448,741,700  83 Linux
/dev/sda4       1,948,218,615 1,953,520,064     5,301,450   f W95 Ext d (LBA)
/dev/sda5       1,948,218,678 1,953,520,064     5,301,387  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001a9aa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       401,624       401,562  83 Linux
/dev/sdb2    *        401,625     1,397,654       996,030  83 Linux
/dev/sdb4           1,397,655   976,768,064   975,370,410   5 Extended
/dev/sdb5           1,397,718     1,670,759       273,042  82 Linux swap / Solaris
/dev/sdb6           1,670,823   976,768,064   975,097,242  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0a5d96e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dafd52c7-c8fc-4fd2-819c-7e2503996171" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="2090CD3990CD1666" LABEL="tilt" TYPE="ntfs" 
/dev/sda3: UUID="d0c0fe44-a161-4a93-ab25-c127e53aebc4" TYPE="ext3" 
/dev/sda5: UUID="44ba80ee-4025-4c92-96ef-666489d7adcd" TYPE="swap" 
/dev/sdb1: UUID="e6a43445-bf34-4545-8cf9-debc36493c0c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="538a55cd-fcbd-46e6-935d-2dca68843a0d" TYPE="xfs" 
/dev/sdb5: UUID="af666e68-546a-400d-900e-b92d3c6d9eba" TYPE="swap" 
/dev/sdb6: UUID="205dda69-29b8-4311-94e1-049c823bb922" TYPE="xfs" 
/dev/sdc1: UUID="F697-F464" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ximal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ximal)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ximal)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\Windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\Windows="Windows Fundamentals for Legacy PCs" /fastdetect

=========================== sda3/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

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
# kopt=root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d0c0fe44-a161-4a93-ab25-c127e53aebc4

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
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d0c0fe44-a161-4a93-ab25-c127e53aebc4
kernel		/boot/memtest86+.bin
quiet

title		Windows
root		(hd0,2) makeactive chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d0c0fe44-a161-4a93-ab25-c127e53aebc4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=44ba80ee-4025-4c92-96ef-666489d7adcd none            swap    sw              0       0
# /dev/sdb5
UUID=af666e68-546a-400d-900e-b92d3c6d9eba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 493.0GB: boot/grub/menu.lst
 492.8GB: boot/grub/stage2
 492.7GB: boot/initrd.img-2.6.27-11-generic
 492.8GB: boot/initrd.img-2.6.27-7-generic
 492.7GB: boot/initrd.img-2.6.27-9-generic
 492.8GB: boot/vmlinuz-2.6.27-11-generic
 492.8GB: boot/vmlinuz-2.6.27-7-generic
 492.8GB: boot/vmlinuz-2.6.27-9-generic
 492.7GB: initrd.img
 492.7GB: initrd.img.old
 492.8GB: vmlinuz
 492.8GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: initrd.buffalo

=============================== sdb2/etc/fstab: ===============================

/dev/root	/		ext3	defaults	1 1
proc		/proc		proc	defaults	0 0
devpts         /dev/pts    devpts     gid=4,mode=620 0    0

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 5e 90 20 20 20 20 20  20 20 20 00 02 40 20 00  |.^.        ..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 2c 00 00 00  |........?...,...|
00000020  a4 3f ef 00 7a 07 00 00  00 00 00 00 02 00 00 00  |.?..z...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 64 f4 97 f6 4e  4f 20 4e 41 4d 45 20 20  |..)d...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 10 00 01 00 00 7e  |  FAT32   .....~|
00000060  fc bd 00 7c 66 bb 00 00  00 00 8e d3 8b e5 fb 8e  |...|f...........|
00000070  db 8e c3 52 32 e4 cd 13  84 d2 79 2a b4 41 bb aa  |...R2.....y*.A..|
00000080  55 cd 13 72 0f 81 fb 55  aa 75 09 d1 e9 73 05 c6  |U..r...U.u...s..|
00000090  06 80 7d 74 b4 08 cd 13  72 0c 83 e1 3f 89 4e 18  |..}t....r...?.N.|
000000a0  8a ce 41 89 4e 1a 66 ff  76 2c 66 58 66 50 66 48  |..A.N.f.v,fXfPfH|
000000b0  66 48 66 3d ed ff ff 0f  77 44 66 0f b6 4e 0d 51  |fHf=....wDf..N.Q|
000000c0  66 f7 e1 66 91 8a 46 10  66 f7 66 24 66 03 c1 59  |f..f..F.f.f$f..Y|
000000d0  66 50 51 e8 6a 00 be dd  7d 8b fb b9 0b 00 f3 a6  |fPQ.j...}.......|
000000e0  75 1f f6 05 18 75 1a c7  06 d6 7c eb 1d ff 77 14  |u....u....|...w.|
000000f0  ff 77 1a eb b5 81 7f 68  68 06 0f 84 6a 01 e9 e7  |.w.....hh...j...|
00000100  00 83 c3 20 79 d0 59 66  58 66 40 e2 c3 66 58 06  |... [email]y.YfXf@..fX[/email].|
00000110  68 e0 1f 07 50 66 c1 e8  07 66 3d ff ff ff ff 74  |h...Pf...f=....t|
00000120  07 66 a3 1b 7d e8 18 00  5b 83 e3 7f c1 e3 02 66  |.f..}...[......f|
00000130  26 8b 87 00 7e 66 25 ff  ff ff 0f 07 66 50 eb b3  |&...~f%.....fP..|
00000140  66 03 46 1c 66 0f b7 4e  0e 66 03 c1 66 89 46 62  |f.F.f..N.f..f.Fb|
00000150  bf 05 00 8b 46 64 33 d2  f7 76 18 91 8b 46 62 f7  |....Fd3..v...Fb.|
00000160  76 18 42 87 ca 3b 56 1a  73 18 f7 76 1a 8a f2 86  |v.B..;V.s..v....|
00000170  c5 c1 e8 02 c0 cc 02 0a  c8 0a f4 84 e4 b8 01 02  |................|
00000180  eb 08 8c 46 60 b4 42 be  5a 7c bb 00 7e 8a 56 fe  |...F`.B.Z|..~.V.|
00000190  cd 13 73 09 4f 74 51 32  e4 cd 13 eb b6 c3 00 00  |..s.OtQ2........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 0d 4e 6f 6e 2d 73 79  |..........Non-sy|
000001c0  73 74 65 6d 20 64 69 73  6b 2c 20 70 72 65 73 73  |stem disk, press|
000001d0  20 61 6e 79 20 6b 65 79  2e 2e 2e 07 00 42 4f 4f  | any key.....BOO|
000001e0  54 57 49 5a 20 53 59 53  be b9 7d ac b4 0e b3 07  |TWIZ SYS..}.....|
000001f0  cd 10 ac 84 c0 75 f5 98  cd 16 cd 19 00 00 55 aa  |.....u........U.|
00000200

---

### Post by paducahguy on 2009-02-15
well i need some sleep.. please pm me cal as i really need some help with this one thing and it requires windows unfortunately... nyhow long story short is installing windows "AFTER" linux  :( 

Thus to boot my linux ill goign through a little over a i'd sa at least 5... ok i fell asleep at the kb again.. time to lay down on the couch.. hcugh i would appreciate a pm John as it makes it easier than having to searh the por forums.... Thanks much to all who read n help :)

---

### Post by caljohnsmith on 2009-02-15
So can you boot into Ubuntu OK now? If so, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP
root (hd0,1)
chainloader +1

```
Reboot, and let me know what happens when you boot XP from your Grub menu.

---

### Post by paducahguy on 2009-02-15
That cured the windows boot problem my friend...

That part is solved... 

Soo... is there any way you might have time to tell me how to make the file that i need to put on my usb stick as a way to haave my computer boot off of it if i put it in the drive ? 

kind of like when you put a cd in the drive of a computer and it gives you 8 seconds or so until it boots up normally allowing you to press a button to get the cd or media you intend to use to boot the system ?

---

### Post by Slim Odds on 2009-02-15
> **paducahguy said:**
> I have bought recently a usb microdrive that is oh.. say 16 gigabytes ...

Dude, if you're not even sure how big your device is how do you expect to do anything? :lolflag:

---

### Post by caljohnsmith on 2009-02-15
OK, how about trying this:
[LIST]
[*]Create a small 5-10 MB ext2 partition on your USB drive
[*]Assuming the partition you created is "sdbX", first mark the partition as bootable, mount the partition, and install Grub:
```
sudo sfdisk -A1 /dev/[COLOR="Blue"]sdb[/COLOR]
sudo mount /dev/[COLOR="Blue"]sdbX[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/[COLOR="Blue"]sdb[/COLOR]
```
So change "sdb" and the partition "sdbX" for your USB drive.
[*]Download the attached "menu.lst.txt" file to your desktop and do:
```
sudo mv ~/Desktop/menu.lst.txt /mnt/boot/grub/menu.lst
```
[/LIST]
Reboot, set your BIOS to boot your USB drive, and let me know how far you get. We can work from there.

---

