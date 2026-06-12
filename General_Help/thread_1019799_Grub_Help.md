---
title: "Grub Help"
date: 2008-12-23
forum: General Help
---

### Post by bridabom73 on 2008-12-23
I think I should post this here, I would have posted it in the Windows section, but I don't see it anywhere.

I have Windows and Ubuntu installed on different hard drives, and I just changed my motherboard, and now I don't know how to get to Windows. I think its because when I installed Ubuntu, Grub automatically detected where that drive was, and now I think its in a different location. I can't reinstall Ubuntu, because I didn't put my home folder in a different partition.
It might also be a Windows or a motherboard problem, even though it was working fine for my brother, but he didn't have a SATA drive, so that might also be something. When I go to Windows, it say that Windows was shut down incorrectly or whatever, and I go to Start Windows Normally and press enter, and it just goes back to like when you just turn on the computer and goes to Grub again. I also tried safe mode and the last working configuration. Can someone help? My motherboard is an ASUS A7N8X Deluxe.

---

### Post by dcstar on 2008-12-23
> **bridabom73 said:**
> I think I should post this here, I would have posted it in the Windows section, but I don't see it anywhere.

I have Windows and Ubuntu installed on different hard drives, and I just changed my motherboard, and now I don't know how to get to Windows. I think its because when I installed Ubuntu, Grub automatically detected where that drive was, and now I think its in a different location. I can't reinstall Ubuntu, because I didn't put my home folder in a different partition.
It might also be a Windows or a motherboard problem, even though it was working fine for my brother, but he didn't have a SATA drive, so that might also be something. When I go to Windows, it say that Windows was shut down incorrectly or whatever, and I go to Start Windows Normally and press enter, and it just goes back to like when you just turn on the computer and goes to Grub again. I also tried safe mode and the last working configuration. Can someone help? My motherboard is an ASUS A7N8X Deluxe.

Windows will not run on substantially different hardware from its original installation, it is specifically designed **not** to work as an anti-copying method.

Do a web search for your Windows problem and you may find something useful, but you will not find Windows solutions in a Linux forum.

---

### Post by 2hot6ft2 on 2008-12-24
> **dcstar said:**
> Windows will not run on substantially different hardware from its original installation, it is specifically designed **not** to work as an anti-copying method.

Do a web search for your Windows problem and you may find something useful, but you will not find Windows solutions in a Linux forum.
It's like he said. That's the way they have it set up. It looks at the drives serial # and the systems configuration and wont work.

---

### Post by Tanker Bob on 2008-12-24
To get Windows to work, you will have to boot from the Windows CD and "repair" the existing Windows by installing over it. Your data should survive. I did exactly what you did and documented the recovery process [here](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27604&an=0&page=0#Post27604).

You should be able to recover the Linux disk. Try pulling the power from the Windows hard drive, make sure the jumpers are set correctly to make the Linux driver the master, and then try booting Linux alone. If your Linux hard disk won't boot even without the Windows disk installed, download and burn a CD or floppy with [Super Grub Disk](http://www.supergrubdisk.org/). It will be able to fix Grub, or failing that, at least directly boot your system. I've run it from both CD and floppy. The latter is slower but works fine.

The bottom line is that Linux will start up fine on a completely new hardware setup once you get Grub sorted out, but Windows chokes badly.

---

### Post by bridabom73 on 2008-12-28
> **Tanker Bob said:**
> To get Windows to work, you will have to boot from the Windows CD and "repair" the existing Windows by installing over it. Your data should survive. I did exactly what you did and documented the recovery process [here](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27604&an=0&page=0#Post27604).

You should be able to recover the Linux disk. Try pulling the power from the Windows hard drive, make sure the jumpers are set correctly to make the Linux driver the master, and then try booting Linux alone. If your Linux hard disk won't boot even without the Windows disk installed, download and burn a CD or floppy with [Super Grub Disk](http://www.supergrubdisk.org/). It will be able to fix Grub, or failing that, at least directly boot your system. I've run it from both CD and floppy. The latter is slower but works fine.

The bottom line is that Linux will start up fine on a completely new hardware setup once you get Grub sorted out, but Windows chokes badly.

I tried repairing it, but I have no idea what to do. I typed help, but I still don't know what to do to get it to fix what's wrong.

---

### Post by Tanker Bob on 2008-12-28
> **bridabom73 said:**
> I tried repairing it, but I have no idea what to do. I typed help, but I still don't know what to do to get it to fix what's wrong.

If you are running Linux alone with the Windows drive unpowered, just tell SuperGrubDisk to repair Grub. It will repair/install Grub on the only drive it can see - the Linux one. You can also go through the menus to tell SGD exactly which hard drive to repair. All this assumes that Grub is your problem, of course.

And again, to recover your Windows drive, pull the power on the Linux drive, start the Windows install CD. The first time it asks what to do, tell it to install Windows. It will detect your existing install and ask again what to do. The second time it asks, tell it to use the existing installation. I forget the exact words. I give more detail in the link that I posted above.

---

### Post by bridabom73 on 2008-12-28
I found out its not Grub, and its not Windows. I tried reinstalling it with the Linux drive unplugged, and the Windows CD couldn't find any hard drives! >:( Its gotta be the motherboard not being able to read the drive. Its a SATA drive, so I think that I have to set something up so that the motherboard can use it. I can access the drive from Linux, just when I boot from it, it says "Starting up..." and just stays there forever. It doesn't go back to the post screen anymore when I try to run Windows, it just tries to start and that's it.

---

### Post by caljohnsmith on 2008-12-28
With all your HDDs connected, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Tanker Bob on 2008-12-28
> **bridabom73 said:**
> I found out its not Grub, and its not Windows. I tried reinstalling it with the Linux drive unplugged, and the Windows CD couldn't find any hard drives! >:( Its gotta be the motherboard not being able to read the drive. Its a SATA drive, so I think that I have to set something up so that the motherboard can use it. I can access the drive from Linux, just when I boot from it, it says "Starting up..." and just stays there forever. It doesn't go back to the post screen anymore when I try to run Windows, it just tries to start and that's it.
Another quick thought. Windows won't find a hard drive if it isn't the master/primary drive on its chain and the primary drive isn't a FAT/NTFS drive. You might ensure that the Windows drive shows up as the master/primary in its chain, preferably the first chain. Windows is finicky that way. If the Windows drive appears anywhere on the BIOS screen when powered and hooked up, then the problem isn't your motherboard.

Linux, OTOH, couldn't care less. Linux will find and mount any drives that it can find in the system whose file system it understands. I've found that to be true even if a drive is classified as "not installed" in BIOS, but physically attached and powered.

---

### Post by gb5757870 on 2008-12-28
[QUOTE=bridabom73;6452186]I found out its not Grub, and its not Windows. I tried reinstalling it with the Linux drive unplugged, and the Windows CD couldn't find any hard drives! >:( Its gotta be the motherboard not being able to read the drive. Its a SATA drive, so I think that I have to set something up so that the motherboard can use it. I can access the drive from Linux, just when I boot from it, it says "Starting up..." and just stays there forever. It doesn't go back to the post screen anymore when I try to run Windows, it just tries to start and that's it.[/QUOTE

Hey, thought I'd let you know that I have a very similar problem. In fact I have the same problem, except that I didn't replace any motherboards. XP just doesn't want to boot, gives the "Starting Up" error when selected from grub. I'm getting some help in this thread: [http://ubuntuforums.org/showthread.php?p=6453466#post6453466](http://ubuntuforums.org/showthread.php?p=6453466#post6453466)

---

### Post by bridabom73 on 2008-12-29
> **caljohnsmith said:**
> With all your HDDs connected, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

Okay this is long.

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 49030380.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbce1bce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     1028159      514048+   b  W95 FAT32
/dev/sda2   *     1028160   115234244    57103042+  83  Linux
/dev/sda3       115234245   117226304      996030   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb846ed4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    49030379    24515158+   7  HPFS/NTFS
/dev/sdb2        49030380   195800219    73384920    7  HPFS/NTFS

sfdisk -V /dev/sdb:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3C32-0CDF" TYPE="vfat" 
/dev/sda2: UUID="db82548f-5da4-49da-ba8e-ae496a4bfad0" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="8a1d2d3c-9a35-470f-b1ad-7292eae5da2c" 
/dev/sdb1: UUID="72F8F50CF8F4CEFB" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb2: UUID="249CCFB69CCF8132" LABEL="Local Disk" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,1)/boot/grub/splashimages/Mac4Lin_1.0_GRUB3.xpm.gz

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
# kopt=root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=db82548f-5da4-49da-ba8e-ae496a4bfad0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3C32-0CDF  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=72F8F50CF8F4CEFB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=249CCFB69CCF8132 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=8a1d2d3c-9a35-470f-b1ad-7292eae5da2c none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

================================== sda2/boot: ==================================

total 89316
drwxr-xr-x  3 root root    4096 2008-12-23 14:08 .
drwxr-xr-x 21 root root    4096 2008-11-28 11:53 ..
-rw-r--r--  1 root root  424317 2007-10-14 21:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-21 23:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   75311 2007-10-14 21:39 config-2.6.22-14-generic
-rw-r--r--  1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-21 23:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  4 root root    4096 2008-12-23 14:08 grub
-rw-r--r--  1 root root    5466 2008-07-13 10:58 grub.menu.lst.copy
-rw-r--r--  1 root root 7268180 2008-12-23 14:08 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7268172 2008-12-23 00:54 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7514169 2008-12-23 14:07 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7513960 2008-12-23 00:54 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7516991 2008-12-23 14:07 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7516983 2008-12-23 00:54 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7518509 2008-12-23 14:07 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7518962 2008-12-23 00:54 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7519334 2008-12-23 14:07 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7519356 2008-12-23 00:53 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  823535 2007-10-14 21:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-21 23:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1764280 2007-10-14 21:39 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-21 23:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda2/boot/grub: ===============================

total 236
drwxr-xr-x 4 root root   4096 2008-12-23 14:08 .
drwxr-xr-x 3 root root   4096 2008-12-23 14:08 ..
-rw-r--r-- 1 root root    197 2002-01-02 15:17 default
-rw-r--r-- 1 root root     30 2002-01-02 15:17 device.map
-rw-r--r-- 1 root root   8660 2002-01-02 15:17 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2002-01-02 15:17 fat_stage1_5
-rw-r--r-- 1 root root     15 2002-01-02 15:17 installed-version
-rw-r--r-- 1 root root   9152 2002-01-02 15:17 jfs_stage1_5
-rw-r--r-- 1 root root   6014 2008-12-23 14:08 menu.lst
-rw-r--r-- 1 root root   6014 2008-12-23 14:08 menu.lst~
-rw-r--r-- 1 root root   5466 2008-07-13 11:09 menu.lst.backup
-rw-r--r-- 1 root root   7860 2002-01-02 15:17 minix_stage1_5
-rw-r--r-- 1 root root  10132 2002-01-02 15:17 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-21 15:57 splash
drwxr-xr-x 2 root root   4096 2008-10-21 16:02 splashimages
-rw-r--r-- 1 root root    512 2002-01-02 15:17 stage1
-rw-r--r-- 1 root root 110292 2002-01-02 15:17 stage2
-rw-r--r-- 1 root root   9980 2002-01-02 15:17 xfs_stage1_5

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /kernel=osxboot.exe

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2008-12-29
According to the script output you posted, it looks like Grub is configured to boot Windows OK, so it looks like you have a Windows problem rather than a Grub problem. One thing you could do to check whether that is true is to set your BIOS to boot the Windows drive on start up, and then you should boot straight into Windows (if Windows is OK). If you still have problems, I would boot your Windows Install CD, go to the "recovery console" and run:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Windows again to see if anything changed. How about trying that and let me know how it goes.

---

### Post by bridabom73 on 2008-12-29
I tried running with only the Windows drive, its just the same Starting Up... error. I tried running chkdsk /r, it just comes up with:
```
The volume Serial Number is 3c32-0cdf
CHKDSK is checking the volume...
CHKDSK is performing additional checking or recovery...
CHKSDK has finished checking the volume.
   513024 kilobytes total disk space.
   512800 kilobytes are available.

     4096 bytes in each allocation unit.
   128256 total allocation units on disk.
   128200 allocation units available on disk.
```
It didn't report any errors (At least I don't think it did), and it still stays stuck at Starting Up... I ran it twice, then tried to load Windows, then I did it again so I could post what came up. What do you suppose I do now?

---

### Post by caljohnsmith on 2008-12-29
Since you changed your motherboard, that would be the most likely cause of why you can't boot Windows any more. One last thing that would be worth checking is to see if testdisk finds anything wrong with the Windows boot sector, because it is quick and easy to check it with testdisk. To use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP.

If the testdisk claims the boot sectors match though, I think about the only remaining option (short of reinstalling) is to do a "Windows Repair" from your Windows Install CD; after booting the Install CD, select the "install Windows" option, and then after that you will be given the opportunity to do a "Windows Repair". Good luck and let me know how it goes.

---

### Post by bridabom73 on 2008-12-29
At when it says "Extrapolated boot sector and current boot sector are different" it only says Dump, List, and Exit, there's no write. What do I do? I tried booting Windows again, and the same Starting Up... error, and I tried installing Windows again, and it for some reason didn't find the hard drive that Windows was already on. I'm 100% sure that it didn't, because I had unplugged the Linux drive, and it said that it didn't find any hard drives. When I boot with only the Windows drive, it goes to where it says Start Windows Normally, and Last Good Configuration, and Safe Mode and stuff. When I try to do all three of those options, its just like my computer gets reset or something. It goes back to the memory test and stuff. But with the Linux drive in, when I go to Windows, it comes up with Starting Up... and just stays there.

---

