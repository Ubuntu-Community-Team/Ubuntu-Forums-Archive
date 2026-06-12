---
title: "GRUB inside GRUB"
date: 2009-01-03
forum: General Help
---

### Post by Longines on 2009-01-03
Installed 8.04 on my laptop using the live CD around six months ago. It gave me a GRUB dual boot with XP and everything worked fine.

Upgraded to 8.10 and everything still worked fine.

Attempted to upgrade to 9.04A2 yesterday and it failed hard on some hardware display issue - could only get to a terminal window.

Tried to boot from the live CD to reinstall 8.10 over 9.04 but GRUB appeared to be stopping any boot from CD. So I booted into Windows and ran umenu.exe from the CD. I chose the "Demo and full installation" option followed by "Help me to boot from CD". Everything installed fine and I now have my 8.10 back. However....

It appears to have installed a second copy of GRUB. If I choose the Windows XP option in GRUB I'm offered a second GRUB menu of "Ubuntu" or "Windows XP Professional" which appears to be a leftover from the "Help me to boot from CD".

How do I get rid of the second GRUB menu so it boots directly into XP when I select it on the first menu?

TIA.

---

### Post by caljohnsmith on 2009-01-03
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Longines on 2009-01-03
Short version: I've ended up with nested GRUB instances and I'd like to remove the child menu whilst keeping the parent.

[SIZE="2"]```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'vfat'

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       149693669 sectors, but according to the info from 
                       fdisk, it has 149693670 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8545ea45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8193149     4096543+  12  Compaq diagnostics
/dev/sda2   *     8193150   157886819    74846835    7  HPFS/NTFS
/dev/sda4       157886820   195366464    18739822+   5  Extended
/dev/sda5       193711833   195366464      827316   82  Linux swap / Solaris
/dev/sda6       157886946   193711769    17912412   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 5 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="0E4E-05CE" TYPE="vfat" 
/dev/sda2: UUID="58C8D566C8D54344" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="3e0e6379-87a6-4d81-a6c5-4435a39e3781" TYPE="swap" 
/dev/sda6: UUID="3a459dde-7622-480d-a90c-642d3bb83b13" TYPE="ext3" 

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
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/grant/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=grant)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


============================== sda2/ubuntu/disks: ==============================

total 4
drwxrwxrwx 1 root root    0 2009-01-02 23:34 .
drwxrwxrwx 1 root root 4096 2009-01-02 23:34 ..
drwxrwxrwx 1 root root    0 2009-01-02 23:34 boot
drwxrwxrwx 1 root root    0 2009-01-02 23:34 shared

=========================== sda2/ubuntu/disks/boot/: ===========================

total 0
drwxrwxrwx 1 root root 0 2009-01-02 23:34 .
drwxrwxrwx 1 root root 0 2009-01-02 23:34 ..
drwxrwxrwx 1 root root 0 2009-01-02 23:34 grub

========================= sda2/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-02 23:34 .
drwxrwxrwx 1 root root 0 2009-01-02 23:34 ..

========================= sda2/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-02 23:34 .
drwxrwxrwx 1 root root 0 2009-01-02 23:34 ..

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
default		2

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
# kopt=root=UUID=3a459dde-7622-480d-a90c-642d3bb83b13 ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a459dde-7622-480d-a90c-642d3bb83b13

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
uuid		3a459dde-7622-480d-a90c-642d3bb83b13
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=3a459dde-7622-480d-a90c-642d3bb83b13 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-4-generic
quiet

title		Ubuntu 8.10 (recovery mode)
uuid		3a459dde-7622-480d-a90c-642d3bb83b13
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=3a459dde-7622-480d-a90c-642d3bb83b13 ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-4-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows NT/2000/XP
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=3a459dde-7622-480d-a90c-642d3bb83b13 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3e0e6379-87a6-4d81-a6c5-4435a39e3781 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 54716
drwxr-xr-x  3 root root    4096 2009-01-03 01:41 .
drwxr-xr-x 22 root root    4096 2009-01-03 01:37 ..
-rw-r--r--  1 root root  422607 2008-04-10 17:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root  528276 2009-01-02 00:34 abi-2.6.28-4-generic
-rw-r--r--  1 root root   79964 2008-04-10 17:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
-rw-r--r--  1 root root   96624 2009-01-02 00:34 config-2.6.28-4-generic
drwxr-xr-x  2 root root    4096 2009-01-03 09:09 grub
-rw-r--r--  1 root root 7884370 2008-05-07 17:34 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 2008-04-22 19:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 8197149 2009-01-03 01:36 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8197073 2009-01-03 01:41 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root 7650873 2009-01-02 16:34 initrd.img-2.6.28-4-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 17:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root 1413039 2009-01-02 00:34 System.map-2.6.28-4-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2009-01-02 00:36 vmcoreinfo-2.6.28-4-generic
-rw-r--r--  1 root root 1904248 2008-04-10 17:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic
-rw-r--r--  1 root root 3342384 2009-01-02 00:34 vmlinuz-2.6.28-4-generic

=============================== sda6/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-03 09:09 .
drwxr-xr-x 3 root root   4096 2009-01-03 01:41 ..
-rw-r--r-- 1 root root    197 2009-01-03 00:23 default
-rw-r--r-- 1 root root     15 2008-05-07 17:34 device.map
-rw-r--r-- 1 root root   8108 2009-01-03 00:23 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-03 00:23 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 00:23 installed-version
-rw-r--r-- 1 root root   8712 2009-01-03 00:23 jfs_stage1_5
-rw-r--r-- 1 root root   4688 2009-01-03 07:10 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-03 00:23 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-03 00:23 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 00:23 stage1
-rw-r--r-- 1 root root 121460 2009-01-03 00:23 stage2
-rw-r--r-- 1 root root   9556 2009-01-03 00:23 xfs_stage1_5

No errors were reported.
```[/SIZE]

---

### Post by caljohnsmith on 2009-01-03
OK, I believe I see the issue; you still have Ubuntu installed inside of Windows via Wubi. If you don't need your Wubi installation any more, then when you are in Windows go to Control Panel > Add/Remove Programs, and there you can uninstall Ubuntu from Windows. As long as any antivirus programs you have don't interfere with the uninstall process, that should remove Ubuntu from your Windows boot menu. How about trying that and let me know how it goes.

---

### Post by Longines on 2009-01-03
I worked out from your(?) excellent script output that it was Windows' boot.ini that was generating the child "GRUB" menu. Google helped me edit it back to something less intrusive.

Ubuntu/Wubi was in Add/Remove which was a bit of a surprise given that I'd chosen "Run Live CD and install" from within Windows rather than 'Install the Wubi App' option. No harm, no foul though.

Many thanks for all your help.

---

### Post by caljohnsmith on 2009-01-03
Glad you have it fixed; just thought I'd mention that if Ubuntu uninstalls OK using Add/Remove Programs in Windows, then you don't have to manually modify your boot.ini file. But I'm glad to see you figured it out anyway. By the way, that really useful script is the creation of forum member meierfra, so he deserves the credit for it. Cheers and have fun with Ubuntu. :)

---

