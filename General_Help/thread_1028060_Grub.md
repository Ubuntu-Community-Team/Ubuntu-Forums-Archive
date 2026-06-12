---
title: "Grub"
date: 2009-01-02
forum: General Help
---

### Post by RedSingularity on 2009-01-02
I just installed windows onto my PC and lost the grub boot.  How can i get it back?  By the way the computer is running on 2 HDD's.  One is for Ubuntu and the other for windows.

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-01-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

You have to resotore grub boot manager. Lilo would work too but I don't use it and don't feel like looking for an install description.

---

### Post by cdtech on 2009-01-02
1. Boot from a Live CD.

2. Open a Terminal. Get to a superuser prompt (sudo su).

3. Type "grub" which makes a **GRUB** prompt appear.

4. Type "find /boot/grub/stage1". You'll get a something like "(hd0)" or in my case "(hd0,1)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,1)".

6. Type "setup (hd0)". This is key, this will overwrite the MBR.

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by xarroyo on 2009-01-02
Also you can use the Super Grub.. This application helps you to restore the Grub! [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) In case you don't have the live cd.

---

### Post by cdtech on 2009-01-02
It's probably a little late to tell you this but while your in the Live CD you could save your Windows MBR to your Ubuntu install in case you need it later. After you reinstall GRUB you may want to back that up as well, just in case you need either later during your ventures.
```
sudo dd if=/dev/sda of=~/**.mbr**/Windows.mbr bs=512 count=1
```
Then after you restore GRUB:
```
sudo dd if=/dev/sda of=~/**.mbr**/Ubuntu.mbr bs=512 count=1
```
I created a hidden directory (.mbr) to store my MBR's.

---

### Post by RedSingularity on 2009-01-03
> **cdtech said:**
> 1. Boot from a Live CD.

2. Open a Terminal. Get to a superuser prompt (sudo su).

3. Type "grub" which makes a **GRUB** prompt appear.

4. Type "find /boot/grub/stage1". You'll get a something like "(hd0)" or in my case "(hd0,1)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,1)".

6. Type "setup (hd0)". This is key, this will overwrite the MBR.

7. Type "quit".

8. Restart the system. Remove the bootable CD.


I followed the instructions exactly and it said that everything was "Successful" but when i restart it is still booting directly into windows.

---

### Post by RedSingularity on 2009-01-03
Bump...

---

### Post by caljohnsmith on 2009-01-03
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by RedSingularity on 2009-01-04
```
<HTML>
<HEAD>
<TITLE>Page Unavailable</TITLE>
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
<style>
  body {
    background-image:url('http://publish.comcast.net/unavailable/bg_unavail.gif');
    background-repeat:repeat-x;
    }

</style>
</HEAD>
<BODY BGCOLOR="#aca0ae" LEFTMARGIN=0 TOPMARGIN=0 MARGINWIDTH=0 MARGINHEIGHT=0>


<!-- images in style (above) and referenced in below imagemap require absolute paths for proper functioning -->

<div align="center"><IMG SRC="http://publish.comcast.net/unavailable/unavailable.gif" WIDTH=995 HEIGHT=738 BORDER=0 ALT="" USEMAP="#unavailMap"></div>
<MAP NAME="unavailMap">
<AREA SHAPE="rect" ALT="" COORDS="690,605,787,632" HREF="http://www.spotlight.tv/advertisewithus/">
<AREA SHAPE="rect" ALT="" COORDS="566,605,682,631" HREF="http://www.comcast.net/signin.jsp?redirectUrl=https%3A%2F%2Fsso.comcast.net%2FComcast%2FIdP%2Fsso%3Ftarget%3Dhttp%253A%252F%252Fforums.comcast.net%252Fcomcastsupport%253Fcategory.id%253Devolution">
<AREA SHAPE="rect" ALT="" COORDS="465,605,557,631" HREF="http://www.comcast.com/Corporate/Move/default.html?CMP=BAC-COMMISC018">
<AREA SHAPE="rect" ALT="" COORDS="398,604,457,631" HREF="http://www.askcomcast.com/contactus.asp">
<AREA SHAPE="rect" ALT="" COORDS="301,605,389,630" HREF="http://www.comcast.net/terms/">
<AREA SHAPE="rect" ALT="" COORDS="196,606,291,629" HREF="http://www.comcast.net/privacy/">
<AREA SHAPE="rect" ALT="" COORDS="769,549,894,588" HREF="http://www.comcast.com/hdtv/?CMP=ILC-comcastnethdtv">
<AREA SHAPE="rect" ALT="" COORDS="643,548,744,587" HREF="http://www.comcast.com/shop/buyflow/default.ashx?SourcePage=VOIP&CMP=ILC-fcomcastnetcdv">
<AREA SHAPE="rect" ALT="" COORDS="527,549,617,585" HREF="http://www.comcast.com/shop/buyflow/default.ashx?SourcePage=Cable&CMP=ILC-fcomcastnetdcable">
<AREA SHAPE="rect" ALT="" COORDS="323,550,506,584" HREF="http://www.comcast.com/8mbps/?CMP=ILC-fcomcastnetdcable2">
<AREA SHAPE="rect" ALT="" COORDS="848,101,933,138" HREF="http://publish.comcast.net/auth.php?o=logout">
<AREA SHAPE="rect" ALT="" COORDS="758,101,842,139" HREF="http://publish.comcast.net/help/index/">
<AREA SHAPE="rect" ALT="" COORDS="666,102,752,140" HREF="http://publish.comcast.net/filemanager/files/all/">
<AREA SHAPE="rect" ALT="" COORDS="575,102,660,139" HREF="http://publish.comcast.net/settings/index/">
<AREA SHAPE="rect" ALT="" COORDS="485,102,570,140" HREF="http://publish.comcast.net/widgets/index/">
<AREA SHAPE="rect" ALT="" COORDS="393,102,479,140" HREF="http://publish.comcast.net/widgets/index/">
<AREA SHAPE="rect" ALT="" COORDS="302,102,387,139" HREF="http://publish.comcast.net/photos/index/">
<AREA SHAPE="rect" ALT="" COORDS="212,102,296,138" HREF="http://publish.comcast.net/pages/index/">
<AREA SHAPE="rect" ALT="" COORDS="124,104,205,138" HREF="http://publish.comcast.net/blog/index/">
<AREA SHAPE="rect" ALT="" COORDS="37,104,113,137" HREF="http://publish.comcast.net/home/">
</MAP>
<!-- End ImageReady Slices -->
</BODY>
</HTML>
```

---

### Post by caljohnsmith on 2009-01-04
Shadow121, I just now checked and the script is available on the server, so you shouldn't get a 404 error again. Please give it another try and let me know how it goes.

---

### Post by RedSingularity on 2009-01-04
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005c191

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   612992204   306496071   83  Linux
/dev/sdb2       612992205   625137344     6072570    5  Extended
/dev/sdb5       612992268   625137344     6072538+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FA107E5B107E1F37" TYPE="ntfs" 
/dev/sdb1: UUID="0b41bdc8-5b8d-4648-8936-fdcf190e6d1d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="227cb508-8c87-48fb-bc1d-a83e1767b7e8" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
# kopt=root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d

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
uuid		0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0b41bdc8-5b8d-4648-8936-fdcf190e6d1d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root





=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0b41bdc8-5b8d-4648-8936-fdcf190e6d1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=227cb508-8c87-48fb-bc1d-a83e1767b7e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 23788
drwxr-xr-x  3 root root    4096 2008-12-27 21:04 .
drwxr-xr-x 20 root root    4096 2008-12-27 21:04 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-02 01:48 grub
-rw-r--r--  1 root root 8195285 2008-12-27 21:03 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8195495 2008-12-27 21:04 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-02 01:48 .
drwxr-xr-x 3 root root   4096 2008-12-27 21:04 ..
-rw-r--r-- 1 root root    197 2008-12-27 15:29 default
-rw-r--r-- 1 root root     45 2008-12-27 15:29 device.map
-rw-r--r-- 1 root root   8108 2008-12-27 15:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-27 15:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-27 15:29 installed-version
-rw-r--r-- 1 root root   8712 2008-12-27 15:29 jfs_stage1_5
-rw-r--r-- 1 root root   4920 2009-01-02 01:48 menu.lst
-rw-r--r-- 1 root root   5103 2008-12-27 21:04 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-27 15:29 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-27 15:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-27 15:29 stage1
-rw-r--r-- 1 root root 121460 2008-12-27 15:29 stage2
-rw-r--r-- 1 root root   9556 2008-12-27 15:29 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-04
It looks like you all ready have Grub installed correctly to your Ubuntu sdb drive, so can you change your BIOS to boot the Ubuntu drive? That would be ideal, because then you can keep your drives independent of each other as far as booting is concerned.

---

### Post by RedSingularity on 2009-01-04
I will look into the bios now and give it a shot.

---

### Post by RedSingularity on 2009-01-04
That was it!  I cant believe i overlooked that!  What a dumb mistake on my part.  Well thanks a bunch for your help.  Appreciate it.  :)

---

### Post by caljohnsmith on 2009-01-04
You're welcome, glad to hear Ubuntu is booting OK now; cheers and have fun with Ubuntu. :)

---

