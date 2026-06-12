---
title: "[SOLVED] Can't select XP"
date: 2008-12-26
forum: General Help
---

### Post by Hyper Tails on 2008-12-26
Hi I'm triple booting my pc with XP,Vista and intrepid
and I installed ubuntu last but going to put Kubuntu instead now
and I can select Vista but not XP

what's up with that?

help

---

### Post by eagle416 on 2008-12-26
does it give you an error message? if so, what's it say?

---

### Post by Hyper Tails on 2008-12-26
no it doesent but it's not listed

---

### Post by eagle416 on 2008-12-26
It sounds like you need to update grub. Would reinstalling grub help?

---

### Post by Hyper Tails on 2008-12-26
> Would reinstalling grub help? 

no

> It sounds like you need to update grub.

how do I do that?

---

### Post by Monotoko on 2008-12-26
There will be 2 boot screens, Vista has its own...., this is the setup i have

Power On
¬
Choice between Vista And Ubuntu
go to ubuntu or if i boot vistaL
¬
Choice between Vista and XP

Vista takes over XP's bootloader you see, but it doesnt use GRUB
You should install in this order
XP - Vista - Ubuntu

---

### Post by eagle416 on 2008-12-26
if Monotoko's comment doesn't help, check to see if WinXP is even on Grub's List.

go to /boot/grub/menu.1st

scroll down, and see if anything that says Windows XP is there.

---

### Post by Monotoko on 2008-12-26
It wont be, the Vista bootloader takes over XP's, it no longer boots independantly, you will just get "NDLSR missing press ctrl alt del to restart" or something if you try and boot straight from the XP partition, you need to access it through Vista

---

### Post by eagle416 on 2008-12-26
> **Monotoko said:**
> It wont be, the Vista bootloader takes over XP's, it no longer boots independantly, you will just get "NDLSR missing press ctrl alt del to restart" or something if you try and boot straight from the XP partition, you need to access it through Vista

Oooh... didn't know that.

---

### Post by Hyper Tails on 2008-12-26
I installed it from this order

Vista-XP-Ubuntu

---

### Post by Monotoko on 2008-12-26
Thats why then...you will have to just give me a moment, and il work out what happened to XP

---

### Post by Monotoko on 2008-12-26
Now that is interesting....if anything i would expect to lose Vista, my findings confirm the same (a simple google search)

Could you boot into XP before you installed Ubuntu?

EDIT: I found this: [http://www.ajuaonline.com/2008/05/29/edit-windows-vista-bootloader-with-easybcd/](http://www.ajuaonline.com/2008/05/29/edit-windows-vista-bootloader-with-easybcd/)
you appear to need to use EasyBCD to get XP into your bootloader, dont ask me how as i havent duel-booted windows since the days of XP and 98, someone else may be able to help you.

If it becomes too much of a problem with no help, you may need to reinstall in the following order:
XP-Vista-(Restore Ubuntu GRUB loader...no need to delete)

---

### Post by obsrv on 2008-12-26
When GRUB loads press c I think to enter command promt the write root (hd and press TAB to see available disk, then enter number of the disc that winxp is on, then tab again and find partition of winxp. it should look like root (hd1,6) or smth. press enter, then write savedefault and enter then etner makedefault and then chainload. If it works, then add all these lines to menu.lst in /boot/grub/menu.lst

and one question. using standart 0,97 grub or GRUB2?

---

### Post by Monotoko on 2008-12-26
That wont work, XP will not boot independantly after Vista is installed, it must be done using the Vista bootloader, you will just get an error if you try.

---

### Post by obsrv on 2008-12-26
Oh sorry then, then you need this:

[http://www.pronetworks.org/forum/viewtopic.php?t=88231](http://www.pronetworks.org/forum/viewtopic.php?t=88231)

:popcorn:

---

### Post by Monotoko on 2008-12-26
[http://www.uluga.ubuntuforums.org/showthread.php?t=1010875](http://www.uluga.ubuntuforums.org/showthread.php?t=1010875)

Exhausting all the avenues before we suggest reinstall, reinstalling 3 OS's is not a simple task

---

### Post by Hyper Tails on 2008-12-26
Hi 
sorry if this sounds wrong
 but i selected vista and it brought me into XP

---

### Post by caljohnsmith on 2008-12-27
> **Hyper Tails said:**
> Hi 
sorry if this sounds wrong
 but i selected vista and it brought me into XP
Actually that sounds right since you installed XP after Vista, but in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by Hyper Tails on 2008-12-27
is this correct?```

============================= Boot Info Summary: ==============================

 => /dev/sdb has no valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6104a97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154143674    77071806    7  HPFS/NTFS
/dev/sda2       154143675   488375999   167116162+   f  W95 Ext'd (LBA)
/dev/sda5       316480563   488375999    85947718+   7  HPFS/NTFS
/dev/sda6       154143801   309781394    77818797   83  Linux
/dev/sda7       309781458   316480499     3349521   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 5 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

Warning: partition 5 does not start at a cylinder boundary
/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="82824E99824E9219" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda5: UUID="08CC807ACC806432" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda6: UUID="7e1b6bc9-af45-4b2c-82f0-849988862526" TYPE="ext3" 
/dev/sda7: UUID="55259b09-e8c7-4981-86d6-5ba938311d65" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================== sda1/Boot: ==================================

total 772
drwxrwxrwx 1 root root   4096 2008-12-27 01:53 .
drwxrwxrwx 1 root root   8192 2008-12-26 14:17 ..
-rwxrwxrwx 1 root root  28672 2008-12-27 01:54 BCD
-rwxrwxrwx 2 root root  24576 2008-12-26 22:19 BCD.Backup.0001
-rwxrwxrwx 1 root root   1024 2008-12-27 01:53 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-26 18:49 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-26 18:49 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-26 18:49 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-26 18:49 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-26 18:49 da-DK
drwxrwxrwx 1 root root      0 2008-12-26 18:49 de-DE
drwxrwxrwx 1 root root      0 2008-12-26 18:49 el-GR
drwxrwxrwx 1 root root      0 2008-12-26 18:49 en-US
drwxrwxrwx 1 root root      0 2008-12-26 18:49 es-ES
drwxrwxrwx 1 root root      0 2008-12-26 18:49 fi-FI
drwxrwxrwx 1 root root      0 2008-12-26 18:49 Fonts
drwxrwxrwx 1 root root      0 2008-12-26 18:49 fr-FR
drwxrwxrwx 1 root root      0 2008-12-26 18:49 hu-HU
drwxrwxrwx 1 root root      0 2008-12-26 18:49 it-IT
drwxrwxrwx 1 root root      0 2008-12-26 18:49 ja-JP
drwxrwxrwx 1 root root      0 2008-12-26 18:49 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 06:21 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-26 18:49 nb-NO
drwxrwxrwx 1 root root      0 2008-12-26 18:49 nl-NL
drwxrwxrwx 1 root root      0 2008-12-26 18:49 pl-PL
drwxrwxrwx 1 root root      0 2008-12-26 18:49 pt-BR
drwxrwxrwx 1 root root      0 2008-12-26 18:49 pt-PT
-rwxrwxrwx 1 root root 262144 2008-12-27 01:53 Recovery.bcd
-rwxrwxrwx 2 root root   1024 2008-12-27 01:53 Recovery.bcd.LOG
drwxrwxrwx 1 root root      0 2008-12-26 18:49 ru-RU
drwxrwxrwx 1 root root      0 2008-12-26 18:49 sv-SE
drwxrwxrwx 1 root root      0 2008-12-26 18:49 tr-TR
drwxrwxrwx 1 root root      0 2008-12-26 18:49 zh-CN
drwxrwxrwx 1 root root      0 2008-12-26 18:49 zh-HK
drwxrwxrwx 1 root root      0 2008-12-26 18:49 zh-TW

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
# kopt=root=UUID=7e1b6bc9-af45-4b2c-82f0-849988862526 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7e1b6bc9-af45-4b2c-82f0-849988862526

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
uuid		7e1b6bc9-af45-4b2c-82f0-849988862526
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7e1b6bc9-af45-4b2c-82f0-849988862526 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7e1b6bc9-af45-4b2c-82f0-849988862526
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7e1b6bc9-af45-4b2c-82f0-849988862526 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7e1b6bc9-af45-4b2c-82f0-849988862526
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
UUID=7e1b6bc9-af45-4b2c-82f0-849988862526 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=55259b09-e8c7-4981-86d6-5ba938311d65 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 12820
drwxr-xr-x  3 root root    4096 2008-12-26 14:07 .
drwxr-xr-x 20 root root    4096 2008-12-26 14:07 ..
-rw-r--r--  1 root root  503560 2008-10-24 05:25 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 05:25 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-26 14:07 grub
-rw-r--r--  1 root root 8655177 2008-12-26 14:07 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 17:41 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 05:25 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 05:27 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 05:25 vmlinuz-2.6.27-7-generic

=============================== sda6/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2008-12-26 14:07 .
drwxr-xr-x 3 root root   4096 2008-12-26 14:07 ..
-rw-r--r-- 1 root root    197 2008-12-26 14:07 default
-rw-r--r-- 1 root root     15 2008-12-26 14:07 device.map
-rw-r--r-- 1 root root   8108 2008-12-26 14:07 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-26 14:07 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 14:07 installed-version
-rw-r--r-- 1 root root   8712 2008-12-26 14:07 jfs_stage1_5
-rw-r--r-- 1 root root   4619 2008-12-26 14:07 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-26 14:07 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-26 14:07 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-26 14:07 stage1
-rw-r--r-- 1 root root 121460 2008-12-26 14:07 stage2
-rw-r--r-- 1 root root   9556 2008-12-26 14:07 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

```

---

### Post by caljohnsmith on 2008-12-27
OK, as I suspected, your Vista partition actually has an XP boot sector since you installed XP after Vista. To fix that problem, how about booting your Vista Install CD, go to the command line, and run:
```
bootrec /fixboot
```
Then reboot, and when you select "Windows Vista/Longhorn (loader)" from your Grub menu, you should boot into Vista this time (assuming Vista doesn't have any other issues). Also, would you like to be able to boot XP and Vista separately from the Grub menu, or do you want to use Vista's boot loader to boot Vista and XP?

---

### Post by Hyper Tails on 2008-12-27
Okay I did that now and now i can't select XP
anymore (this time i'm right for sure)

---

### Post by caljohnsmith on 2008-12-27
> **Hyper Tails said:**
> Okay I did that now and now i can't select XP
anymore (this time i'm right for sure)
Yes, that is as expected, but can you boot Vista now? Or what happens when you select Vista from the Grub menu?

---

### Post by Hyper Tails on 2008-12-27
it boots straight into Vista

---

### Post by caljohnsmith on 2008-12-27
OK, so to boot XP, you can add it to your Vista boot menu by using [EasyBCD]("http://neosmart.net/dl.php?id=1"). Let me know how that goes.

---

### Post by Hyper Tails on 2008-12-27
Thanks so much!!!

now I got it fixed now

I'll do this on my laptop later on and asked for help on it if i run into any problems

---

