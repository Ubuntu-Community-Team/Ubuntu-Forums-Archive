---
title: "Grub error 18"
date: 2009-02-21
forum: General Help
---

### Post by Kraust on 2009-02-21
I just installed xubuntu 8.10 onto my old Compaq (Like 9 years old). I get a Grub error 18 on start up but my computer still has its original HDD (a 20 GB).

It's not being dual booted with any other OS, and it's on a Clean Partition made by the installer. I should note that the installer made two partitions.

I didn't use a Live CD to do the isntallation, and currently I'm on the same computer but with a BackTrack3 Live CD.

Thanks in advanced.

(Oh and I'm trying to get xubuntu to work <_<. Didn't think I mentioned that.)

---

### Post by caljohnsmith on 2009-02-21
If you didn't use the Live CD to do the installation, what did you use? Did you use the alternate CD? In order to do troubleshooting, it would help greatly if you could download and use a Live CD. So in case you get a Live CD working, how about downloading the **Boot Info Script** to the Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup related to your Grub error 18.

---

### Post by Kraust on 2009-02-21
Yea I used the alternative CD instead of the Live CD, I didn't think it would have been a problem.

I'll go try and get the Live CD and see what I can do.

EDIT: I just tried this using BackTrack (it worked even if it's KDE Based, and I wanted to try it before I wasted an hour of my life DLing the live setup <_<)

> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdc
 => No boot loader is installed in the MBR of /dev/sdb

hdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive hdb: _____________________________________________________________________

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63    27,149,849    27,149,787   c W95 FAT32 (LBA)
/dev/hdb2          27,149,850    58,621,184    31,471,335   5 Extended
/dev/hdb5          27,149,913    57,207,464    30,057,552  83 Linux
/dev/hdb6          57,207,528    58,621,184     1,413,657  82 Linux swap / Solaris


Drive hdc: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 728 MB, 728705024 bytes
255 heads, 63 sectors/track, 22 cylinders, total 355813 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1027 MB, 1027604480 bytes
18 heads, 49 sectors/track, 2275 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 240     2,007,039     2,006,800   6 FAT16

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/hdb1: UUID="B821-72E6" TYPE="vfat" 
/dev/hdb5: UUID="4a4aa737-74ff-4331-a18b-97217ce6e551" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb6: UUID="329e5e36-dc0f-4999-8dfe-948cd0d31280" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="1GB FLASH" UUID="E0FD-1813" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb1 on /mnt/hdb1 type vfat (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/hdb5 on /mnt/hdb5 type ext3 (rw,noatime)
/dev/sda1 on /mnt/sda1 type vfat (rw)
/dev/sdb1 on /mnt/sdb1 type vfat (rw)


=========================== hdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4a4aa737-74ff-4331-a18b-97217ce6e551 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4a4aa737-74ff-4331-a18b-97217ce6e551

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4a4aa737-74ff-4331-a18b-97217ce6e551
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a4aa737-74ff-4331-a18b-97217ce6e551 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4a4aa737-74ff-4331-a18b-97217ce6e551
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a4aa737-74ff-4331-a18b-97217ce6e551 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4a4aa737-74ff-4331-a18b-97217ce6e551
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4a4aa737-74ff-4331-a18b-97217ce6e551 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=329e5e36-dc0f-4999-8dfe-948cd0d31280 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== hdb5: Location of files loaded by Grub: ===================


  16.2GB: boot/grub/menu.lst
  16.2GB: boot/grub/stage2
  16.2GB: boot/initrd.img-2.6.27-7-generic
  16.1GB: boot/vmlinuz-2.6.27-7-generic
  16.2GB: initrd.img
  16.1GB: vmlinuz


<< Sorry if I'm wasting your time by not doing this in xubuntu. It's the same script so I assume the outputs should be the same.

And I can see that it didn't get rid of my FAT32 Partition in the installation?

---

### Post by longtom on 2009-02-22
Sorry - chipping in as absolute beginner - but I had my one grub problem today.

Maybe you want to cast an eye here:

[http://ubuntuforums.org/showthread.php?p=6778570#post6778570](http://ubuntuforums.org/showthread.php?p=6778570#post6778570)

Good luck

longtom

---

### Post by caljohnsmith on 2009-02-22
Just as an FYI, a Grub error 18 is:
> **Error 18**: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle.
So a Grub error 18 typically occurs when you have an older BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. Note from the results of the script you ran:
> **Kraust said:**
> 
```
=================== hdb5: Location of files loaded by Grub: ===================

16.2GB: boot/grub/menu.lst
16.2GB: boot/grub/stage2
16.2GB: boot/initrd.img-2.6.27-7-generic
16.1GB: boot/vmlinuz-2.6.27-7-generic
16.2GB: initrd.img
16.1GB: vmlinuz 
```

Considering your computer is 9 years old, probably it has the 8.4 GB limitation; that would explain your Grub error 18, because all your Ubuntu boot files are located at ~16 GB into the drive, as shown above. The solution is usually simple: put your boot files within the first 8.4 GB of the HDD, and that will probably cure your Grub error 18. Based on what you said, is it safe to assume you don't want that first FAT32 partition on the drive? If so, I would suggest first wiping the HDD's partition table clean so you can start fresh, and then when you use the alternate installer, it should use the entire drive by default to install Ubuntu. Then your Ubuntu partition should be at the front of the drive and you should be OK. If your Backtrack CD has "fdisk", you can delete all partitions on the HDD by first doing:
```
sudo fdisk -lu
```
Make sure your HDD is still "hdb", and then do:
```
sudo fdisk /dev/hdb
```
Choose "o", then "w". That will delete the current partition table on hdb so you can start fresh. Let me know how that goes or if you run into problems.

---

### Post by Kraust on 2009-02-22
Thanks, following that resolved my problem.

---

