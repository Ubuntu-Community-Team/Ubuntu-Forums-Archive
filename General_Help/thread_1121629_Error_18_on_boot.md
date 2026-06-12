---
title: "Error 18 on boot"
date: 2009-04-10
forum: General Help
---

### Post by ka9mnx on 2009-04-10
After installing the latest update I get an error 18 when trying to boot to 2.6.27-11. I can boot into 2.6.27-9 just fine. What's gone wrong?
Thanks,
Gary

---

### Post by fabricator4 on 2009-04-10
> **ka9mnx said:**
> After installing the latest update I get an error 18 when trying to boot to 2.6.27-11. I can boot into 2.6.27-9 just fine. What's gone wrong?
Thanks,
Gary

Try changing your BIOS settings for LBA.  It seems to be confused about how it's addressing the number of logical cylinders.  Typical settings for LBA might be auto or manual.

Chris

---

### Post by ka9mnx on 2009-04-10
Try changing your BIOS settings for LBA. It seems to be confused about how it's addressing the number of logical cylinders. Typical settings for LBA might be auto or manual.

Thanks for the reply Chris.
I went to the BIOS and LBA is not an option. Computer: IBM ThinkPad T40.

Gary

---

### Post by meierfra. on 2009-04-10
It looks like the new kernel is outside the reach of the bios. Just to confirm, I suggest to boot into  Ubuntu  and download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags).


The standard solution for Grub Error 18 (other than changing to LBA mode or flashing the bios) is  to create a separate boot partition:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by ka9mnx on 2009-04-11
Thanks meierfra for your reply.

Here are the results of the dump:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       45046864 sectors, but according to the info from 
                       fdisk, it has 45057537 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4724c95

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    45,057,599    45,057,537   7 HPFS/NTFS
/dev/sda2          45,062,325    78,140,159    33,077,835   5 Extended
/dev/sda5          45,062,388    48,162,869     3,100,482  82 Linux swap / Solaris
/dev/sda6          48,162,933    78,140,159    29,977,227  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AA54457B54454AF1" LABEL="IBM_PRELOAD" TYPE="ntfs" 
/dev/sda5: UUID="699adbe4-3908-4d9e-91e7-b333393ff817" TYPE="swap" 
/dev/sda6: UUID="9f3d3f43-bf9b-48f1-befb-4d6451d0765c" TYPE="ext3" 

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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sda1 on /media/IBM_PRELOAD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


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
# kopt=root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f3d3f43-bf9b-48f1-befb-4d6451d0765c

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
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9f3d3f43-bf9b-48f1-befb-4d6451d0765c
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
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9f3d3f43-bf9b-48f1-befb-4d6451d0765c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=699adbe4-3908-4d9e-91e7-b333393ff817 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  34.1GB: boot/grub/menu.lst
  32.9GB: boot/grub/stage2
  34.1GB: boot/initrd.img-2.6.27-11-generic
  32.8GB: boot/initrd.img-2.6.27-7-generic
  32.9GB: boot/initrd.img-2.6.27-9-generic
  38.6GB: boot/vmlinuz-2.6.27-11-generic
  32.8GB: boot/vmlinuz-2.6.27-7-generic
  32.8GB: boot/vmlinuz-2.6.27-9-generic
  34.1GB: initrd.img
  32.9GB: initrd.img.old
  38.6GB: vmlinuz
  32.8GB: vmlinuz.old

I see where there is a conflict.

Gary

---

### Post by chunchengch on 2009-04-11
Error 18 : Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

---

### Post by meierfra. on 2009-04-11
Quote from [Hermanzone]("http://users.bigpond.net.au/hermanzone/p15.htm#18")

> Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented.
2.11 GB or 4095 cylinder limit
3.26 GB or 6322 cylinder limit
4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)It seems you bios are plagued by the 33.8GB limit.  Your older kernel
> 32.9GB: boot/initrd.img-2.6.27-9-generic
is within that limit.  But your new kernel

> 38.6GB: boot/vmlinuz-2.6.27-11-generic
is outside the limit.

You might check whether there is an update available for your bios.
If not you will have to create a separate boot partition. Hermazone has instructions for this:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by ka9mnx on 2009-04-13
Thanks meierfra for your reply.

I don't think that is the problem. I have the latest bios update and it's dated 2007 but I'll check out the link you sent.

Check out my dump and here is where I think the problem is...

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda1 has
45046864 sectors, but according to the info from
fdisk, it has 45057537 sectors.
Operating System: Windows XP
Boot files/dirs: /BOOT.INI /ntldr /NTDETECT.COM

Thanks,
Gary

---

### Post by meierfra. on 2009-04-13
> Boot sector info: According to the info in the boot sector, sda1 has
45046864 sectors, but according to the info from
fdisk, it has 45057537 sectors.
That would only effect booting into XP and a small difference like that usually does not cause any problem. It definitely is not the cause of "grub error 18".

But you might as well fix it: Boot from the LiveCD, download the [testdisk-6.10.linux26.tar.bz2 package]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to your desktop, and then do:


```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk.

---

### Post by ka9mnx on 2009-04-15
Thanks again meierfra.

I fixed the ntfs problem and that made GRUP to quit working. Oh well. I reloaded XP and ubuntu and installed GRUB in the Window$ partition (20GB). You were right. That fixed the limitation problem. First I went to the IBM support site and found a new update for the hard disk. Thought that would fix the problem but it didn't. I'm really surprised that the ThinkPad falls into this problem. But you were right and all is well now. Thanks!
Gary

---

### Post by meierfra. on 2009-04-15
> all is well now. 
Great. Have fun with XP and Ubuntu.

---

