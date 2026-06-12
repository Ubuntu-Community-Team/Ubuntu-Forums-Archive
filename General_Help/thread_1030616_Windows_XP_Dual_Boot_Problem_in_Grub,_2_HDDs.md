---
title: "Windows XP Dual Boot Problem in Grub, 2 HDDs"
date: 2009-01-04
forum: General Help
---

### Post by sillyusernamerulesinplace on 2009-01-04
I have 2 HDDs, one is smaller, a single partition, and hooked up through IDE.  The other is larger, with many partitions and hooked up through serial ATA.

I have Ubuntu 8.10 installed on the SATA drive, on its own partition (5).

I would like to dual boot, but cannot get the windows drive to work correctly through Grub.

Through my bios, I can set either HDD as the primary boot device.  If I boot to the IDE drive, it has the NT Bootloader set up, and windows boots perfectly normal, fully working.  If I boot to the SATA drive, grub loads up, but the windows entry does not work.  

The windows entry is as follows:
```
title		Microsoft Windows XP Professional
root	(hd0,0)
savedefault
makeactive
chainloader	+1
```

When I select this option, it says that there is no such partition.  If I do the Ubuntu line, it tells me its loading from (hd0,5) so I tried to change the windows line to "root (hd1,0)".

With that change, Windows then starts to boot, but gives an error about not finding hal.dll and halts the boot.

This is odd, as if I go back and set the IDE drive as the first boot device, windows boot loader comes up works fine, and windows runs with no problem again.

Please help, Im not sure why I can boot into grub/Ubuntu just fine, and to windows just fine, but cannot chose which one without changing the bios setting each time.

I would be fine to write over the NT Bootloader on the IDE drive as well if that would fix the problem, so long as I could boot into either using Grub.  If I can get it to work all using the SATA drive as the pointer, that would be even better, so when my parents use the computer I can set the bios to just go to windows as to not confuse them.

Thanks for anyones help.

---

### Post by caljohnsmith on 2009-01-04
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by sillyusernamerulesinplace on 2009-01-04
Thank you for the reply, it seems like I got it working using:

```
title Windows 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

For the windows entry.  If I had to guess, I think the MBR of the second disk has the NT Boot Loader on it as well, and previously, the error was when that boot loader was trying to run, not the one on the actual install drive.

Thank you for the response though Calijohnsmith, I will go ahead and post that information in case it can help someone else in the future.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63, but according to the info from fdisk, 
                       sdb5 starts at sector 1071 .
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 15.3 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f261f25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29977289    14988613+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77d703d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1008    81920159    40959576    f  W95 Ext'd (LBA)
/dev/sdb2   *    81920160   488394143   203236992    7  HPFS/NTFS
/dev/sdb5            1071    43503695    21751312+   7  HPFS/NTFS
/dev/sdb6        43504335    80224703    18360184+  83  Linux
/dev/sdb7        80224767    81920159      847696+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F278594678590B2D" TYPE="ntfs" 
/dev/sdb2: UUID="98F43FBBF43F9B08" LABEL="Stuff" TYPE="ntfs" 
/dev/sdb5: UUID="7C585D3A585CF47C" TYPE="ntfs" 
/dev/sdb6: UUID="798c164e-8191-4284-9e6d-d200db24afff" TYPE="ext3" 
/dev/sdb7: UUID="696f5b01-5ba1-4777-addb-126d3516f940" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/geoff/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=geoff)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect




================================ sdb2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Ultimate" /noexecute=optin /fastdetect


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
# kopt=root=UUID=798c164e-8191-4284-9e6d-d200db24afff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=798c164e-8191-4284-9e6d-d200db24afff

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		798c164e-8191-4284-9e6d-d200db24afff
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=798c164e-8191-4284-9e6d-d200db24afff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		798c164e-8191-4284-9e6d-d200db24afff
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=798c164e-8191-4284-9e6d-d200db24afff ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		798c164e-8191-4284-9e6d-d200db24afff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=798c164e-8191-4284-9e6d-d200db24afff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		798c164e-8191-4284-9e6d-d200db24afff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=798c164e-8191-4284-9e6d-d200db24afff ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		798c164e-8191-4284-9e6d-d200db24afff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1




=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=798c164e-8191-4284-9e6d-d200db24afff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=696f5b01-5ba1-4777-addb-126d3516f940 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb6/boot: ==================================

total 23804
drwxr-xr-x  3 root root    4096 2008-12-16 12:37 .
drwxr-xr-x 20 root root    4096 2008-12-09 21:34 ..
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-04 16:06 grub
-rw-r--r--  1 root root 8201826 2008-12-09 21:34 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8201887 2008-12-16 12:37 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sdb6/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-04 16:06 .
drwxr-xr-x 3 root root   4096 2008-12-16 12:37 ..
-rw-r--r-- 1 root root    197 2008-12-09 18:36 default
-rw-r--r-- 1 root root     30 2008-12-09 18:36 device.map
-rw-r--r-- 1 root root   8108 2008-12-09 18:36 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-09 18:36 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-09 18:36 installed-version
-rw-r--r-- 1 root root   8712 2008-12-09 18:36 jfs_stage1_5
-rw-r--r-- 1 root root   5264 2009-01-04 16:06 menu.lst
-rw-r--r-- 1 root root   5177 2009-01-04 16:04 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-09 18:36 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-09 18:36 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-09 18:36 stage1
-rw-r--r-- 1 root root 121460 2008-12-09 18:36 stage2
-rw-r--r-- 1 root root   9556 2008-12-09 18:36 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
umount: /tmp/BootInfo/sdb2: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

Looking at this, it also looks like my old install of Vista my have been screwing it up. At any rate, Im pretty sure its all working now.  Thanks again for the reply and help, your responses on other threads in this forum helped me greatly.  I appreciate it.

---

### Post by caljohnsmith on 2009-01-04
I'm really glad to hear you figured it out for yourself, and thanks for posting the output of that script anyway as it will help meierfra (the author of the script) to continue to tweak and improve the script. Cheers and have fun with Windows and Ubuntu. :)

---

