---
title: "I need a GRUB expert"
date: 2009-01-15
forum: General Help
---

### Post by Mr Pockets151 on 2009-01-15
I need help setting up a GRUB or just any bootloader that will work.

I have 4 primary partitions and I was using the Mandriva 2009 GRUB. Everything was working fine. I just finished installing WIN 7 and then I installed a 64-bit version of MDV. I chose to use the GRUB on the Windows MBR.

Every OS I have gets listed on the menu but only Windows and MDV work. My Ubuntu entry shoots me to my Ubunutu Grub then gives me an error 15. Where as before it worked fine.

Again...sopmeone that's an expert at this can you give me some pointers.

What info do you need to help get me in the right direction.....

---

### Post by Titan8990 on 2009-01-15
post your /boot/grub/menu.lst

report the output of:

blkid


And let me know which drive Ubuntu is on.

---

### Post by caljohnsmith on 2009-01-15
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Mr Pockets151 on 2009-01-15
thnx.  I will do this as soon as I get home.

---

### Post by Mr Pockets151 on 2009-01-15
my menu.lst```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd2,1)/boot/gfxmenu
default 3

title linux
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd.img

title linux-nonfb
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 
initrd (hd2,1)/boot/initrd.img

title failsafe
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 failsafe
initrd (hd2,1)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title windows1
root (hd2,0)
map (0x82) (0x80)
map (0x80) (0x82)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd2,3)
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd2,1)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.7-1mnb
kernel (hd2,1)/boot/vmlinuz-2.6.27.7-server-1mnb BOOT_IMAGE=server_2.6.27.7-1mnb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd-2.6.27.7-server-1mnb.img
```

blkid command doesn't work.

The boot script```

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  Geometry: 16 Heads and 63 sectors per Track. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 (Official) for x86_64 Kernel 2.6.27.7-server-1mnb on a Dual-processor x86_64 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc3: _________________________________________________________________________

    File system:       Extended Partition

sdc4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdc4 
                       and looks at sector 463445550 of the same hard drive 
                       for the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
16 heads, 63 sectors/track, 319120 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde0d3798

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321670943   160835440+   7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1c316cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   845774054   422886996    7  HPFS/NTFS
/dev/sdb2       845774055   976768064    65497005    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004c1e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   103956614    51978276    7  HPFS/NTFS
/dev/sdc2       103956615   228974444    62508915   83  Linux
/dev/sdc3       228974445   228990509        8032+   5  Extended
/dev/sdc4       228990510   488392064   129700777+  83  Linux
/dev/sdc5       228974508   228990509        8001   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C0C0E888C0E8864E" LABEL="DO NOT GO HERE!" TYPE="ntfs" 
/dev/sdb1: UUID="9AEB58DE7E2F7C89" LABEL="MUSIC, PICTURES AND FILES" TYPE="ntfs" 
/dev/sdb2: UUID="EA7C2C7B7C2C4523" LABEL="EXTRA STORAGE" TYPE="ntfs" 
/dev/sdc1: UUID="55CCAA7A68D8CCE6" TYPE="ntfs" 
/dev/sdc2: UUID="97d6db45-d810-4e7a-8ee1-78d35e421c69" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="28efa3da-a054-4b5d-98bc-f9777f2734b3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="a5a7dd73-a75c-4290-8889-d00db30d667f" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


================================== sda1/Boot: ==================================

total 596
drwxrwxrwx 1 root root   4096 2009-01-15 00:12 .
drwxrwxrwx 1 root root   8192 2009-01-15 21:25 ..
-rwxrwxrwx 1 root root  28672 2009-01-16 01:26 BCD
-rwxrwxrwx 1 root root  25600 2009-01-16 01:16 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-15 00:12 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-15 00:12 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-15 00:12 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-15 00:12 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-15 00:12 da-DK
drwxrwxrwx 1 root root      0 2009-01-15 00:12 de-DE
drwxrwxrwx 1 root root      0 2009-01-15 00:12 el-GR
drwxrwxrwx 1 root root      0 2009-01-15 00:12 en-US
drwxrwxrwx 1 root root      0 2009-01-15 00:12 es-ES
drwxrwxrwx 1 root root      0 2009-01-15 00:12 fi-FI
drwxrwxrwx 1 root root      0 2009-01-15 00:12 Fonts
drwxrwxrwx 1 root root      0 2009-01-15 00:12 fr-FR
drwxrwxrwx 1 root root      0 2009-01-15 00:12 hu-HU
drwxrwxrwx 1 root root      0 2009-01-15 00:12 it-IT
drwxrwxrwx 1 root root      0 2009-01-15 00:12 ja-JP
drwxrwxrwx 1 root root      0 2009-01-15 00:12 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 07:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-15 00:12 nb-NO
drwxrwxrwx 1 root root      0 2009-01-15 00:12 nl-NL
drwxrwxrwx 1 root root      0 2009-01-15 00:12 pl-PL
drwxrwxrwx 1 root root      0 2009-01-15 00:12 pt-BR
drwxrwxrwx 1 root root      0 2009-01-15 00:12 pt-PT
drwxrwxrwx 1 root root      0 2009-01-15 00:12 ru-RU
drwxrwxrwx 1 root root      0 2009-01-15 00:12 sv-SE
drwxrwxrwx 1 root root      0 2009-01-15 00:12 tr-TR
drwxrwxrwx 1 root root      0 2009-01-15 00:12 zh-CN
drwxrwxrwx 1 root root      0 2009-01-15 00:12 zh-HK
drwxrwxrwx 1 root root      0 2009-01-15 00:12 zh-TW

=========================== sdc2/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd2,1)/boot/gfxmenu
default 3

title linux
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd.img

title linux-nonfb
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 
initrd (hd2,1)/boot/initrd.img

title failsafe
kernel (hd2,1)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 failsafe
initrd (hd2,1)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title windows1
root (hd2,0)
map (0x82) (0x80)
map (0x80) (0x82)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd2,3)
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd2,1)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.7-1mnb
kernel (hd2,1)/boot/vmlinuz-2.6.27.7-server-1mnb BOOT_IMAGE=server_2.6.27.7-1mnb root=UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 splash=silent vga=788
initrd (hd2,1)/boot/initrd-2.6.27.7-server-1mnb.img

=============================== sdc2/etc/fstab: ===============================

# Entry for /dev/sdc2 :
UUID=97d6db45-d810-4e7a-8ee1-78d35e421c69 / ext3 relatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
/dev/fd0 /media/floppy auto umask=0,users,iocharset=utf8,noauto,exec,flush 0 0
# Entry for /dev/sda1 :
UUID=C0C0E888C0E8864E /mnt/win_c ntfs-3g defaults 0 0
# Entry for /dev/sdb1 :
UUID=9AEB58DE7E2F7C89 /mnt/win_c2 ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=55CCAA7A68D8CCE6 /mnt/win_c3 ntfs-3g defaults 0 0
# Entry for /dev/sdb2 :
UUID=EA7C2C7B7C2C4523 /mnt/win_d ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sdc5 :
UUID=a5a7dd73-a75c-4290-8889-d00db30d667f swap swap defaults 0 0

================================== sdc2/boot: ==================================

total 15536
drwxr-xr-x  3 root root    4096 2009-01-16 03:34 .
drwxr-xr-x 21 root adm     4096 2009-01-16 03:51 ..
-rw-r--r--  1 root root     440 2009-01-16 03:24 boot.backup.sda
lrwxrwxrwx  1 root root      27 2009-01-16 03:34 config -> config-2.6.27.7-server-1mnb
-rw-r--r--  1 root root   90547 2008-12-11 22:43 config-2.6.27.7-server-1mnb
-rw-r--r--  1 root root   90386 2008-10-02 10:10 config-2.6.27-server-0.rc8.2mnb
-rw-r--r--  1 root root  483840 2009-01-15 18:35 gfxmenu
drwxr-xr-x  2 root root    4096 2009-01-16 03:24 grub
-rw-------  1 root root 4020370 2009-01-15 18:53 initrd-2.6.27.7-server-1mnb.img
-rw-------  1 root root 4019581 2009-01-15 18:35 initrd-2.6.27-server-0.rc8.2mnb.img
lrwxrwxrwx  1 root root      31 2009-01-15 18:53 initrd.img -> initrd-2.6.27.7-server-1mnb.img
lrwxrwxrwx  1 root root      31 2009-01-15 18:53 initrd-server.img -> initrd-2.6.27.7-server-1mnb.img
lrwxrwxrwx  1 root root      35 2009-01-16 03:34 kernel.h -> /boot/kernel.h-2.6.27.7-server-1mnb
-rw-r--r--  1 root root    1493 2009-01-16 03:34 kernel.h-2.6.27.7-server-1mnb
lrwxrwxrwx  1 root root      31 2009-01-16 02:58 System.map -> System.map-2.6.27.7-server-1mnb
-rw-r--r--  1 root root 1153486 2008-12-11 22:43 System.map-2.6.27.7-server-1mnb
-rw-r--r--  1 root root 1153238 2008-10-02 10:10 System.map-2.6.27-server-0.rc8.2mnb
lrwxrwxrwx  1 root root      28 2009-01-15 18:53 vmlinuz -> vmlinuz-2.6.27.7-server-1mnb
-rw-r--r--  1 root root 2409504 2008-12-11 22:43 vmlinuz-2.6.27.7-server-1mnb
-rw-r--r--  1 root root 2405728 2008-10-02 10:10 vmlinuz-2.6.27-server-0.rc8.2mnb
lrwxrwxrwx  1 root root      28 2009-01-15 18:53 vmlinuz-server -> vmlinuz-2.6.27.7-server-1mnb

=============================== sdc2/boot/grub: ===============================

total 268
drwxr-xr-x 2 root root   4096 2009-01-16 03:24 .
drwxr-xr-x 3 root root   4096 2009-01-16 03:34 ..
-rw-rw-r-- 1 root root     60 2009-01-16 03:24 device.map
-rw-r--r-- 1 root root     60 2009-01-15 18:53 device.map.old
-rw-r--r-- 1 root root   8896 2009-01-16 03:24 e2fs_stage1_5
-rw-r--r-- 1 root root   8576 2009-01-16 03:24 fat_stage1_5
-rw-r--r-- 1 root root   7712 2009-01-16 03:24 ffs_stage1_5
-rwxr-xr-x 1 root root    115 2009-01-16 03:24 install.sh
-rwxr-xr-x 1 root root    115 2009-01-15 18:53 install.sh.old
-rw-r--r-- 1 root root   9216 2009-01-16 03:24 iso9660_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-16 03:24 jfs_stage1_5
-rw-rw-r-- 1 root root   1215 2009-01-16 03:24 menu.lst
-rw-r--r-- 1 root root    223 2008-08-06 18:31 menu.lst.example
-rw-r--r-- 1 root root   1215 2009-01-15 18:53 menu.lst.old
-rw-r--r-- 1 root root   7936 2009-01-16 03:24 minix_stage1_5
-rw-r--r-- 1 root root  10720 2009-01-16 03:24 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-16 03:24 stage1
-rw-r--r-- 1 root root 122186 2009-01-16 03:24 stage2
-rw-r--r-- 1 root root   8000 2009-01-16 03:24 ufs2_stage1_5
-rw-r--r-- 1 root root   7264 2009-01-16 03:24 vstafs_stage1_5
-rw-r--r-- 1 root root  10312 2009-01-16 03:24 xfs_stage1_5

=========================== sdc4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=28efa3da-a054-4b5d-98bc-f9777f2734b3

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
uuid		28efa3da-a054-4b5d-98bc-f9777f2734b3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		28efa3da-a054-4b5d-98bc-f9777f2734b3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		28efa3da-a054-4b5d-98bc-f9777f2734b3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		28efa3da-a054-4b5d-98bc-f9777f2734b3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		28efa3da-a054-4b5d-98bc-f9777f2734b3
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
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5ee6d014-888d-482d-be11-ca41735e1491 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		linux (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent vga=788 
initrd		(hd2,1)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		linux-nonfb (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent 
initrd		(hd2,1)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		failsafe (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da failsafe 
initrd		(hd2,1)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		2.6.27-desktop586rc8-2mnb (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent vga=788 
initrd		(hd2,1)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		desktop586 2.6.27.4-1mnb (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27.4-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.4-1mnb root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent vga=788 
initrd		(hd2,1)/boot/initrd-2.6.27.4-desktop586-1mnb.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		desktop586 2.6.27.4-2mnb (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27.4-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.4-2mnb root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent vga=788 
initrd		(hd2,1)/boot/initrd-2.6.27.4-desktop586-2mnb.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		desktop586 2.6.27.5-2mnb (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27.5-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.5-2mnb root=UUID=eeb42dc2-d8f5-4a1a-9474-468e1b87e0da splash=silent vga=788 
initrd		(hd2,1)/boot/initrd-2.6.27.5-desktop586-2mnb.img
savedefault
boot


=============================== sdc4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc4
UUID=28efa3da-a054-4b5d-98bc-f9777f2734b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=a5a7dd73-a75c-4290-8889-d00db30d667f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc4/boot: ==================================

total 25528
drwxr-xr-x  3 root root    4096 2008-12-17 02:07 .
drwxr-xr-x 21 root root    4096 2009-01-14 23:35 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-14 19:04 grub
-rw-r--r--  1 root root 8671661 2008-12-14 19:04 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671144 2008-12-17 02:07 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

=============================== sdc4/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2008-12-14 19:04 .
drwxr-xr-x 3 root root   4096 2008-12-17 02:07 ..
-rw-r--r-- 1 root root    197 2008-12-14 18:36 default
-rw-r--r-- 1 root root     45 2008-12-14 18:36 device.map
-rw-r--r-- 1 root root   8108 2008-12-14 18:36 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-14 18:36 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-14 18:36 installed-version
-rw-r--r-- 1 root root   8712 2008-12-14 18:36 jfs_stage1_5
-rw-r--r-- 1 root root  10681 2008-12-14 19:04 menu.lst
-rw-r--r-- 1 root root  10597 2008-12-14 19:04 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-14 18:36 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-14 18:36 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-14 18:36 stage1
-rw-r--r-- 1 root root 121460 2008-12-14 18:36 stage2
-rw-r--r-- 1 root root   9556 2008-12-14 18:36 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-16
I think the issue might be that Mandriva's Grub is not as recent as Ubuntu's Grub and thus can't deal with the new "uuid" notation that Ubuntu's Grub uses. Since you all ready have Grub installed to the boot sector of the Ubuntu partition, probably all you need to do to fix the problem is use "chainloader" instead of the "configfile" notation for Ubuntu in your Mandriva's menu.lst. In other words, in your Mandriva's menu.lst, how about changing the Ubuntu entry to be:
```
title Ubuntu 8.10
root (hd2,3)
chainloader +1
```
Let me know if that works or not.

---

### Post by Mr Pockets151 on 2009-01-16
Haha....great I will try that.  But, I decided that I'm getting rid of MDV 09 all together.  3 OSes is enough.  I find myself using Intrepid all the time anyway.  The support is excellent.

I'm going to repartion my windows install over the mdv partition.  So when I'm done I'm planning to use the Ubutnu GRUB.  I can just restore that using the LIVE CD right?  

Before I do that though, I will try what you suggested to give you a response if that worked or not. 

I know that when I installed Ubuntu I chose to install the GRUB on the Ubuntu partition not the MBR.

---

