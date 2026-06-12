---
title: "GRUB messed up ! URGENT please help"
date: 2009-03-02
forum: General Help
---

### Post by markk1994 on 2009-03-02
Hey so I have 2 320 gbs hds so I installed ubuntu on one of them last night since this is my new pc. After installation GRUB took over and me being curious opened /boot/grub/menu.lst and screwed up my Windows boot partion thingy.Now when I try to boot i get this error "Unexpected Device String" This is my menu.lft file 

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
he rootnoreply statement. Here is the current Windoze section:
title		Ubuntu 8.10, memtest86+
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd1,4)
makeactive
chainloader	+1
```

---

### Post by caljohnsmith on 2009-03-02
In order to get a clearer picture of your setup related to booting Windows, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by markk1994 on 2009-03-02
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   623,193,479   623,193,417  83 Linux
/dev/sda2         623,193,480   625,137,344     1,943,865   5 Extended
/dev/sda5         623,193,543   625,137,344     1,943,802  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf9232a9

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         15,120   625,136,399   625,121,280   5 Extended
/dev/sdb5              15,183   625,136,399   625,121,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5855328f-2672-4e41-9e7b-752b01b38af9" TYPE="ext3" 
/dev/sda5: TYPE="swap" 
/dev/sdb5: UUID="708432BA843282A0" TYPE="ntfs" 

=============================== "mount" output: ===============================

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/martin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=martin)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=martin)


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
# kopt=root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5855328f-2672-4e41-9e7b-752b01b38af9

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
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
he rootnoreply statement. Here is the current Windoze section:
title		Ubuntu 8.10, memtest86+
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd1,4)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5855328f-2672-4e41-9e7b-752b01b38af9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0075cbd0-a41a-4c0d-ae1d-26d105d74cbd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 239.7GB: boot/grub/menu.lst
 239.7GB: boot/grub/stage2
 239.7GB: boot/initrd.img-2.6.27-11-generic
 239.7GB: boot/initrd.img-2.6.27-7-generic
 239.7GB: boot/vmlinuz-2.6.27-11-generic
 239.7GB: boot/vmlinuz-2.6.27-7-generic
 239.7GB: initrd.img
 239.7GB: initrd.img.old
 239.7GB: vmlinuz
 239.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by caljohnsmith on 2009-03-02
It looks like the problem is you installed Ubuntu on the drive that had your Vista boot files, because the Vista partition on your sdb drive is missing its boot files. And to make matters a little more complicated, you have Vista installed to sdb5, which is a logical partition, so you have to take special steps to boot Vista from a logical partition. I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") on how to restore Vista's boot files and also how to boot Vista from a logical partition. Good luck and let me know how it goes.

---

### Post by markk1994 on 2009-03-02
I dont think thats the case for some reason cause I installed it on a different partion for sure. I mounted the vista drive and all files are their so its just a matter of finding out what (hdx,y) it is.... Please help

---

### Post by markk1994 on 2009-03-02
sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr


The boot files are still there....

---

