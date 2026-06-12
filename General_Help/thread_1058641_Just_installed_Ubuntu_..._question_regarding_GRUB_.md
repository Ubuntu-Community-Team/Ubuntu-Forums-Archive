---
title: "Just installed Ubuntu ... question regarding GRUB loader?"
date: 2009-02-03
forum: General Help
---

### Post by bigasif on 2009-02-03
Hey,
I previously had Vista installed on my Dell laptop, and was always planning on installing Ubuntu as a dual-boot config, and finally got around to it a few days ago. After a few bumps regarding getting my wireless to work (I lurked here throughout the entire process and finally got it working :D ) I love it!

Anyways, I installed updates and all that good stuff, and all was fine and dandy. Today I decided to install the Windows 7 Beta as a triple boot but run into a few problems. First off, let me explain my pre-ubuntu partition set up and my post-ubuntu partition set up.

Pre-Ubuntu
----------
~100GB C: (Vista)
~200GB D: (Data and Storage)

Post-Ubuntu
------------
~80GB C: (Vista)
~20GB for ubuntu
     -~3.7GB Swap...running 2gb ram, so i did 3.7 swap...basically just rounded whatever was there to get as close to 4gb as i could
     -~7.3GB Root
     -~12GB Home
~200GB D: (NTFS data/storage for Windows stuff...same as before)

So that was how I had it set-up. Then, to install Windows 7, I decided to try and shrink part of the 200GB storage parition for about 40GB's for Windows 7, as I wanted to keep my Vista partition large, as it was my primary O/S. So I used the Vista built-in partition manager to shrink the volume and I got the 40gb free space partition. I then proceeded to try and install Windows 7, and came up with an error during installation...turns out it was a CRC error, so I had to re-burn the dvd. When I tried to reboot, GRUB was encountering an Error, and thus I couldn't boot into any O/S at that time.

I googled the problem and noticed everybody mentioning a fixmbr command to reload the Vista MBR to overwrite the GRUB loader. SO did that, and booted into Vista fine. However, now I couldn't load Ubuntu. I tried booting from the LiveCD and things seemed hopeless as I followed this guide ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)), as well as a few more things off google but kept getting the Error: 15 File Not Found for grub. So I decided to go ahead and reinstall ubuntu from there. Now, I'm not too sure if ubuntu was gone before or if it was still there, but there wasn't any way for me to check. And when installing ubuntu, I noticed that the ~20GB was listed as free space in the ubuntu partition manager during installation, so I went ahead and used that space...sicne I'm pretty sure it's the same free space I had the first time around.

Now, Ubuntu is back, Vista is back, and GRUB is back. Sounds nice...but the problem is, no Windows 7 anymore :| ...so how would I get the Windows 7 back into Grub? Is it maybe because I had it installed on that logical partition instead of the main C: partition that this might be happening? I REALLY hope there's a workaround to get Windows 7, Vista, and Ubuntu on GRUB...or even an alternative to have all 3...some other loader would suffice too. 

Second question, I noticed that on the GRUB loader screen, there are quite a few options. 

Ubuntu 8.1, kernel 2.6.27-7-generic
Ubuntu 8.1, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.1, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Microsoft Windows XP Embedded

Do I need to have all these options there? Is there a way to get rid of some of them? I also don't have XP installed, and never have, so what's with the embedded XP? Also, the first time around installing Ubuntu...after updating, some additional options were added to the GRUB loader...I think it was the same as the first 2 in that list, except the kernel was 2.6.27-11-generic and the same thing with recovery mode. So which is needed, and what can I do to make it more organized?

Thanks in advance for any help at all!
All help is appreciated!

*[EDIT:] Just noticed something...if I choose Vista from GRUB, the windows bootloader screen shows up, giving me the option for Windows 7 or Vista. That does somewhat work...but I'd still prefer to be able to just choose everything straight from ONE loader if possible?*

Cheers,
BiGaSiF

---

### Post by Liviu-Theodor on 2009-02-03
Maybe you need and/or want to look at the [How to install Windows after Ubuntu]("http://ubuntuforums.org/showthread.php?t=993805") thread, and apply accordingly to your configuration. And yes, all OS's that you want to load directly should appear in the FRUB configuration file.

---

### Post by Powerman2442 on 2009-02-03
If you want to edit out options from the GRUB menu you can do it in Ubuntu. I recall there being a program in the repository that lets you do edit the GRUB menu.lst file without actually opening and editing the files contents. I can't remember the name of it as I never used it. But you can edit it manually this way.

First back it up...

```
sudo cp /boot/grub/menu.lst /home
```

You can use /home or wherever you know you can find it. Check and make sure it is indeed there and has conents.

Then you can type this to open up and edit the menu.lst file.

```
sudo gedit /boot/grub/menu.lst
```

I always edited the names. For exmaple: I changed Windows Longhorn (loader) to Windows Vista Home Premium. It was just something that looked more appealing to me. I also removed the memtest86+ as I found no use for it. Also, removed the kernel part of the names next to Ubuntu X.XX. Just because I only had one version of Ubuntu so I knew the kernel.

Good Luck,

P.S. I think it would be more trouble then it was worth to try adding Windows 7 to GRUB, honestly, although I could be wrong. Good luck...

---

### Post by caljohnsmith on 2009-02-03
I think it would help to first get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Windows 7 and Vista separately with Grub.

---

### Post by bigasif on 2009-02-03
Hey,
Thanks for the replies. The community here is great!

Anyways, I took a look at that How to Install Windows after Linux page, and didn't really find anything too helpful for my situation unfortunately.But I'll take a more in depth look at it a bit later.

As for editing the GRUB menu.lst file, I did that before when I first installed Ubuntu a few days back, just to get the default set to Vista instead of Ubuntu, by changing 'default 0' to 'default x', where 'x' was the value for Vista on the list. I do think that I will change the names though just to make things clearer.

Also, how did you remove the memtest loader from the list? Did you just comment out those lines? Is there any harm in doing so, or any reason why NOT to do that?

And as for the last post, here's the results for the boot_info_script. To get the command to work, I first had to get the boot_info_script.txt file, and found on google to get it as follows

'cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt'

So here are the contents of the RESULTS.txt file...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  
    Operating System:  Windows Vista
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sda8: _________________________________________________________________________

    File system:       swap

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   165727428    82815519+   7  HPFS/NTFS
/dev/sda3       165742605   625137344   229697370    f  W95 Ext'd (LBA)
/dev/sda5       209825028   539008314   164591643+   7  HPFS/NTFS
/dev/sda6       539009024   620924927    40957952    7  HPFS/NTFS
/dev/sda7       620928378   625137344     2104483+  dd  Unknown
/dev/sda8       165742731   172714814     3486042   82  Linux swap / Solaris
/dev/sda9       172714878   186386129     6835626   83  Linux
/dev/sda10      186386193   209824964    11719386   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 2 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0C1A" TYPE="vfat" 
/dev/sda2: UUID="50F61D91F61D7904" TYPE="ntfs" 
/dev/sda5: UUID="A63C5DBB3C5D86E9" TYPE="ntfs" 
/dev/sda6: UUID="2A6C24FF6C24C781" TYPE="ntfs" 
/dev/sda7: LABEL="MEDIADIRECT" UUID="07D8-0C1A" TYPE="vfat" 
/dev/sda8: UUID="952c4ed2-aab6-4dd5-b1b0-4c56570e352d" TYPE="swap" 
/dev/sda9: UUID="bd84a74c-6c94-494a-b0f3-85ebb859ac5f" TYPE="ext3" 
/dev/sda10: UUID="8da2fc14-9aeb-432e-8af9-70896a476680" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda9 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda10 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/asif/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=asif)

================================== sda2/Boot: ==================================

total 620
drwxrwxrwx 1 root root   4096 2009-02-03 03:15 .
drwxrwxrwx 1 root root  24576 2009-02-03 03:15 ..
-rwxrwxrwx 1 root root  32768 2009-02-03 01:07 BCD
-rwxrwxrwx 1 root root  29696 2009-02-03 00:42 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-27 01:36 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-27 01:36 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-02-03 03:15 bootstat.dat
drwxrwxrwx 1 root root      0 2009-02-03 03:15 cs-CZ
drwxrwxrwx 1 root root      0 2009-02-03 03:15 da-DK
drwxrwxrwx 1 root root      0 2009-02-03 03:15 de-DE
drwxrwxrwx 1 root root      0 2009-02-03 03:15 el-GR
drwxrwxrwx 1 root root      0 2009-02-03 03:15 en-US
drwxrwxrwx 1 root root      0 2009-02-03 03:15 es-ES
drwxrwxrwx 1 root root      0 2009-02-03 03:15 fi-FI
drwxrwxrwx 1 root root      0 2009-02-03 03:15 Fonts
drwxrwxrwx 1 root root      0 2009-02-03 03:15 fr-FR
drwxrwxrwx 1 root root      0 2009-02-03 03:15 hu-HU
drwxrwxrwx 1 root root      0 2009-02-03 03:15 it-IT
drwxrwxrwx 1 root root      0 2009-02-03 03:15 ja-JP
drwxrwxrwx 1 root root      0 2009-02-03 03:15 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 02:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-02-03 03:15 nb-NO
drwxrwxrwx 1 root root      0 2009-02-03 03:15 nl-NL
drwxrwxrwx 1 root root      0 2009-02-03 03:15 pl-PL
drwxrwxrwx 1 root root      0 2009-02-03 03:15 pt-BR
drwxrwxrwx 1 root root      0 2009-02-03 03:15 pt-PT
drwxrwxrwx 1 root root      0 2009-02-03 03:15 ru-RU
drwxrwxrwx 1 root root      0 2009-02-03 03:15 sv-SE
drwxrwxrwx 1 root root      0 2009-02-03 03:15 tr-TR
drwxrwxrwx 1 root root      0 2009-02-03 03:15 zh-CN
drwxrwxrwx 1 root root      0 2009-02-03 03:15 zh-HK
drwxrwxrwx 1 root root      0 2009-02-03 03:15 zh-TW

================================ sda7/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


=========================== sda9/boot/grub/menu.lst: ===========================

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
default		6

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
# kopt=root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bd84a74c-6c94-494a-b0f3-85ebb859ac5f

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
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda7
title		Microsoft Windows XP Embedded
root		(hd0,6)
savedefault
makeactive
chainloader	+1


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=8da2fc14-9aeb-432e-8af9-70896a476680 /home           ext3    relatime        0       2
# /dev/sda8
UUID=952c4ed2-aab6-4dd5-b1b0-4c56570e352d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda9/boot: ==================================

total 23820
drwxr-xr-x  3 root root    4096 2009-02-03 03:55 .
drwxr-xr-x 20 root root    4096 2009-02-03 03:53 ..
-rw-r--r--  1 root root  508385 2009-01-29 16:11 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91358 2009-01-29 16:11 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-02-03 10:25 grub
-rw-r--r--  1 root root 8205304 2009-02-03 03:55 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8201366 2009-02-03 03:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1031799 2009-01-29 16:11 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1074 2009-01-29 16:12 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2248912 2009-01-29 16:11 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic

=============================== sda9/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-02-03 10:25 .
drwxr-xr-x 3 root root   4096 2009-02-03 03:55 ..
-rw-r--r-- 1 root root    197 2009-02-02 20:51 default
-rw-r--r-- 1 root root     15 2009-02-02 20:51 device.map
-rw-r--r-- 1 root root   8108 2009-02-02 20:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-02-02 20:51 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-02-02 20:51 installed-version
-rw-r--r-- 1 root root   8712 2009-02-02 20:51 jfs_stage1_5
-rw-r--r-- 1 root root   5289 2009-02-03 10:25 menu.lst
-rw-r--r-- 1 root root   5289 2009-02-03 03:54 menu.lst~
-rw-r--r-- 1 root root   7352 2009-02-02 20:51 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-02-02 20:51 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-02-02 20:51 stage1
-rw-r--r-- 1 root root 121460 2009-02-02 20:51 stage2
-rw-r--r-- 1 root root   9556 2009-02-02 20:51 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  eb 50 90 44 65 6c 6c 20  38 2e 31 00 02 04 01 00  |.P.Dell 8.1.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 1a  0c d8 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 fa 33 c0 8e d0 bc  00 07 fb fc b9 80 00 8e  |...3............|
00000060  d8 be 00 7c b8 00 20 8e  c0 33 ff f3 66 a5 ea 73  |...|.. ..3..f..s|
00000070  00 00 20 0e 1f 66 0f b7  06 16 00 66 d1 e0 03 06  |.. ..f.....f....|
00000080  0e 00 66 03 06 1c 00 66  a3 46 00 a1 11 00 a3 4e  |..f....f.F.....N|
00000090  00 c1 e8 04 a2 40 00 b8  00 30 a3 44 00 8e c0 e8  |.....@...0.D....|
000000a0  f0 00 33 db b9 0b 00 be  ba 01 8b fb f3 a6 74 0f  |..3...........t.|
000000b0  83 c3 20 ff 0e 4e 00 75  eb be b0 01 e9 b4 00 26  |.. ..N.u.......&|
000000c0  8b 47 1a a3 50 00 a1 16  00 a3 4e 00 66 a1 1c 00  |.G..P.....N.f...|
000000d0  03 06 0e 00 66 a3 46 00  a1 4e 00 3d 40 00 76 03  |....f.F..N.=@.v.|
000000e0  b8 40 00 a2 40 00 e8 a9  00 66 0f b6 06 40 00 66  |.@..@....f...@.f|
000000f0  01 06 46 00 29 06 4e 00  74 09 c1 e0 05 01 06 44  |..F.).N.t......D|
00000100  00 eb d5 c7 06 44 00 70  00 a0 0d 00 a2 40 00 66  |.....D.p.....@.f|
00000110  0f b7 06 50 00 66 83 e8  02 66 0f b6 0e 0d 00 66  |...P.f...f.....f|
00000120  f7 e1 66 0f b7 0e 16 00  66 d1 e1 03 06 0e 00 66  |..f.....f......f|
00000130  03 0e 1c 00 66 03 c1 66  0f b7 0e 11 00 66 c1 e9  |....f..f.....f..|
00000140  04 66 03 c1 66 a3 46 00  e8 47 00 8b 36 50 00 b8  |.f..f.F..G..6P..|
00000150  00 30 d1 e6 73 03 05 00  10 8e c0 26 ad 3d f8 ff  |.0..s......&.=..|
00000160  73 16 a3 50 00 0f b6 06  0d 00 c1 e0 09 01 06 42  |s..P...........B|
00000170  00 eb 9c e8 0d 00 eb fe  8a 16 24 00 33 ed ea 00  |..........$.3...|
00000180  00 70 00 ac 3c 00 74 09  b4 0e bb 07 00 cd 10 eb  |.p..<.t.........|
00000190  f2 c3 b4 42 8a 16 24 00  be 3e 00 cd 13 72 01 c3  |...B..$..>...r..|
000001a0  be a5 01 eb ce 44 69 73  6b 20 65 72 72 6f 72 00  |.....Disk error.|
000001b0  4e 6f 20 4c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No Loader.DELLBI|
000001c0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 00 00  |O BIN...........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

If anyone has any ideas for me or any sort of help, that would be great. Also, you can now see which options appear on Grub for me, so if you can suggest which ones I can get rid of, that would be helpful, since I'm not too sure which are required, except for the Vista one, and just one of the Ubuntu's, but not sure which one. The extra kernel's showed up after installing updates.

Thanks again,
BiGaSiF

---

### Post by Powerman2442 on 2009-02-03
Memtest86+ basically testes your memory to see if it is working correctly. From my understanding it writes information to your memory then reads it back multiple times to try to determine if your memory is bad. Usually if you have problems with your system locking up or automatically rebooting for no reason you should run memest just to check and see if your memory is good. At that point you can determine if you memory if good or bad and that should help everyone on the forums lead you to a fix for your problem.

As for removeing the memtest86+ from the GRUB menu you. When I edited the menu.lst I edited out the whole memtest part. It looked something like this...

title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot

I just removed the entire memtest section from title to boot. Like I said back up the original menu.lst just in case.

---

### Post by caljohnsmith on 2009-02-03
In order to boot Windows 7 and Vista separately, I would recommend following [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832"). Also, it does appear that you have Windows XP installed on sda7. How about posting the output of:
```
sudo mount /dev/sda7 /mnt && ls -l /mnt
```
So we can see if it looks like XP really is there. Let me know how it goes with the tutorial, or if you run into problems.

---

### Post by bigasif on 2009-02-03
Hey,
Thanks for the quick replies again guys!

***Note: Italicized text was edited/added about 2 minutes after posting just to edit something and clear something up.***

For the removal process for memtest from the Grub loader, thanks for the details and info! I'll most likely get rid of it once I get this thing figured out.

As for updates to what has happened so far, here goes. So I followed the tutorial, all commands were completed successfully, but when I tried to load Windows 7 from the Grub page, *it simply said "Starting Up..." and stayed there. I also then tried booting from the XP part on the Grub screen, and got an error that said "Error 12: Invalid device requested   Press any key to continue..." which takes me back to Grub.* Seems like the only ones that actually work are the Windows Vista loader which gives me the option to boot Vista or Windows 7, and then the Ubuntu options.

I then went ahead and tried step 3, and once I hit rebuild BS, it instantly came to the next screen and says:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 6 L HPFS - NTFS          33551 193 51 38650 201 15   81915904

filesystem size           81915904 81915904
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               5119743 5119743
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.







[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]
```

So I'm guessing the 3rd step wasn't needed in my case and I'm just having some other kind of problem? Also, going about finding out exactly which partition the Windows 7 OS is loaded on, I simply checked that RESULTS.txt file and just looked for the partition that was ~40GB's, since that's how much I split it to for Windows 7. Is that a reasonable approach?

As for what shows up with that command to test for XP, here is the output...

```
total 764
-rwxr-xr-x  1 root root    222 2008-12-27 01:54 boot.ini
-rwxr-xr-x  1 root root 399196 2005-12-13 20:55 bootmgr
drwxr-xr-x  7 root root   4096 2008-12-27 01:54 Documents and Settings
-rwxr-xr-x  1 root root      0 2006-08-10 00:59 md3.txt
-rwxr-xr-x  1 root root  47564 2004-08-03 00:38 ntdetect.com
-rwxr-xr-x  1 root root 250048 2005-08-19 11:13 ntldr
drwxr-xr-x 10 root root   4096 2008-12-27 01:54 Program Files
-rwxr-xr-x  1 root root  57344 2005-10-30 17:46 rmbr.exe
-rwxr-xr-x  1 root root    282 2005-11-07 14:43 WERUNTIME.INI
drwxr-xr-x 23 root root   4096 2008-12-27 01:54 windows
```

Judging by the size of that partition from the RESULTS/txt file (~2ish GB's) I'm guessing that's one of Dell's stuff for my laptop, perhaps MediaDirect which controls the MediaDirect keys on the front of my laptop, and allows the laptop to launch the MediaDirect application without booting into an O/S.

Thanks again!
BiGaSiF

---

### Post by caljohnsmith on 2009-02-04
> **bigasif said:**
> 
I then went ahead and tried step 3, and once I hit rebuild BS, it instantly came to the next screen and says:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 6 L HPFS - NTFS          33551 193 51 38650 201 15   81915904

filesystem size           81915904 81915904
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               5119743 5119743
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
[COLOR="Blue"]Extrapolated boot sector and current boot sector are different.[/COLOR]


[  Dump  ]  [  List  ]  [ [COLOR="Blue"]Write[/COLOR]  ]  [  Quit  ]
```

So I'm guessing the 3rd step wasn't needed in my case and I'm just having some other kind of problem? 
Actually you do need to do the 3rd step, because as testdisk is showing you above, your boot sectors don't match. So you should select "Write" on that screen and that will rebuild your boot sector. 
> **bigasif said:**
> 
Also, going about finding out exactly which partition the Windows 7 OS is loaded on, I simply checked that RESULTS.txt file and just looked for the partition that was ~40GB's, since that's how much I split it to for Windows 7. Is that a reasonable approach?

Your 40 GB Windows 7 partition appears to be the sda6 partition, so is that the one you mean?
> **bigasif said:**
> 
As for what shows up with that command to test for XP, here is the output...

```
total 764
-rwxr-xr-x  1 root root    222 2008-12-27 01:54 boot.ini
-rwxr-xr-x  1 root root 399196 2005-12-13 20:55 bootmgr
drwxr-xr-x  7 root root   4096 2008-12-27 01:54 Documents and Settings
-rwxr-xr-x  1 root root      0 2006-08-10 00:59 md3.txt
-rwxr-xr-x  1 root root  47564 2004-08-03 00:38 ntdetect.com
-rwxr-xr-x  1 root root 250048 2005-08-19 11:13 ntldr
drwxr-xr-x 10 root root   4096 2008-12-27 01:54 Program Files
-rwxr-xr-x  1 root root  57344 2005-10-30 17:46 rmbr.exe
-rwxr-xr-x  1 root root    282 2005-11-07 14:43 WERUNTIME.INI
drwxr-xr-x 23 root root   4096 2008-12-27 01:54 windows
```

Judging by the size of that partition from the RESULTS/txt file (~2ish GB's) I'm guessing that's one of Dell's stuff for my laptop, perhaps MediaDirect which controls the MediaDirect keys on the front of my laptop, and allows the laptop to launch the MediaDirect application without booting into an O/S.

Thanks again!
BiGaSiF
After looking over the output of the script more carefully, I'm sure you must be right about sda7 being your MediaDirect partition. Therefore I would remove the Windows XP entry from your Grub's menu.lst since you don't need to boot the MediaDirect partition, true? Because if you do need to boot sda7, you should remove the "makeactive" line in the Windows XP Grub entry. Anyway, let me know how it goes.

---

### Post by bigasif on 2009-02-04
Thanks for the reply!

> **caljohnsmith said:**
> Actually you do need to do the 3rd step, because as testdisk is showing you above, your boot sectors don't match. So you should select "Write" on that screen and that will rebuild your boot sector. 

I just went ahead and did that. After that step, and rebooting to try and boot from Windows 7 on Grub, I got an error from Windows Boot Manager. 

```
Windows failed to start. A recent hardware or software change might be the cause. To Fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \Windows\system32/winload.exe

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.
```

What now??? :S
I seem to be able to still boot into Vista/Windows 7 fine if I choose the Windows Vista loader, and then choose either Windows 7 or Vista from the Windows Boot Loader...but can't seem to select Windows 7 from the Grub list.

> **caljohnsmith said:**
> 
Your 40 GB Windows 7 partition appears to be the sda6 partition, so is that the one you mean?
Yeap, that's the one. sda6 seems to be the Windows 7 partition, based on size. Any way I can find out for sure though? Although...I don't see there being any other possibility since it's the only one that's even CLOSE to 40GB.

> **caljohnsmith said:**
> 
After looking over the output of the script more carefully, I'm sure you must be right about sda7 being your MediaDirect partition. Therefore I would remove the Windows XP entry from your Grub's menu.lst since you don't need to boot the MediaDirect partition, true? Because if you do need to boot sda7, you should remove the "makeactive" line in the Windows XP Grub entry. Anyway, let me know how it goes.
Awesome. Yeah, I'll go ahead and remove that from the menu.lst file. What about the rest of the stuff on Grub? There are 2 versions of ubuntu with different kernels, and a regular and recovery mode for each. And then the memtest...which I will probably get rid of either way. Thanks again!

BiGaSiF

---

### Post by caljohnsmith on 2009-02-04
So did you run *all* the bcdedit commands that the tutorial gave in step 2? Did they all complete successfully? I think it's important to do all the bcdedit commands since you are using Windows 7. If you did them, what entry are you using in your Grub menu to boot Windows 7? Does it look like:
```
title Windows 7
rootnoverify (hd0,5)
chainloader +1
```
But it sounds like you probably have the correct Windows 7 entry if you are getting that Windows error. Also, how about posting:
```
sudo mount /dev/sda6 /mnt && ls -l /mnt /mnt/[Bb][Oo][Oo][Tt]
```

---

### Post by meierfra. on 2009-02-04
> \Windows\system32[COLOR="Red"]/[/COLOR]winload.exe

Seems you made a typo when  following the tutorial. It needs to be "\Windows\system32\winload.exe".  To fix it, boot into Window 7. Click on "Start". Type "cmd" and press  "Ctrl+Shift+Enter". This will open a console.
Type:


```

bcdedit /store C:\boot\bcd /set {default} path \Windows\system32\winload.exe

```

(Here you need to replace "C:" by the drive letter of your Windows 7 partition. (Go to "My Computer" to determine the drive letter)


If this did not solve your problem, boot into Window 7 again. Open a console as above. Type


```
bcdedit /store C:\boot\bcd >>C:\info.txt

bcdedit /store D:\boot\bcd >>C:\info.txt
```


Here replace "C:" by the drive letter of your Windows 7 partition and  "D:" by the drive letter of your Vista partition  Then post the content of the file "info.txt" in the root folder of your Windows 7 partition.

---

### Post by bigasif on 2009-02-04
> **meierfra. said:**
> Seems you made a typo when  following the tutorial. It needs to be "\Windows\system32\winload.exe".  To fix it, boot into Window 7. Click on "Start". Type "cmd" and press  "Ctrl+Shift+Enter". This will open a console.
Type:


```

bcdedit /store C:\boot\bcd /set {default} path \Windows\system32\winload.exe

```

(Here you need to replace "C:" by the drive letter of your Windows 7 partition. (Go to "My Computer" to determine the drive letter)


If this did not solve your problem, boot into Window 7 again. Open a console as above. Type


```
bcdedit /store C:\boot\bcd >>C:\info.txt

bcdedit /store D:\boot\bcd >>C:\info.txt
```


Here replace "C:" by the drive letter of your Windows 7 partition and  "D:" by the drive letter of your Vista partition  Then post the content of the file "info.txt" in the root folder of your Windows 7 partition.

:D :D :D It worked! Thank you so much! It was that typo I guess I must've made during the tutorial. I thought something seemed fishy about that when that error came up. Ah well, that's solved now. Thanks to all of you for helping me out with that! Now I'm able to successfully load Ubuntu, Vista, and Windows 7 from my Grub loader :D

But yeah, I had to run the command prompt as administrator since when I tried running the command the first time, it told me access was denied. So I right-clicked on it, and ran it as administrator, and presto! Also, when I was in Windows 7, the only drives I could see were C: (Windows 7) D: (Data partition available on both Vista and Windows 7) and E: (DVD-Drive) ...seemed like I couldn't access the Vista O/S partition, so the second command to copy the boot info from Vista to the Windows 7 root folder wouldn't have worked, correct? But yeah, either way it was solved before needing to execute those commands :)

Also, caljohnsmith, yes, that's what my entry looks like in Grub. Also, all the commands executed successfully when I followed the tutorial, but yeah, seems like it was a typo. And also, don't know if it's helpful anymore, but here's the output to that command...

```
laptop-ubuntu:~$ sudo mount /dev/sda6 /mnt && ls -l /mnt /mnt/[Bb][Oo][Oo][Tt]
/mnt:
total 3959801
-rwxrwxrwx 1 root root         24 2008-10-15 12:11 autoexec.bat
drwxrwxrwx 1 root root       4096 2009-02-04 23:15 BOOT
-rwxrwxrwx 1 root root     438840 2006-11-02 15:00 BOOTMGR
-rwxrwxrwx 1 root root         10 2008-10-15 12:11 config.sys
drwxrwxrwx 1 root root          0 2008-12-12 18:58 Documents and Settings
-rwxrwxrwx 1 root root 1603092480 2009-02-04 23:17 hiberfil.sys
-rwxrwxrwx 1 root root 2451263488 2009-02-04 23:17 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-13 02:57 PerfLogs
drwxrwxrwx 1 root root       4096 2008-12-12 18:58 ProgramData
drwxrwxrwx 1 root root       4096 2009-02-03 01:03 Program Files
drwxrwxrwx 1 root root          0 2009-02-03 00:30 Recovery
drwxrwxrwx 1 root root          0 2009-02-03 00:30 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2009-02-03 00:42 System Volume Information
drwxrwxrwx 1 root root       4096 2009-02-03 00:30 Users
drwxrwxrwx 1 root root      16384 2009-02-03 01:02 Windows

/mnt/BOOT:
total 4084
-rwxrwxrwx 1 root root  262144 2009-02-04 23:15 BCD
-rwxrwxrwx 1 root root  262144 2009-02-04 23:15 bcd.LOG
-rwxrwxrwx 2 root root       0 2009-02-04 23:15 bcd.LOG1
-rwxrwxrwx 2 root root       0 2009-02-04 23:15 bcd.LOG2
-rwxrwxrwx 1 root root    1024 2006-11-02 15:00 BOOTFIX.BIN
-rwxrwxrwx 1 root root 3170304 2006-11-02 15:00 BOOT.SDI
-rwxrwxrwx 1 root root   87552 2006-11-02 15:00 BOOTSECT.EXE
-rwxrwxrwx 1 root root    2048 2006-11-02 15:00 ETFSBOOT.COM
-rwxrwxrwx 1 root root  386664 2006-11-02 15:00 MEMTEST.EXE
```

...Now 2 more quick questions if any of you guys have any ideas...since you seem to be EXTREMELY helpful so far...

First, would you guys happen to know how I can get rid of the Windows Boot Manager so that I don't have to go to that screen once I choose Vista, because then it gives me the choice for Vista and Windows 7, but since I already have Windows 7 in Grub, I don't see the point in having to go to that screen as well when I want to boot Vista.

Second, would you guys suggest me getting rid of one of the kernel versions of ubuntu on Grub? Initially I only had these ones,

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
```

Once I installed updates, these also got added above the previous 2...

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

```

Also, any point in keeping the recovery mode's there? Thanks again guys!

Seriously...this is by far the MOST HELPFUL online community I've been to. Responses are quick and always very helpful. AND I'm really getting attached to Ubuntu lol...I'm really thinking of trying to make it the default :)

Cheers,
BiGaSiF

---

### Post by meierfra. on 2009-02-05
> But yeah, I had to run the command prompt as administrator since when I tried running the command the first time, it told me access was denied.

Did you open the command prompt via "Start" "cmd" "Ctrl+Shift+Enter"?  Pressing "Ctrl+Shift+Enter" instead of just "enter"  should have opened the command prompt as administrator.


> ...seemed like I couldn't access the Vista O/S partition, so the second command to copy the boot info from Vista to the Windows 7 root folder wouldn't have worked, correct?

Correct. Usually Window 7 has no problems detecting Vista. No idea what the problem could be.


> How I can get rid of the Windows Boot Manager so that I don't have to go to that screen once I choose Vista,


Just a couple of days ago killergp123 posted a solution to this problem:

[QUOTE=killergp123]
found out what I had to do, just went into startup/recovery options in vista and made vista primary operating system and unticked show OS menu at startup
[/QUOTE]

> Second, would you guys suggest me getting rid of one of the kernel versions of ubuntu on Grub?

I recommend keeping both kernels. The second kernel might come in handy, if the first kernel fails to boot for what ever reason.  But I suggest to limit the number of kernels to two:

Open "menu.lst" via
```
gksudo gedit /boot/grub/menu.lst
```
look for

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

and change the last line to:

# howmany=2

If you do want to get rid of the second kernel, use "#howmany=1", save the file and then type "sudo  update-grub" in a terminal. That will delete the extra kernel.

Or you can just manually delete the following from menu.lst:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bd84a74c-6c94-494a-b0f3-85ebb859ac5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bd84a74c-6c94-494a-b0f3-85ebb859ac5f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

> 
Also, any point in keeping the recovery mode's there? 

Definitely, the recovery mode can be a live saver in certain situations.

---

