---
title: "Grub and two windows installations"
date: 2009-01-21
forum: General Help
---

### Post by sunjayc_99 on 2009-01-21
I'm having a little bit of trouble with GRUB.

My current setup is this:
Windows XP Home on the first drive, Ubuntu and Windows XP Pro on the second drive.
I installed Ubuntu after XP Home was already installed, and XP Pro after that.

I know that if I boot into XP Home from GRUB, I can select XP Pro from Windows' own boot menu. But I want to try and boot into XP Pro directly.
I've already copied over NTLDR and boot.ini into XP Pro's partition.

My problem is this: Any way I try to boot directly into XP Pro from GRUB, my computer immediately restarts on me. I've tried mapping the drives and hiding the XP Home partition, but it still restarts on me, too fast to see any errors.

This is my fdisk -l output:
```
Disk /dev/sda: 40.0 GB, 40037760000 bytes
240 heads, 63 sectors/track, 5171 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa7b9a7b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5170    39085168+  17  Hidden HPFS/NTFS
/dev/sda2            5171        5172        8032+  83  Linux

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
240 heads, 63 sectors/track, 15500 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb2c5b2c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9794    74035521   83  Linux
/dev/sdb2   *        9795       15301    41632920    7  HPFS/NTFS
/dev/sdb3           15302       15501     1510110    5  Extended
/dev/sdb5           15302       15501     1510078+  82  Linux swap / Solaris
```

---

### Post by caljohnsmith on 2009-01-22
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot your two Windows installs separately.

---

### Post by sunjayc_99 on 2009-01-23
Here's the output from the script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40037760000 bytes
240 heads, 63 sectors/track, 5171 cylinders, total 78198750 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7b9a7b9

/dev/sda1     *           63   78,170,399   78,170,337  17 Hidden HPFS/NTFS
/dev/sda2         78,172,290   78,188,354       16,065  83 Linux

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
240 heads, 63 sectors/track, 15500 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2c5b2c5

/dev/sdb1                 63  148,071,104  148,071,042  83 Linux
/dev/sdb2     *  148,085,280  231,351,119   83,265,840   7 HPFS/NTFS
/dev/sdb3        231,352,065  234,372,284    3,020,220   5 Extended
/dev/sdb5        231,352,128  234,372,284    3,020,157  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D4C08A87C08A7012" TYPE="ntfs" 
/dev/sdb1: UUID="375f30a7-4449-41f6-bd72-201e9d64317d" TYPE="ext3" 
/dev/sdb2: UUID="2AA0499EA049717D" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="6b938cf8-6735-4814-b278-7f424a442867" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sunjayc99/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sunjayc99)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/menu.lst: ===========================

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
default		saved

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
# kopt=root=UUID=375f30a7-4449-41f6-bd72-201e9d64317d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=375f30a7-4449-41f6-bd72-201e9d64317d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=375f30a7-4449-41f6-bd72-201e9d64317d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Microsoft Windows XP Pro SP3
root		(hd1,1)
savedefault
chainloader	+1

title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=375f30a7-4449-41f6-bd72-201e9d64317d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=6b938cf8-6735-4814-b278-7f424a442867 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 18080
drwxr-xr-x  3 root root    4096 2009-01-22 17:20 .
drwxr-xr-x 21 root root    4096 2009-01-22 17:20 ..
-rw-r--r--  1 root root  422838 2008-11-27 14:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80051 2008-11-27 14:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    4096 2009-01-22 17:20 grub
-rw-r--r--  1 root root 7501750 2009-01-17 15:00 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7501625 2009-01-17 14:58 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  905633 2008-11-27 14:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921976 2008-11-27 14:13 vmlinuz-2.6.24-23-generic

=============================== sdb1/boot/grub: ===============================

total 220
drwxr-xr-x 2 root root   4096 2009-01-22 17:20 .
drwxr-xr-x 3 root root   4096 2009-01-22 17:20 ..
-rw-r--r-- 1 root root    197 2009-01-21 18:01 default
-rw-r--r-- 1 root root     30 2009-01-02 21:30 device.map
-rw-r--r-- 1 root root   8056 2009-01-21 18:01 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-21 18:01 fat_stage1_5
-rw-r--r-- 1 root root     18 2009-01-21 18:01 installed-version
-rw-r--r-- 1 root root   8608 2009-01-21 18:01 jfs_stage1_5
-rw-r--r-- 1 root root   4642 2009-01-22 17:20 menu.lst
-rw-r--r-- 1 root root   4642 2009-01-22 17:20 menu.lst~
-rw-r--r-- 1 root root   4642 2009-01-22 17:19 menu.lst.bak
-rw-r--r-- 1 root root   7324 2009-01-21 18:01 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-21 18:01 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 18:01 stage1
-rw-r--r-- 1 root root 108356 2009-01-21 18:01 stage2
-rw-r--r-- 1 root root   9276 2009-01-21 18:01 xfs_stage1_5

=================== sdb1: Location  of files loaded by Grub: ===================


  30.4GB: boot/grub/menu.lst
  32.1GB: boot/grub/stage2
  31.7GB: boot/initrd.img-2.6.24-23-generic
  31.7GB: boot/initrd.img-2.6.24-23-generic.bak
  30.6GB: boot/vmlinuz-2.6.24-23-generic
  31.7GB: initrd.img
  30.6GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on sda2

00000000  d2 04 00 00 02 0a a2 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000010  02 0a a3 66 00 40 00 00  d2 04 00 00 02 0a a4 66  |...f.@.........f|
00000020  00 40 00 00 d2 04 00 00  02 0a a5 66 00 40 00 00  |.@.........f.@..|
00000030  d2 04 00 00 02 0a a6 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000040  02 0a a7 66 00 40 00 00  d2 04 00 00 02 0a a8 66  |...f.@.........f|
00000050  00 40 00 00 d2 04 00 00  02 0a a9 66 00 40 00 00  |.@.........f.@..|
00000060  d2 04 00 00 02 0a aa 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000070  02 0a ab 66 00 60 00 00  d2 04 00 00 02 0a ac 66  |...f.`.........f|
00000080  00 40 00 00 00 04 00 00  02 07 ad 66 00 40 00 00  |.@.........f.@..|
00000090  d2 04 00 00 02 0a ae 66  00 50 00 00 d2 04 00 00  |.......f.P......|
000000a0  02 0a af 66 00 00 00 00  d2 04 00 00 02 0a b1 66  |...f...........f|
000000b0  00 40 00 00 d2 04 00 00  02 0a b2 66 00 40 00 00  |.@.........f.@..|
000000c0  d2 04 00 00 02 0a b3 66  00 40 00 00 d2 04 00 00  |.......f.@......|
000000d0  02 0a b4 66 00 40 00 00  d2 04 00 00 02 0a b5 66  |...f.@.........f|
000000e0  00 40 00 00 d2 04 00 00  02 0a b6 66 00 40 00 00  |.@.........f.@..|
000000f0  d2 04 00 00 02 0a b7 66  00 50 00 00 d2 04 00 00  |.......f.P......|
00000100  02 0a b8 66 00 40 00 00  d2 04 00 00 02 0a b9 66  |...f.@.........f|
00000110  00 50 00 00 d2 04 00 00  02 0a ba 66 00 40 00 00  |.P.........f.@..|
00000120  d2 04 00 00 02 0a bb 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000130  02 0a bc 66 00 40 00 00  d2 04 00 00 02 0a bd 66  |...f.@.........f|
00000140  00 40 00 00 d2 04 00 00  02 0a be 66 00 40 00 00  |.@.........f.@..|
00000150  d2 04 00 00 02 0a bf 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000160  02 0a c0 66 00 40 00 00  d2 04 00 00 02 0a c1 66  |...f.@.........f|
00000170  00 40 00 00 d2 04 00 00  02 0a c2 66 00 40 00 00  |.@.........f.@..|
00000180  d2 04 00 00 02 0a c4 66  00 40 00 00 d2 04 00 00  |.......f.@......|
00000190  02 0a c5 66 00 40 00 00  d2 04 00 00 02 0a c6 66  |...f.@.........f|
000001a0  00 40 00 00 d2 04 00 00  02 0a c7 66 00 40 00 00  |.@.........f.@..|
000001b0  d2 04 00 00 02 0a c8 66  00 40 00 00 d2 04 00 00  |.......f.@......|
000001c0  02 0a c9 66 00 40 00 00  d2 04 00 00 02 0a ca 66  |...f.@.........f|
000001d0  00 40 00 00 d2 04 00 00  02 0a cb 66 00 40 00 00  |.@.........f.@..|
000001e0  d2 04 00 00 02 0a cd 66  00 40 00 00 d2 04 00 00  |.......f.@......|
000001f0  02 0a ce 66 00 40 00 00  d2 04 00 00 02 0a cf 66  |...f.@.........f|
00000200


=============================== StdErr Messages: ===============================

/dev/sda2: unknown volume type
```

Ignore the menu.lst settings for the Windows entries; I haven't been using those.

---

### Post by caljohnsmith on 2009-01-23
It looks like you're about 90% of the way to get XP Pro booting by itself. For one thing, you'll need to copy over the "NTDETECT.COM" file to the XP Pro partition as well, so how about doing:
```
sudo mkdir /mnt/sda1 /mnt/sdb2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb2 /mnt/sdb2
sudo cp /mnt/sda1/NTDETECT.COM /mnt/sdb2
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your XP Pro entry to be:
```
title		Microsoft Windows XP Pro SP3
root		(hd1,1)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
chainloader	+1
```
Then reboot, try XP Pro from Grub, and let me know exactly what happens. We can work from there.

---

### Post by sunjayc_99 on 2009-01-23
Looks like all I needed was the NTDETECT.COM, 'cause it works perfectly now.
Thanks!

---

### Post by caljohnsmith on 2009-01-23
Glad to hear you have XP Pro booting from its own partition now. Cheers and and enjoy all your OSes. :)

---

### Post by nathski on 2011-05-16
Hello Guys, I'm new here, but glad to join the forum, I have a situation... i recently change the OS of my computer from XP to windows 7, then tried out the new Ubuntu 11.04,then tried to go back to windows xp not knowing about the GRUB,so i checked the forum..now what's happening now is reinstalled back the Ubuntu now showing on the GRUB menu aside the linux boot option also: windows NT/2000/xp (loader) (on /dev/sda1) and microsoft windows xp professional (on /dev/sdab2),now i chose the first boot option for windows so i can tried to reinstall back the windows xp but while reinstall windows xp, the system prompted me of an error stating that: Fatal Error: one of the components that windows needs to continue setup could not be installed.

Data error (cyclic redundancy check).

If you are installing from a CD, there might be a problem with disc.... 
tried cleaning the disc and do the same process but still having same issue. Pls help me out, totally lost... at this point, thanks

---

