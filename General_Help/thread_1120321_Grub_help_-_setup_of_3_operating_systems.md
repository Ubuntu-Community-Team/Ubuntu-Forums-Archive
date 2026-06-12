---
title: "Grub help - setup of 3 operating systems"
date: 2009-04-08
forum: General Help
---

### Post by Nixie Pixel on 2009-04-08
Hello, I am having problems getting grub to work with my 3 installed O/Ss.  HDD A has Vista 64 on it, HDD B has Jaunty Jackalope and XP32 on it.  Right now grub will only boot to Vista 64 and Jaunty from the bootloader on disk A.  I tried adding my own XP32 entry but it is telling me that the device is invalid.  Please see my fdisk and menu.lst info below.

fdisk:
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ae24bbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7783    62516224    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa453fc98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12749   102400000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           12750       60801   385977690    5  Extended
/dev/sdb5           12750       13235     3903763+  82  Linux swap / Solaris
/dev/sdb6           13236       15667    19535008+  83  Linux
/dev/sdb7           15668       58889   347180683+  83  Linux
/dev/sdb8           58890       60801    15358108+   7  HPFS/NTFS
```

menu.lst snippet:
```
uuid	a920f9e7-790d-4ad5-a292-9914b187d1d0
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry added by me, poorly, to try and get XP32 working
# on /dev/sda1
title		Windows XP Home 32-bit (loader)
rootnoverify	(hd1,8)
savedefault
makeactive
chainloader	+1
```

Can anyone tell me what I've done wrong here?

Thanks!

---

### Post by meierfra. on 2009-04-08
Try

title		Windows XP Home 32-bit (loader)
rootnoverify	(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1


**If this does not work:**

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by Nixie Pixel on 2009-04-08
Instead of telling me there was an invalid device, a screen pops up for half a second that appears to ask if I want to use "an older version of Windows" or "Windows Vista," but it is gone too quickly to make any changes.

Here is the result of the script:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ae24bbe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            128   125,032,575   125,032,448   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa453fc98

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,812,685   976,768,064   771,955,380   5 Extended
/dev/sdb5         204,812,748   212,620,274     7,807,527  82 Linux swap / Solaris
/dev/sdb6         212,620,338   251,690,354    39,070,017  83 Linux
/dev/sdb7         251,690,418   946,051,784   694,361,367  83 Linux
/dev/sdb8         946,051,848   976,768,064    30,716,217   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 32.0 GB, 32078036992 bytes
5 heads, 32 sectors/track, 391577 cylinders, total 62652416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3202a88c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064    62,652,415    62,644,352   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2ED0DBE8D0DBB3F5" TYPE="ntfs" 
/dev/sdb1: UUID="949CF73B9CF71708" LABEL="Barracuda" TYPE="ntfs" 
/dev/sdb5: UUID="bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8" TYPE="swap" 
/dev/sdb6: UUID="a920f9e7-790d-4ad5-a292-9914b187d1d0" TYPE="ext3" 
/dev/sdb7: UUID="eace83b9-d4f6-48ca-bb0e-cbce8bc7267e" TYPE="ext3" 
/dev/sdb8: UUID="7E0007A15EC5936D" LABEL="XP32home" TYPE="ntfs" 
/dev/sdc1: LABEL="PATRIOT" UUID="65E9-D6B7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nixie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nixie)
/dev/sdc1 on /media/PATRIOT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a920f9e7-790d-4ad5-a292-9914b187d1d0

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

uuid	a920f9e7-790d-4ad5-a292-9914b187d1d0
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry added by me, poorly, to try and get XP32 working
# on /dev/sda1
title		Windows XP Home 32-bit (loader)
rootnoverify	(hd1,8)
savedefault
makeactive
chainloader	+1

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=eace83b9-d4f6-48ca-bb0e-cbce8bc7267e /home           ext3    relatime        0       2
# none was on /dev/sdb5 during installation
UUID=bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 120.1GB: boot/grub/menu.lst
 120.2GB: boot/grub/stage2
 120.2GB: boot/initrd.img-2.6.28-11-generic
 120.2GB: boot/initrd.img-2.6.28-9-generic
 120.2GB: boot/vmlinuz-2.6.28-11-generic
 120.1GB: boot/vmlinuz-2.6.28-9-generic
 120.2GB: initrd.img
 120.2GB: initrd.img.old
 120.2GB: vmlinuz
 120.1GB: vmlinuz.old
```

Edit: I had a USB drive (Patriot - /dev/sdc) plugged in when I ran this, sorry)

---

### Post by meierfra. on 2009-04-08
All the boot files for XP are on /dev/sdb1 (the first partition on your ubuntu drive)) So the XP entry I gave you is the correct one. But Vista overwrote the boot sector of /dev/sdb1. So I suggest  to restore the boot sector of /dev/sdb1:

**If you have an XP CD**

Boot from the XP CD and press "r" to get to repair console.
Type 

```
map
```
to determine the  drive letter of /dev/sdb1.

Then type

```
fixboot D:
```
(but replace "D" by the drive letter of /dev/sdb1

**If you don't have a XP CD, but have a Vista CD**

Boot from the Vista CD. Choose "Repair Computer" and at the new screen choose "command line".
type

```
diskpart
list volume 
quit
```

to determine the drive letter of your CD drive and of /dev/sdb1.
Then

```
E:\boot\bootsect.exe /nt52  D:
```
but replace "E:" by the drive letter of CD drive and "D:" by the drive letter of /dev/sdb1.


If you  don't have any Windows CD, let me know, and I can show you how to fix the boot sector from Ubuntu.

---

### Post by Nixie Pixel on 2009-04-10
Ok, so I took your advice and repaired the XP32 drive with an XP disk.  Thank you!  

Unfortunately, I had to reinstall Vista on the first hard drive, which of course messed up the boot manager again.  But this time I forgot to switch the drive order in BIOS before installing Vista, so no boot manager was loaded at all.  

Unfortunately I can't see the disk at all using the Vista DVD, diskpart isn't finding the drive and I'm not sure why.  So now I ask for your assistance in doing this in Ubuntu.

Thanks!

---

### Post by meierfra. on 2009-04-10
Could you run the boot_info_script  and post RESULT.txt again, so what I can figure out you current setup?  (Make sure to post the new RESULTS.txt If you didn't delete the old one, it will be called RESULTS1.txt)

---

### Post by Nixie Pixel on 2009-04-10
The first (Vista) drive has failed.  I am going to re-flash the firmware to try and correct the problem.  However, I need access to XP, and currently I don't have it.  I ran the fixboot program on each of my two NTFS partitions, but I can't get the bootloader to work.  Here is the current results file:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 137.4 GB, 137438953472 bytes
255 heads, 63 sectors/track, 16709 cylinders, total 268435456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa453fc98

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,812,685   976,768,064   771,955,380   5 Extended
/dev/sdb5         204,812,748   212,620,274     7,807,527  82 Linux swap / Solaris
/dev/sdb6         212,620,338   251,690,354    39,070,017  83 Linux
/dev/sdb7         251,690,418   946,051,784   694,361,367  83 Linux
/dev/sdb8         946,051,848   976,768,064    30,716,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="949CF73B9CF71708" LABEL="Barracuda" TYPE="ntfs" 
/dev/sdb5: UUID="bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8" TYPE="swap" 
/dev/sdb6: UUID="a920f9e7-790d-4ad5-a292-9914b187d1d0" TYPE="ext3" 
/dev/sdb7: UUID="eace83b9-d4f6-48ca-bb0e-cbce8bc7267e" TYPE="ext3" 
/dev/sdb8: UUID="7E0007A15EC5936D" LABEL="XP32home" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nixie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nixie)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a920f9e7-790d-4ad5-a292-9914b187d1d0

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

uuid	a920f9e7-790d-4ad5-a292-9914b187d1d0
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added by me, poorly, to try and get XP32 working
# on /dev/sda1
title Windows XP Home 32-bit (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=eace83b9-d4f6-48ca-bb0e-cbce8bc7267e /home           ext3    relatime        0       2
# none was on /dev/sdb5 during installation
UUID=bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 120.2GB: boot/grub/menu.lst
 120.2GB: boot/grub/stage2
 120.2GB: boot/initrd.img-2.6.28-11-generic
 120.2GB: boot/initrd.img-2.6.28-9-generic
 120.2GB: boot/vmlinuz-2.6.28-11-generic
 120.1GB: boot/vmlinuz-2.6.28-9-generic
 120.2GB: initrd.img
 120.2GB: initrd.img.old
 120.2GB: vmlinuz
 120.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  5a 0c ff 3f 37 c8 10 00  00 00 00 00 3f 00 00 00  |Z..?7.......?...|
00000010  00 00 00 00 31 30 33 32  35 34 37 36 39 38 62 61  |....1032547698ba|
00000020  66 63 30 63 34 35 36 39  00 00 00 08 00 30 30 30  |fc0c4569.....000|
00000030  50 2e 30 38 20 20 41 59  41 54 44 50 4e 4f 20 47  |P.08  AYATDPNO G|
00000040  41 42 45 52 4f 46 54 4f  52 2d 4d 4f 20 20 20 20  |ABEROFTOR-MO    |
00000050  20 20 20 20 20 20 20 20  20 20 20 20 20 20 10 80  |              ..|
00000060  00 00 00 2f 00 40 00 02  00 02 07 00 ff 3f 10 00  |.../.@.......?..|
00000070  3f 00 10 fc fb 00 10 01  00 00 00 10 00 00 07 00  |?...............|
00000080  03 00 78 00 78 00 78 00  78 00 00 00 00 00 00 00  |..x.x.x.x.......|
00000090  00 00 00 00 00 00 01 00  06 07 00 00 00 00 00 00  |................|
000000a0  e0 00 00 00 20 40 00 44  00 40 20 40 00 04 00 40  |.... @.D.@ @...@|
000000b0  3f 40 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |?@..............|
000000c0  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
000000d0  00 00 00 00 00 40 00 00  00 00 00 00 00 00 00 00  |.....@..........|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 a5 45  |...............E|
00000200
```

Thanks again for your help.

---

### Post by meierfra. on 2009-04-10
The boot sector seems to be ok, but the boot files have disappeared.  Did you reformat /dev/sdb1?  I suggest to follow this tutorial: 

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

and place the boot files in your XP parrtition /dev/sdb8.

In step 1 use /dev/sdb8

In step 3 use partition(5)

In step 4 use

title XP
rootnoverify (hd0,7)
chainloader +1

You don't need to do Step 5

---

### Post by ubockto on 2009-04-10
Use the kgrubeditor in your synaptic package manager to solve any difficulties, and learn and weep, just like me:lolflag:

---

### Post by Nixie Pixel on 2009-04-10
Ok, I am about to follow the tutorial to restore the boot manager(s).

However, I think my partition table is messed up - I was able to recover the boot drive but I think there are issues with the partitions:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 234837042 
    on boot drive #2 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #6 for /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000050

Partition  Boot         Start           End          Size  Id System

/dev/sda1           5,729,571    51,895,193    46,165,623  c2 Hidden Linux/PowerBoot
/dev/sda2    *  3,788,505,088 3,788,505,090             3  a3 Unknown
/dev/sda3          22,844,420    47,748,099    24,903,680   0 Empty
/dev/sda4             131,072       393,543       262,472   0 Empty

/dev/sda1 overlaps with /dev/sda3
/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa453fc98

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,812,685   976,768,064   771,955,380   5 Extended
/dev/sdb5         204,812,748   212,620,274     7,807,527  82 Linux swap / Solaris
/dev/sdb6         212,620,338   251,690,354    39,070,017  83 Linux
/dev/sdb7         251,690,418   946,051,784   694,361,367  83 Linux
/dev/sdb8         946,051,848   976,768,064    30,716,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="949CF73B9CF71708" LABEL="Barracuda" TYPE="ntfs" 
/dev/sdb5: UUID="bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8" TYPE="swap" 
/dev/sdb6: UUID="a920f9e7-790d-4ad5-a292-9914b187d1d0" TYPE="ext3" 
/dev/sdb7: UUID="eace83b9-d4f6-48ca-bb0e-cbce8bc7267e" TYPE="ext3" 
/dev/sdb8: UUID="7E0007A15EC5936D" LABEL="XP32home" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nixie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nixie)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a920f9e7-790d-4ad5-a292-9914b187d1d0

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

uuid	a920f9e7-790d-4ad5-a292-9914b187d1d0
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		a920f9e7-790d-4ad5-a292-9914b187d1d0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added by me, poorly, to try and get XP32 working
# on /dev/sda1
title Windows Vista Ultimate 64-bit (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=a920f9e7-790d-4ad5-a292-9914b187d1d0 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=eace83b9-d4f6-48ca-bb0e-cbce8bc7267e /home           ext3    relatime        0       2
# none was on /dev/sdb5 during installation
UUID=bf1d75d9-c0da-4252-9c0a-7c4c549dc8d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 120.2GB: boot/grub/menu.lst
 120.2GB: boot/grub/stage2
 120.2GB: boot/initrd.img-2.6.28-11-generic
 120.2GB: boot/initrd.img-2.6.28-9-generic
 120.2GB: boot/vmlinuz-2.6.28-11-generic
 120.1GB: boot/vmlinuz-2.6.28-9-generic
 120.2GB: initrd.img
 120.2GB: initrd.img.old
 120.2GB: vmlinuz
 120.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  00 00 ff b6 78 01 00 00  ff d7 3b c3 89 45 fc 74  |....x.....;..E.t|
00000010  40 89 45 d8 8d 45 d8 50  6a 01 68 04 11 00 00 ff  |@.E..E.Pj.h.....|
00000020  b6 78 01 00 00 ff d7 8b  45 d8 8b 4d e4 40 89 45  |.x......E..M.@.E|
00000030  e8 8b 45 dc 03 c1 99 2b  c2 d1 f8 6a 01 89 45 ec  |..E....+...j..E.|
00000040  8d 45 e8 50 53 ff b6 78  01 00 00 ff 15 90 17 01  |.E.PS..x........|
00000050  75 81 8e 9c 01 00 00 00  10 00 00 eb 59 0f bf 45  |u...........Y..E|
00000060  08 0f bf 4d 0c 89 45 e8  89 45 d8 8d 45 d8 50 ff  |...M..E..E..E.P.|
00000070  b6 78 01 00 00 89 4d ec  89 4d dc ff 15 20 16 01  |.x....M..M... ..|
00000080  75 8b 3d f8 17 01 75 8d  45 d8 50 53 68 11 11 00  |u.=...u.E.PSh...|
00000090  00 ff b6 78 01 00 00 ff  d7 3b c3 89 45 fc 0f 84  |...x.....;..E...|
000000a0  78 01 00 00 f6 86 98 01  00 00 08 75 09 f6 45 e0  |x..........u..E.|
000000b0  46 75 03 89 5d fc 39 5d  fc 0f 84 5d 01 00 00 8d  |Fu..].9]...]....|
000000c0  45 f4 50 6a 01 ff 75 fc  8b ce e8 69 fc ff ff 85  |E.Pj..u....i....|
000000d0  c0 0f 8c f3 01 00 00 ff  75 fc 6a 08 68 0b 11 00  |........u.j.h...|
000000e0  00 ff b6 78 01 00 00 ff  d7 8b 45 f4 8d 8e a4 00  |...x......E.....|
000000f0  00 00 51 8d 9e b4 01 00  00 50 89 03 e8 c8 30 e5  |..Q......P....0.|
00000100  ff ff 75 fc 8b ce ff 33  e8 07 72 ff ff 85 c0 89  |..u....3..r.....|
00000110  45 f8 0f 84 d8 00 00 00  6a 00 ff b6 78 01 00 00  |E.......j...x...|
00000120  6a 00 ff 75 ec ff 75 e8  6a 28 e8 62 2b e7 ff f7  |j..u..u.j(.b+...|
00000130  d8 1b c0 83 e0 08 0d 02  01 00 00 50 ff 75 f8 ff  |...........P.u..|
00000140  15 78 18 01 75 89 45 f0  8d 45 fc 50 68 e4 f8 09  |.x..u.E..E.Ph...|
00000150  75 68 3c 16 0c 75 ff b6  20 01 00 00 e8 4c 79 e7  |uh<..u.. ....Ly.|
00000160  ff 85 c0 7c 14 8b 45 fc  8b 08 6a 00 50 ff 51 20  |...|..E...j.P.Q |
00000170  8b 45 fc 8b 08 50 ff 51  08 8b 45 e8 89 45 d8 8b  |.E...P.Q..E..E..|
00000180  45 ec 89 45 dc 8d 45 d8  50 ff b6 78 01 00 00 ff  |E..E..E.P..x....|
00000190  15 20 16 01 75 8d 45 d8  50 6a 00 68 11 11 00 00  |. ..u.E.Pj.h....|
000001a0  ff b6 78 01 00 00 ff d7  85 c0 74 3b 8b 4d f0 85  |..x.......t;.M..|
000001b0  c9 74 34 83 c1 f5 51 ff  33 8b ce 50 89 86 70 01  |.t4...Q.3..P..p.|
000001c0  00 00 e8 32 a6 ff ff f6  86 ac 01 00 00 01 74 17  |...2..........t.|
000001d0  66 f7 86 9c 01 00 00 00  20 75 0c ff b6 78 01 00  |f....... u...x..|
000001e0  00 ff 15 f4 18 01 75 ff  75 f8 ff 15 d8 17 01 75  |......u.u......u|
000001f0  6a 00 ff 33 e8 d0 2f e5  ff 53 e8 9e 03 de ff 83  |j..3../..S......|
00000200

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

---

### Post by meierfra. on 2009-04-10
> However, I think my partition table is messed up - I was able to recover the boot drive but I think there are issues with the partitions:
Yup, the partition table on 64 GB drive is messed up.  But let's worry about that later.  Follows the tutorial to recover  the XP boot files  and set your bios to boot from the 500GB  Ubuntu/XP drive. Then the messed up partition table on the 64GB should not interfere with booting into XP.

---

### Post by Nixie Pixel on 2009-04-11
Thank you!  I can boot into XP and Ubuntu without any problems at all now.  That tutorial is awesome!

The only question I have about it is why did we remove the "setdefault" and "makeactive" lines?

Now, on the partition table - the Vista drive is an SSD that has particular requirements.  I had to use diskpar to create a single partition aligned with a starting offset of 128 (sectors).  Don't ask me why the SSDs need this, as I'm not 100% sure, but that's how it has to be.  So that 60GB drive should have only one partition with a starting offset of 128 in sectors.  

If we can't restore that, then I might as well start from scratch.  And if you happen to know how I can use fdisk or another linux utility to create the partition with a starting offset of 128 sectors without having to boot into Windows to use diskpar, I would be in your debt.

Thanks again for all your help!

---

### Post by meierfra. on 2009-04-11
> why did we remove the "setdefault" and "makeactive" lines?
Both savedefault and makeactive are usually unnecessary: see this [post]("http://www.uluga.ubuntuforums.org/showthread.php?t=1119849#26") for an explanation. And "makeactive" applied to a logical partition actually produces "grub errror 12".



> And if you happen to know how I can use fdisk or another linux utility to create the partition with a starting offset of 128 sectors


I would use fdisk to create the partition and then gparted to format the partition

```
sudo fdisk -u /dev/sda
d
1
d
2
d
3
d
4
```

this deletes all your four partitions on /dev/sda

```
n
p
1   (number 1 not letter l)
128
enter (to accept the default)
w
```

This creates a primary partition starting at sector 128 and ending at the end of the hard drive.

Then just use gparted to format that partition anyway you would like.

---

### Post by Nixie Pixel on 2009-04-12
Thank you, this was very useful!

---

