---
title: "Grub Error 17"
date: 2009-02-20
forum: General Help
---

### Post by Tom_T on 2009-02-20
Hi

Installed Ubuntu on to my main PC that also has 2 copies of XP installed. At first it was all multibooting fine with Grub.

Today I turn it on and now get error 17 on startup

So I booted up partedmagic and tried to reinstall grub using:

root (hd0,2)
setup (hd0)

But this fails.

I've run the boot_info_script and these are the results:
```
============================= Boot Info Summary: ==============================

 =>  => 
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:      Boot files/dirs:   
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:      Boot files/dirs:   
sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:      Boot files/dirs:   
sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:      Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85ee85ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,671,969   114,671,907  17 Hidden HPFS/NTFS
/dev/sda2         114,671,970   280,575,224   165,903,255   7 HPFS/NTFS
/dev/sda3         280,575,225   383,680,394   103,105,170  93 Amoeba/Accidently Hidden Linux
/dev/sda4         383,680,395   389,544,119     5,863,725   5 Extended
/dev/sda5         383,680,458   389,544,119     5,863,662  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6fce6fc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   145,211,534   145,211,472   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="04E86FFAE86FE87E" LABEL="XP Pro" TYPE="ntfs" 
/dev/sda2: UUID="34F001B9F001827A" LABEL="ALI" TYPE="ntfs" 
/dev/sda3: LABEL="ubuntu" UUID="020b5ae8-5241-4eb6-beb5-4bf8b698f5b2" TYPE="ext3" 
/dev/sda5: UUID="de114161-3ac3-4a57-927b-91e03c769f56" TYPE="swap" 
/dev/sdb1: UUID="449C52CA9C52B660" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=0,utf8,umask=077)
/dev/sda3 on /mnt type ext3 (rw)
/dev/sdd1 on /media/USB DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=0,utf8,umask=077)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=/boot/grub/splashimages/splash.xpm.gz

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
# kopt=root=UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2

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
uuid		020b5ae8-5241-4eb6-beb5-4bf8b698f5b2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
#uuid		020b5ae8-5241-4eb6-beb5-4bf8b698f5b2
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		020b5ae8-5241-4eb6-beb5-4bf8b698f5b2
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		020b5ae8-5241-4eb6-beb5-4bf8b698f5b2
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		020b5ae8-5241-4eb6-beb5-4bf8b698f5b2
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Pro - KIDS
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=020b5ae8-5241-4eb6-beb5-4bf8b698f5b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=de114161-3ac3-4a57-927b-91e03c769f56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 187.0GB: boot/grub/menu.lst
 187.0GB: boot/grub/stage2
 187.0GB: boot/initrd.img-2.6.27-11-generic
 187.0GB: boot/initrd.img-2.6.27-7-generic
 187.0GB: boot/vmlinuz-2.6.27-11-generic
 187.0GB: boot/vmlinuz-2.6.27-7-generic
 187.0GB: initrd.img
 187.0GB: initrd.img.old
 187.0GB: vmlinuz
 187.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hda 
=============================== StdErr Messages: ===============================

sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~
sed: unsupported command ~

```

The main 250GB drive is split:
XP
XP - KIDS
Ubuntu
SWAP
Unallocated

The 80GB Drive is just one partition.

I did change the menu.lst yeserday :rolleyes: in an attempt to hide other partitions from view.

I didn't want hd0 to see hd1, hd2 etc
or hd1 to see hd0, hd2 etc..  and so on.

So I added this to the Windows options in menu.lst !!

```
title		Windows XP Pro
root		(hd0,0)
unhide (hd0,0)
hide (hd0,1)
hide (hd0,2)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Pro - KIDS
root		(hd0,1)
hide (hd0,0)
unhide (hd0,1)
hide (hd0,2)
savedefault
makeactive
chainloader	+1
```

Is that why this has happened ??  How do I fix it ?

Any Ideas ?


Thanks

---

### Post by caljohnsmith on 2009-02-20
So more booting problems again, Tom_T? You seem to have a knack for attracting booting problems. :) About your Grub error 17, it looks like it is due to hiding the Ubuntu partition. Keep in mind that "hiding" a partition just means adding 0x10 to its file system ID in the partition table so it is then an unrecognized file system. That's why your sda3 Ubuntu install now has a file system ID of "93" instead of "83", where "83" is for any linux file system. But since Windows can't recognize nor read a linux partition, there is no need to "hide" the linux partition from Windows by changing its file system ID. If you don't want Windows to even recognize that the linux partition exists on the drive, you would have to delete the linux partition (obviously not what you want to do) or maybe pull some special trick in Windows to prevent Windows from seeing it as a partition (I don't know if that is possible though). 

So bottom line, if you want to hide your NTFS partitions from each other in the menu.lst, that's certainly OK, but I would not recommend hiding the Ubuntu partition or you won't be able to boot like you are currently experiencing. So to unhide the Ubuntu partition, if you boot your Live CD, how about doing:
```
sudo sfdisk -c /dev/sda 3 83
```
And then you should be able to boot Grub again assuming there's no other issues. Let me know how that goes or if you run into problems.

---

### Post by Tom_T on 2009-02-20
As always you save the day :)
That has worked fine.

Can you advise the best way to stop the partitions being visable between various OS's ??

Thanks :)

---

### Post by caljohnsmith on 2009-02-20
> **Tom_T said:**
> As always you save the day :)
That has worked fine.

Can you advise the best way to stop the partitions being visable between various OS's ??

Thanks :)
Glad that worked OK. About the partitions being visible between OSes, what exactly are you trying to accomplish, or what is the problem with them being visible to each other right now? As far as hiding the two Windows NTFS partitions from each other, you can do it like you are with using "hide" and "unhide" in your menu.lst. But as I tried to explain in my previous post, I don't know of any way you can truly hide the linux partition from your Windows partitions so that Windows doesn't think the linux partition exists. There might be some way like modifying the Windows registry, but I don't know off-hand how to do it.

---

### Post by Tom_T on 2009-02-20
Hi
By default if the kids log in they have another drive that is my XP. I don't want that.

I don't want them to be able to have access to my files etc.

XP doesn't show the ubuntu paritions in 'My Computer' show they are not easily accessable.

If I change the menu.lst to this should that work ??

```
title		Windows XP Pro
root		(hd0,0)
unhide (hd0,0)
hide (hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Pro - KIDS
root		(hd0,1)
hide (hd0,0)
unhide (hd0,1)
savedefault
makeactive
chainloader	+1
```

Thanks :)

---

### Post by caljohnsmith on 2009-02-20
Yes, I think those Windows entries you show should work just fine to hide your two Windows installations from each other. Let me know how that goes. :)

---

### Post by Tom_T on 2009-02-20
Sorted.  Boots into XP and the other XP & Ubuntu are not visable.

Many Thanks :D

---

### Post by caljohnsmith on 2009-02-20
That's great news it worked OK. Hope you don't run into any more booting problems now for a while at least. :)

---

