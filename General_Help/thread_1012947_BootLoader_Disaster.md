---
title: "BootLoader Disaster"
date: 2008-12-16
forum: General Help
---

### Post by davydog187 on 2008-12-16
So the saga begins....

I installed Ubuntu about 3 months ago on a second partition on my laptop and have been using it ever since. My first partition has vista on it. However, the bootloader menus were bugging me because if I went from GRUB and selected vista, it would take me to the vista bootloader.

After talking to a friend, he gave me software for vista that could supposedly fix this problem....except instead of fixing the problem I ended up erasing my vista bootloader. When I would select vista from grub I would get the NTDLR not found error.

Afterwards, I looked up solutions online and came across what seemed like a good solution. It had me replace boot.ini and another file from Ubuntu, however I did not realize this tutorial was for XP not Vista and TADA!I now had a hal.dll error.

Yesterday I decided to get out my vista recovery CD and fix this problem once and for all. It worked, I was able to shut down my computer and it would load Windows normally...for about 12 hours. When I woke up this morning, I turned off my computer, turned it back on with my SUPERGRUB cd and booted Ubuntu. After surfing the Internet I decided to finish with my upgrades on Vista.

Who shows up again? HAL.DLL ERROR!


Someone please help me and end this terrible story. Its been driving me crazy for so long and I just don't know the right way to tackle it.


Any help would be greatly appreciated


Dave

---

### Post by caljohnsmith on 2008-12-16
In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info8.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info8.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post, or you can attach the file itself to your post. That will help clarify your setup and what your problem might be.

---

### Post by davydog187 on 2008-12-16
```

Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #3 for its boot files.

sda1:
    File system:  vfat
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present:  /boot.ini /bootmgr /BOOTMGR /ntldr /NTLDR /NTDETECT.COM /ntdetect.com /Boot /boot /BOOT

sda2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 14338048
    Operating System: Vista
    Boot files/directories present:  /bootmgr /Boot

sda3:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb21d0910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    14338047     7168000    c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2        14338048   224004095   104833024    7  HPFS/NTFS
/dev/sda3       224010360   312576704    44283172+  83  Linux
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 14336000, Id= c, bootable
/dev/sda2 : start= 14338048, size=209666048, Id= 7
/dev/sda3 : start=224010360, size= 88566345, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


sda1/Boot

total 3464
drwxr-xr-x 3 root root    4096 2007-04-25 07:41 .
drwxr-xr-x 5 root root    4096 1969-12-31 19:00 ..
-rwxr-xr-x 1 root root   16384 2008-12-15 16:13 bcd
-rwxr-xr-x 1 root root  262144 2008-12-02 20:26 BCD.Backup.0001
-rwxr-xr-x 1 root root   13312 2008-12-15 16:13 bcd.log
-rwxr-xr-x 1 root root 3170304 2006-09-18 14:45 boot.sdi
-rwxr-xr-x 1 root root   65536 2008-12-02 20:29 BootStat.dat
-rwxr-xr-x 1 root root    2048 2006-09-18 14:27 etfsboot.com
drwxr-xr-x 2 root root    4096 2007-04-25 07:41 fonts

sda1/boot

total 3464
drwxr-xr-x 3 root root    4096 2007-04-25 07:41 .
drwxr-xr-x 5 root root    4096 1969-12-31 19:00 ..
-rwxr-xr-x 1 root root   16384 2008-12-15 16:13 bcd
-rwxr-xr-x 1 root root  262144 2008-12-02 20:26 BCD.Backup.0001
-rwxr-xr-x 1 root root   13312 2008-12-15 16:13 bcd.log
-rwxr-xr-x 1 root root 3170304 2006-09-18 14:45 boot.sdi
-rwxr-xr-x 1 root root   65536 2008-12-02 20:29 BootStat.dat
-rwxr-xr-x 1 root root    2048 2006-09-18 14:27 etfsboot.com
drwxr-xr-x 2 root root    4096 2007-04-25 07:41 fonts

sda1/BOOT

total 3464
drwxr-xr-x 3 root root    4096 2007-04-25 07:41 .
drwxr-xr-x 5 root root    4096 1969-12-31 19:00 ..
-rwxr-xr-x 1 root root   16384 2008-12-15 16:13 bcd
-rwxr-xr-x 1 root root  262144 2008-12-02 20:26 BCD.Backup.0001
-rwxr-xr-x 1 root root   13312 2008-12-15 16:13 bcd.log
-rwxr-xr-x 1 root root 3170304 2006-09-18 14:45 boot.sdi
-rwxr-xr-x 1 root root   65536 2008-12-02 20:29 BootStat.dat
-rwxr-xr-x 1 root root    2048 2006-09-18 14:27 etfsboot.com
drwxr-xr-x 2 root root    4096 2007-04-25 07:41 fonts

sda2/Boot

total 760
drwxrwxrwx 1 root root   4096 2007-04-24 13:05 .
drwxrwxrwx 1 root root  32768 2008-12-16 11:06 ..
-rwxrwxrwx 1 root root  24576 2008-12-16 11:25 BCD
-rwxrwxrwx 1 root root 262144 2008-12-16 11:25 BCD.LOG
-rwxrwxrwx 2 root root      0 2007-04-24 13:05 BCD.LOG1
-rwxrwxrwx 2 root root      0 2007-04-24 13:05 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2007-04-24 13:05 bootstat.dat
drwxrwxrwx 1 root root      0 2007-04-24 13:05 cs-CZ
drwxrwxrwx 1 root root      0 2007-04-24 13:05 da-DK
drwxrwxrwx 1 root root      0 2007-04-24 13:05 de-DE
drwxrwxrwx 1 root root      0 2007-04-24 13:05 el-GR
drwxrwxrwx 1 root root      0 2007-04-24 13:05 en-US
drwxrwxrwx 1 root root      0 2007-04-24 13:05 es-ES
drwxrwxrwx 1 root root      0 2007-04-24 13:05 fi-FI
drwxrwxrwx 1 root root      0 2007-04-24 13:05 Fonts
drwxrwxrwx 1 root root      0 2007-04-24 13:05 fr-FR
drwxrwxrwx 1 root root      0 2007-04-24 13:05 hu-HU
drwxrwxrwx 1 root root      0 2007-04-24 13:05 it-IT
drwxrwxrwx 1 root root      0 2007-04-24 13:05 ja-JP
drwxrwxrwx 1 root root      0 2007-04-24 13:05 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 04:51 memtest.exe
drwxrwxrwx 1 root root      0 2007-04-24 13:05 nb-NO
drwxrwxrwx 1 root root      0 2007-04-24 13:05 nl-NL
drwxrwxrwx 1 root root      0 2007-04-24 13:05 pl-PL
drwxrwxrwx 1 root root      0 2007-04-24 13:05 pt-BR
drwxrwxrwx 1 root root      0 2007-04-24 13:05 pt-PT
drwxrwxrwx 1 root root      0 2007-04-24 13:05 ru-RU
drwxrwxrwx 1 root root      0 2007-04-24 13:05 sv-SE
drwxrwxrwx 1 root root      0 2007-04-24 13:05 tr-TR
drwxrwxrwx 1 root root      0 2007-04-24 13:05 zh-CN
drwxrwxrwx 1 root root      0 2007-04-24 13:05 zh-HK
drwxrwxrwx 1 root root      0 2007-04-24 13:05 zh-TW

sda3/boot/grub/menu.lst

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
# kopt=root=UUID=42127856-1ad2-4f7d-83ed-b2ee6ab5b630 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=42127856-1ad2-4f7d-83ed-b2ee6ab5b630 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=42127856-1ad2-4f7d-83ed-b2ee6ab5b630 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista 0
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista 1
root		(hd0,1)
savedefault
makeactive
chainloader	+1


sda3/boot

total 44012
drwxr-xr-x  3 root root    4096 2008-11-29 11:23 .
drwxr-xr-x 22 root root    4096 2008-11-29 11:23 ..
-rw-r--r--  1 root root  420395 2008-10-21 21:49 abi-2.6.24-21-generic
-rw-r--r--  1 root root  503560 2008-11-04 15:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 18:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   74177 2008-10-21 21:49 config-2.6.24-21-generic
-rw-r--r--  1 root root   85316 2008-11-04 15:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 18:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-02 21:20 grub
-rw-r--r--  1 root root 7731983 2008-10-30 00:45 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7732260 2008-10-30 00:42 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8599718 2008-11-28 11:01 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8599668 2008-11-29 11:23 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1153201 2008-10-21 21:49 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1352144 2008-11-04 15:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 18:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 15:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 18:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1905688 2008-10-21 21:49 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2339552 2008-11-04 15:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 18:30 vmlinuz-2.6.27-9-generic

sda3/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-02 21:20 .
drwxr-xr-x 3 root root   4096 2008-11-29 11:23 ..
-rw-r--r-- 1 root root    197 2008-10-29 15:40 default
-rw-r--r-- 1 root root     15 2008-10-29 15:40 device.map
-rw-r--r-- 1 root root   8056 2008-10-29 15:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-29 15:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-29 15:40 installed-version
-rw-r--r-- 1 root root   8608 2008-10-29 15:40 jfs_stage1_5
-rw-r--r-- 1 root root   4524 2008-12-02 21:20 menu.lst
-rw-r--r-- 1 root root   5541 2008-11-29 11:23 menu.lst~
-rw-r--r-- 1 root root   7324 2008-10-29 15:40 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-29 15:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-29 15:40 stage1
-rw-r--r-- 1 root root 108356 2008-10-29 15:40 stage2
-rw-r--r-- 1 root root   9276 2008-10-29 15:40 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
```

It seems that my first partition, which I believe is the recovery partition, is set to XP. This probably goes back to when I changed the boot files by accident :/

---

### Post by caljohnsmith on 2008-12-16
OK, that's great, the output you posted clarifies things quite a bit. It looks like the reason you are getting a hal.dll error would be because you are using the first Vista entry in your Grub menu labeled "Windows Vista 0". Have you instead tried booting the "Windows Vista 1" entry from your Grub menu? How about giving that a shot and let me know exactly what happens.

---

### Post by davydog187 on 2008-12-16
Well, first of all the grub menu is not the first to open. In order for the grub menu to open I must use SUPER GRUB to load my linux partition. Second, when GRUB was the first to open, what you suggested did not work :/

---

### Post by caljohnsmith on 2008-12-16
> **davydog187 said:**
> Well, first of all the grub menu is not the first to open. In order for the grub menu to open I must use SUPER GRUB to load my linux partition. Second, when GRUB was the first to open, what you suggested did not work :/
According to the results you posted, you have Grub installed to the MBR of your HDD, so you should get Grub when you boot the drive. What happens when you boot the drive? Why do you have to use Super Grub to boot Ubuntu? And when you tried the second Vista entry and it "did not work", what exactly happened? Did it hang or did it give you an error?

---

### Post by davydog187 on 2008-12-16
You are correct, I made a mistake. I did not try rebooting after using SuperGrub to load linux. It seems that I inadvertently reinstalled GRUB and now I am able to load Windows correctly too by selecting the second Windows entry.

Thank you for all your help, I may more have wasted your time but I think I may have learned something.


Dave

---

