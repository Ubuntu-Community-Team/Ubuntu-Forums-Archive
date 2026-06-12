---
title: "Grub Error 13: Unsupported or invalid executable file"
date: 2009-02-07
forum: General Help
---

### Post by WillBMX on 2009-02-07
**Edit: This thread has been solved! Thanks very much to those who posted :D**
**Original post:**

Yup its the old error 13, not sure how to fix it though... my menu.lst looks OK to me, my XP partition is hd(0,0), my Ubuntu partition is hd(0,1). (two hard drives).
It was working fine, all I did was unplug a SATA cable and plu it into a different port. I've put it back how it was but the error remains...

Here's part of my menu.lst (I think this is the significant bit):

```
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
```

Any help would be appreciated.
Thanks:D

---

### Post by 73ckn797 on 2009-02-07
The menu.lst info provided is not what you need to be looking at. The last section of the file is where the system reads info to boot from.

It appears similar to the following:

```
## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Home Edition sp3
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Something may have changed in that part.

---

### Post by WillBMX on 2009-02-07
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,0)
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST
```
That' what I have, and then it ends. Should I have something at the bottom as well?
Is there some way to restore menu.lst?
I Can't see why this has happened as I haven't been in menu.lst...

---

### Post by empty_tank on 2009-02-07
was i correct in reading your post that you have 2 hard drives? Is windows installed in one drive while ubuntu is installed in the second drive?

---

### Post by caljohnsmith on 2009-02-07
I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by WillBMX on 2009-02-07
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdc

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /ntdetect.com

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ae71ae6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,862,899    74,862,837  83 Linux
/dev/sda2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x652d6b3e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,579,791   312,579,729   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064    15,874,047    15,865,984   c W95 FAT32 (LBA)

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a030a893-8630-46b3-966a-a18700f6a820" TYPE="ext3" 
/dev/sda5: UUID="a38134a7-f9e5-4928-ad07-a1d2bfefa559" TYPE="swap" 
/dev/sdb1: UUID="FE3C94033C93B4DD" LABEL="Will_H_drive" TYPE="ntfs" 
/dev/sdc1: UUID="89D1-3FE1" TYPE="vfat" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/will/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=will)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

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
# kopt=root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a030a893-8630-46b3-966a-a18700f6a820

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
# defoptions=vga=792

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a030a893-8630-46b3-966a-a18700f6a820 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a030a893-8630-46b3-966a-a18700f6a820
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,0)
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a030a893-8630-46b3-966a-a18700f6a820 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a38134a7-f9e5-4928-ad07-a1d2bfefa559 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.3GB: boot/grub/menu.lst
   6.1GB: boot/grub/stage2
   6.2GB: boot/initrd.img-2.6.27-11-generic
   6.3GB: boot/initrd.img-2.6.27-7-generic
   6.3GB: boot/initrd.img-2.6.27-9-generic
   6.3GB: boot/vmlinuz-2.6.27-11-generic
   6.2GB: boot/vmlinuz-2.6.27-7-generic
   6.2GB: boot/vmlinuz-2.6.27-9-generic
   6.2GB: initrd.img
   6.3GB: initrd.img.old
   6.3GB: vmlinuz
   6.2GB: vmlinuz.old


That's the results.
I believe that Windows is on one HDD and Ubuntu is on the other, I may well have my C drive partitioned and running both ubuntu and XP though, not 100% sure. When I installed them both though (Windows first) I tried to Do it so eacdh had a separate HDD. Not sure if I pulled it off properly though. It's been running fine for a few months anyhow.
Thanks.

---

### Post by caljohnsmith on 2009-02-07
It looks like part of the issue is that you have Grub installed to the MBR of both your drives, and if you boot the sda drive, you will get a Grub error 13 when trying to boot Windows because Grub is looking on the wrong HDD. To correct it, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
But the other issue is that it looks like your sdb1 Windows partition is missing its boot.ini file, a Windows file necessary to boot. To fix that, how about downloading the attached boot.ini.txt file to your desktop and do:
```
sudo mount /dev/sdb1 /mnt
mv ~/Desktop/boot.ini.txt /mnt/boot.ini
```
Then reboot, select Windows from Grub, and let me know how far you get. We can work from there if necessary.

---

### Post by WillBMX on 2009-02-07
Thanks very much, booted straight into windows, also solved another issue which was that when I tried to boot to Windows before it used to say 'Invalid boot.ini file', then spew a load of other random crap, then boot into Windows. Now it goes straight into the Windows splash screen as the boot.ini file has been restored :D
I very much appreciate the help :D

[for some reason I can't mark this thread as solved, or give you Thanks points or whatever they're called...?]

---

### Post by caljohnsmith on 2009-02-07
Glad to hear that worked OK; cheers and have fun with Ubuntu and Windows. :)

---

