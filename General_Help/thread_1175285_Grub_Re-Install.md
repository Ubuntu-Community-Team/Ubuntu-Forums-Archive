---
title: "Grub Re-Install"
date: 2009-06-01
forum: General Help
---

### Post by CFBauer on 2009-06-01
Hey,

I recently purchased, and installed Ubuntu on a new hard drive. My system currently has three drives, though I will be removing one shortly. SDA1 has Ubuntu, with /home and / partitions. SDA2 has 4 partitions, most notably one with my Windows XP install. The SDA3 is ext3 for storage, which I will be removing soon.

When booting before grub even comes up, I get:

> Grub Loading Stage 1.5

Error 15

[This]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5") guide introduced me to Super Grub Disk, which got me past that bootloader and into my Ubuntu install. Everything seems to work fine.

That guide instructed me to reinstall grub using sudo grub-install /dev/sda after deleting (but backing up!) all but menu.lst in /boot/grub. It doesn't seem to fix the grub issue. Here is the output.

```
chris@chris-desktop:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

Also, when booting into my XP partition using Super Grub Disck, I get an error 13. 

I ran a boot info script which should provide lots of nuggets of info about my current setup:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00097a38

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    63,488,879    63,488,817  83 Linux
/dev/sda2          63,488,880 1,953,520,064 1,890,031,185  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeed5eed5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    32,772,599    32,772,537   7 HPFS/NTFS
/dev/sdb2          32,772,600   488,392,064   455,619,465   f W95 Ext d (LBA)
/dev/sdb5          32,772,663   268,414,019   235,641,357   7 HPFS/NTFS
/dev/sdb6         268,414,083   483,974,189   215,560,107  83 Linux
/dev/sdb7         483,974,253   488,392,064     4,417,812  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0eb277a0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   197,165,744   197,165,682  83 Linux
/dev/sdc2         197,165,745   234,436,544    37,270,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="bd3db902-d2d9-4db4-bb6a-b52cd61a5319" TYPE="ext3" 
/dev/sda2: UUID="488ccf5d-c462-4b85-a3bb-e859efb7835a" TYPE="ext3" 
/dev/sdb1: UUID="D8309E25309E0B20" LABEL="Windows HD" TYPE="ntfs" 
/dev/sdb5: UUID="DEB872C6B8729D29" LABEL="Programs" TYPE="ntfs" 
/dev/sdb6: UUID="af26ee47-7ed8-4415-b74a-0e3a1dab487e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="b7038085-acfe-4465-bc7c-c6f1154a9956" TYPE="swap" 
/dev/sdc1: UUID="16ed371c-1e50-4eb1-9e25-d00baa87617a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="fb14e243-b73f-47d1-bb68-eb0f10402929" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)


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
# kopt=root=UUID=bd3db902-d2d9-4db4-bb6a-b52cd61a5319 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bd3db902-d2d9-4db4-bb6a-b52cd61a5319

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
uuid		bd3db902-d2d9-4db4-bb6a-b52cd61a5319
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bd3db902-d2d9-4db4-bb6a-b52cd61a5319 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bd3db902-d2d9-4db4-bb6a-b52cd61a5319
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bd3db902-d2d9-4db4-bb6a-b52cd61a5319 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bd3db902-d2d9-4db4-bb6a-b52cd61a5319
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
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bd3db902-d2d9-4db4-bb6a-b52cd61a5319 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=488ccf5d-c462-4b85-a3bb-e859efb7835a /home           ext3    relatime        0       2
# swap was on /dev/sdb7 during installation
UUID=b7038085-acfe-4465-bc7c-c6f1154a9956 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.6GB: boot/grub/menu.lst
   7.5GB: boot/grub/stage2
   7.5GB: boot/initrd.img-2.6.28-11-generic
   7.5GB: boot/vmlinuz-2.6.28-11-generic
   7.5GB: initrd.img
   7.5GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer

=======Devices which don't seem to have a corresponding hard drive==============

sde 
```
If anyone has any suggestions, I would greatly appreciate them. Thanks.

---

### Post by lindsay7 on 2009-06-01
Well you can try this, but your drives have windows partitions and Ubuntu partitions mixed through out them and grub is installed on each drive.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit

---

### Post by CFBauer on 2009-06-01
> **lindsay7 said:**
> Well you can try this, but your drives have windows partitions and Ubuntu partitions mixed through out them and grub is installed on each drive.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit
I agree my partitions are a bit of a mess. Hopefully my new drive will help me sort everything out, as it's a 1TB which will be all Ubuntu, and my old SDA2 can go all Windows.

Thanks for your suggestion Lindsay, I gave it a try, but am still seeing the Error 15 before grub loads.

---

### Post by lindsay7 on 2009-06-01
Check your bios and see which drive it is booting off first, change it to the other  drive and see if that will fix it.

---

### Post by CFBauer on 2009-06-01
> **lindsay7 said:**
> Check your bios and see which drive it is booting off first, change it to the other  drive and see if that will fix it.
Right on, that did it! Grub now boots up and loads Ubuntu perfectly, thank you.

Unfortunately, I'm still getting the "error 13" message from Windows. Strangely, I've had this issue before. I have no idea how I fixed it though, one day it just loaded. I thought it was from mounting my Windows partitions in Linux (opening them in Nautilus), but that didn't do the trick this time.

Also, while I have you here and can further take advantage of your knowledge, is there anything I need to do soft-ware wise to physically remove my old HD (SDA3, 120GB)?

---

### Post by CFBauer on 2009-06-01
Good news, I got XP running. I switched from hd(1,0) to hd(2,0).

---

### Post by lindsay7 on 2009-06-01
Great news.  As far a sofware for changing out a drive. You normally do not need and but some retail drives come with software to clone drives and set on up. but you partition it and format it with Gparted which you can get form synaptic or what I like to do is get the cd live file from their web site, burn it to a cd and you can boot from it. That way all the drives on your computer are unmonted and it makes it easy to work on.

---

### Post by CFBauer on 2009-06-02
Sweet. Thanks again.

---

