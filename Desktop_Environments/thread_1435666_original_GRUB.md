---
title: "original GRUB"
date: 2010-03-21
forum: Desktop Environments
---

### Post by farak on 2010-03-21
I am running an ACER ASPIRE 7720Z with a dual boot XP and UBUNTU Intrepid on a single HD. On the same HD I have about 30 gigs of additional storage with an ext3 format. I recently had trouble with accessing the additional storage through linux (but not XP) so I reformatted it through Partition Magic. Since then I have not been able to boot to either OS as I get a GRUB *error 15*. I have searched the forum and the usual way of booting to the Live CD and entering the grub editor does not work. After I enter the editor and do a *find /boot/grub/stage1* - result being (hd0,6) - I enter *root (hd0,6)* and then *setup (hd0)*. From that I get :-

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

Now.....all of the posts I have searched over the last 8 hours have dealt with Ubuntu 9.10 and/or Windows 7 and GRUB2 with a limited number of hits (250) from each search. Has forum support for older releases of Ubuntu been discontinued or is there a problem with the search engine of this forum?

Answers to both of my problems would be immensely appreciated.

Farak

---

### Post by oldfred on 2010-03-21
Just so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Standard way to recover boot:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by farak on 2010-03-22
ok, here are the results from the *boot-info_script*

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda6 and looks 
                       at sector 219747992 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19b9be03

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   185,598,944   185,598,882   7 HPFS/NTFS
/dev/sda2         185,598,945   488,392,064   302,793,120   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         185,599,008   248,798,654    63,199,647  83 Linux
/dev/sda6         248,798,718   468,873,089   220,074,372  83 Linux
/dev/sda7         468,873,153   488,392,064    19,518,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        200402DC0402B4B6                       ntfs                                     
/dev/sda5        6368746f-2074-616b-6f65-207575696400   ext3                                     
/dev/sda6        e79cc70d-2ab6-4d1f-bce9-b79301797cf3   ext3                                     
/dev/sda7        7feda61a-b39e-4e53-ac92-a6226b4668cb   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro

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

title		Ubuntu 8.10, kernel 2.6.27-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 8.10, kernel 2.6.27-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda10
UUID=e79cc70d-2ab6-4d1f-bce9-b79301797cf3  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda11
UUID=03752463-0da0-428d-9c49-c8450f101159  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  

/dev/sda5                                  /media/sda5    ext3         defaults                    0  0  

=================== sda6: Location of files loaded by Grub: ===================


 172.7GB: boot/grub/menu.lst
 180.7GB: boot/grub/stage2
 172.7GB: boot/initrd.img-2.6.27-11-generic
 172.7GB: boot/initrd.img-2.6.27-14-generic
 172.6GB: boot/initrd.img-2.6.27-15-generic
 151.5GB: boot/initrd.img-2.6.27-16-generic
 180.1GB: boot/initrd.img-2.6.27-17-generic
 172.7GB: boot/initrd.img-2.6.27-7-generic
 172.6GB: boot/initrd.img-2.6.27-9-generic
 172.6GB: boot/vmlinuz-2.6.27-11-generic
 172.6GB: boot/vmlinuz-2.6.27-14-generic
 172.6GB: boot/vmlinuz-2.6.27-15-generic
 172.6GB: boot/vmlinuz-2.6.27-16-generic
 174.6GB: boot/vmlinuz-2.6.27-17-generic
 172.7GB: boot/vmlinuz-2.6.27-7-generic
 172.7GB: boot/vmlinuz-2.6.27-9-generic
 180.1GB: initrd.img
 151.5GB: initrd.img.old
 174.6GB: vmlinuz
 172.6GB: vmlinuz.old
```

the link you gave for the standard way to fix GRUB mainly talks about GRUB2 and Ubuntu 9.10. I've already tried the method for the original GRUB but that's where I get the ```
Error 12: Invalid device requested
```

---

### Post by oldfred on 2010-03-22
You have partition table problems.

 Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.
Extended  partition  linking to another extended partition

You cannot have linked extended partitions nor partition 256.

I am no expert on partition table repairs. Many recommend testdisk.
Testdisk is in the repository and can be downloaded if universe is enabled.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

