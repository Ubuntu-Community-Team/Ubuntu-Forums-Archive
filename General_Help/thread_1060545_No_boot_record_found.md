---
title: "No boot record found"
date: 2009-02-04
forum: General Help
---

### Post by GMachine_24 on 2009-02-04
Hi. I was attempting to back up my Ubuntu 8.04 system by booting from the systemrescuecd and using partimage (included on the CD) but I got an error message saying there wasn't enough memory to load the kernel....

so I attempted alternative boot choices from the systemrescuecd and finally got a message stating there was an error reading from the CD and my only choice at that point was to reboot the computer . . . so I removed the systemrescuecd, rebooted the computer and got the "no boot record found" message ... the message then said I should reboot my computer....which I did but ended up with the same "no boot record found" .....

I have a couple "live" Linux CDs to boot from if there is some way to restore the MBR.... Kubuntu... Knoppix.... and I can d/l any other one that might be of use....

I've searched the Net and Ubuntu forums for a couple hours and haven't really found anything that addresses this problem ...

Thanks to anyone who can assist . . . 


--gm

---

### Post by caljohnsmith on 2009-02-04
Do you have internet access from one of your Live CDs? If so, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal if it's Ubuntu) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by GMachine_24 on 2009-02-04
Here is the output from the RESULTS.txt file per your request:


```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Gag is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   398,283,479   398,283,417  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   308,062,439   308,062,377  83 Linux
/dev/sdc2         308,062,440   312,576,704     4,514,265   5 Extended
/dev/sdc5         308,062,503   312,576,704     4,514,202  82 Linux swap / Solaris


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders, total 39862368 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    39,857,264    39,857,202  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d15107c9-faf7-4182-8ec2-02bfe590ad14" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="9ae414ba-60e7-4c2e-8068-ed9d42726ad9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="3dfa3190-6a78-4429-ae03-1317983e0542" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="158b34c5-40ba-4d8d-af79-da1e6253e786" 
/dev/sdd1: UUID="58364c74-b552-401a-acd9-4122c586d715" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

rootfs on / type rootfs (rw)
tmpfs on /initrd/pup_rw type tmpfs (rw,size=1513700k)
tmpfs on /initrd/mnt/tmpfs type tmpfs (rw,size=94324k)
/dev/loop0 on /initrd/pup_ro2 type squashfs (ro,noatime)
unionfs on / type aufs (rw,si=30e92819,xino=/initrd/pup_rw/.aufs.xino,diropq=w,dirs=/initrd/pup_rw=rw:/initrd/pup_ro2=ro)
none on /proc type proc (rw)
none on /dev/pts type devpts (rw,gid=2,mode=620)
none on /sys type sysfs (rw)
none on /proc/bus/usb type usbfs (rw)
/dev/sdd1 on /mnt/sdd1 type ext3 (rw,errors=continue,data=ordered)
/dev/sdc1 on /mnt/sdc1 type ext3 (rw,errors=continue,data=ordered)
/dev/sdb1 on /mnt/sdb1 type ext3 (rw,errors=continue,data=ordered)
/dev/sda1 on /mnt/sda1 type ext3 (rw,errors=continue,data=ordered)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dfa3190-6a78-4429-ae03-1317983e0542 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3dfa3190-6a78-4429-ae03-1317983e0542 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=158b34c5-40ba-4d8d-af79-da1e6253e786 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1              /media/120GB            ext3    defaults        1        2
/dev/sdb1       /media/200GB         ext3         defaults     1       2
#/dev/sdd1       /media/20GB           ext3        defaults     1       2

=================== sdc1: Location of files loaded by Grub: ===================


  70.9GB: boot/grub/menu.lst
  70.9GB: boot/grub/stage2
  70.9GB: boot/initrd.img-2.6.24-16-generic
  70.9GB: boot/initrd.img-2.6.24-16-generic.bak
  70.8GB: boot/initrd.img-2.6.24-21-generic
  70.9GB: boot/initrd.img-2.6.24-21-generic.bak
  70.9GB: boot/initrd.img-2.6.24-22-generic
  70.9GB: boot/initrd.img-2.6.24-22-generic.bak
  71.0GB: boot/initrd.img-2.6.24-23-generic
  70.9GB: boot/initrd.img-2.6.24-23-generic.bak
  70.9GB: boot/vmlinuz-2.6.24-16-generic
  70.9GB: boot/vmlinuz-2.6.24-21-generic
  70.9GB: boot/vmlinuz-2.6.24-22-generic
  70.9GB: boot/vmlinuz-2.6.24-23-generic
  71.0GB: initrd.img
  70.9GB: initrd.img.old
  70.9GB: vmlinuz
  70.9GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

 hda .
 hdb .
 hdc .
 hdd .
 sde .
 sdf .
 sdg .
 sdh .
 sdi .


```

I believe the problem is located here:

```


=> Gag is installed in the MBR of /dev/sdc


```

Gag is a GUI boot utility located on the systemrescueCD (and this is something I didn't know until too late) when you run Gag, it overwrites the MBR with its own info and then, when you quit Gag, it is supposed to "rewrite" the original MBR . . . something I would never have tried if I'd figured this out ahead of time.

I am using the live boot CD from Puppy Linux (which seems to work very well - automatically mounting all drives to the desktop.

Anyway, if there is a fix here, I'd appreciate knowing about it.

--gm

---

### Post by caljohnsmith on 2009-02-05
Yes, it would be good to reinstall Grub to your Ubuntu sdc drive I think instead of using Gag. Also, to get a "no boot record found" on start up probably means your BIOS is set to boot your 200 GB sdb drive before the other drives. How about going into your BIOS and make sure that the sdc Ubuntu drive is before your other drives in the BIOS boot order, and then try reinstalling Grub:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
If the commands complete successfully, reboot, make sure your BIOS is set to boot the Ubuntu drive, and let me know how far you get. We can work from there.

---

### Post by GMachine_24 on 2009-02-05
Hey - thanks for your time but I solved the problem. I used Super Grub Disk 

```


http://www.supergrubdisk.org/


```

booted from the CD, used the automated restore MBR etc. command from the boot page (for *beginners*) and everything was fixed in less than a minute.

I recommend Super Grub Disk (and its Web site) to anyone having boot problems - there is a lot of useful information there.

--gm

---

