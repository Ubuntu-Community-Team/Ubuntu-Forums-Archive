---
title: "Grub won't recognize Vista"
date: 2009-01-08
forum: Desktop Environments
---

### Post by vio919 on 2009-01-08
Hello, I had Vista Ultimate installed on my Dell and I wanted to install Ubuntu and have a dual boot between the two with grub.  I had already done this on my laptop so I figured it wouldn't be a problem.

When I first installed Vista I set up partitions as follows (sizes are approximate):

-30gb partition for XP Core ( originally had a dual boot between vista and a this version of XP, but I later deleted the partition because I never used it)

-50gb partition for Vista

-20gb partition for Ubuntu (for future use)

-400gb "data" partition


I decided I would install Ubuntu to the XP Core partition and combine my original Ubuntu partition into my data one.  So before I went to install ubuntu they were like this (sizes are approximate):

30gb for ubuntu
50gb for vista
420gb for data

When I was installling Ubuntu and it got to the screen where you choose what partition to install it to, it wouldn't give me the option of installing it to the partition I wanted it in.  Instead I had to select manual and manage the partitions myself.  This is how I set them up and how they remain as of now:

------------------------------------------------------------------------
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x418a4189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       60800   488375968+   f  W95 Ext'd (LBA)
/dev/sda5   *        3825       10198    51199123+   7  HPFS/NTFS
/dev/sda6           12749       60800   385977658+   7  HPFS/NTFS
/dev/sda7               1        3762    30218170+  83  Linux
/dev/sda8            3763        3824      497983+  82  Linux swap/Solaris
------------------------------------------------------------------------


so I continued with the installation and there were no errors and Ubuntu worked fine, but when I restarted Vista was not in the grub menu despite that it's supposed to automatically detect that it's there.  My friend told me that I needed to edit my menu.lst file and he walked me through it.  However it says “Invalid device requested” when I try to select it. We ended up trying “hd0,” and then just about every number from 1 to 8 but it wouldn't work. This is the windows section of my menu.lst file

title			Windows Vista
root			(hd0,4)
makeactive
chainloader 		+1

When we finally gave up trying to get it to work through grub, we decided to put the windows bootloader back via Vista repair disk.  When I booted from the disc I selected 'repair' but on the screen where it should list the installed operating system(s) it did not show anything.  It said that if the list is empty then you need to load drivers for your hard disk.  But when I clicked load drivers it wanted an .INF file, and I don't know where to get that.  So that didn't work.

I'm at a loss as to what to do next.  If anyone could help me out it would be appreciated.  Thanks,

Christian

---

### Post by caljohnsmith on 2009-01-08
It looks like part of the issue is your Windows Vista is on a logical partition and not a primary one. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Vista booting problem might be.

---

### Post by vio919 on 2009-01-08
Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  Windows Vista
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda8: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x418a4189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   976751999   488375968+   f  W95 Ext'd (LBA)
/dev/sda5   *    61432623   163830869    51199123+   7  HPFS/NTFS
/dev/sda6       204796683   976751999   385977658+   7  HPFS/NTFS
/dev/sda7             189    60436529    30218170+  83  Linux
/dev/sda8        60436593    61432559      497983+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 5 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="9078D9B778D99C72" LABEL="VistaU" TYPE="ntfs" 
/dev/sda6: UUID="1680F13980F12043" LABEL="DATA" TYPE="ntfs" 
/dev/sda7: UUID="569125c7-5a90-4193-8cdf-149b17196ce2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="b9fe7100-79ab-4683-b310-042c9fe8389b" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/christian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christian)

=========================== sda7/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Microsoft Windows Vista
root		(hd0,4)
makeactive
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=569125c7-5a90-4193-8cdf-149b17196ce2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b9fe7100-79ab-4683-b310-042c9fe8389b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda7/boot: ==================================

total 36364
drwxr-xr-x  3 root root    4096 2009-01-07 16:39 .
drwxr-xr-x 21 root root    4096 2009-01-07 16:36 ..
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-07 16:36 grub
-rw-r--r--  1 root root 7487150 2009-01-07 16:31 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7879155 2008-12-05 02:41 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7488602 2009-01-07 16:39 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7488173 2009-01-07 16:36 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda7/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-07 16:36 .
drwxr-xr-x 3 root root   4096 2009-01-07 16:39 ..
-rw-r--r-- 1 root root    197 2008-12-05 02:42 default
-rw-r--r-- 1 root root     15 2008-12-05 02:42 device.map
-rw-r--r-- 1 root root   8056 2008-12-05 02:42 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-05 02:42 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-05 02:42 installed-version
-rw-r--r-- 1 root root   8608 2008-12-05 02:42 jfs_stage1_5
-rw-r--r-- 1 root root   4345 2009-01-08 00:11 menu.lst
-rw-r--r-- 1 root root   4352 2009-01-07 16:36 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-05 02:42 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-05 02:42 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-05 02:42 stage1
-rw-r--r-- 1 root root 108356 2008-12-05 02:42 stage2
-rw-r--r-- 1 root root   9276 2008-12-05 02:42 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

---

### Post by vio919 on 2009-01-10
Bump.  Can anyone find any answers in the above info?

---

### Post by caljohnsmith on 2009-01-10
It looks like you have at least a few issues preventing you from booting Vista from Grub right now. For one thing, your Vista partition has a Windows XP boot sector instead of a Vista one, meaning that it will try and boot XP's "ntldr" rather than Vista's "bootmgr". The other issue is that your Vista partition is missing its boot files. And the last problem that I see is that your Grub entry for Vista uses "makeactive", which unfortunately won't work because Vista is on a logical parition (sda5); Grub cannot set the boot flag on a logical partition (i.e. make it "active"), only on a primary one, so Grub will immediately return an error if you add "makeactive" to a boot stanza for a logical partition. But the good news is that all those issues should be easily fixable, so you probably don't need to reinstall Vista in order to fix those problems. How about following [this tuturial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore Vista's boot files, and also it gives specific instructions for what special steps you need to take to boot Vista from a logical partition as you are trying to do. Since the script results you posted didn't show any problems with the NTFS file system parameters that are embedded in the Vista boot sector, for now it looks like you can skip step 3 in that tutorial, and just do steps 1 and 2. How about giving that a shot and let me know how it goes, or let me know if you run into problems. :)

---

### Post by sayakb on 2009-01-10
Do take a look at supergrub disk.

---

### Post by vio919 on 2009-01-10
I tried following the tutorial, but, in the second step, the last command, I was unable to execute it. Apparently the disk does not have the file bootsect.ext. The only files in the boot folder on the disk are bcd, boot.sdi, and bootfix.bin. I tried booting Vista without executing this last command, but it says starting up and just hangs there, and I have to manually reboot in order to get out of it.

---

### Post by caljohnsmith on 2009-01-11
> **vio919 said:**
> I tried following the tutorial, but, in the second step, the last command, I was unable to execute it. Apparently the disk does not have the file bootsect.ext. The only files in the boot folder on the disk are bcd, boot.sdi, and bootfix.bin. I tried booting Vista without executing this last command, but it says starting up and just hangs there, and I have to manually reboot in order to get out of it.
So did you have to download and use the Vista Recovery CD that the tutorial links to? If so that would be the issue. How about instead using this command from the Vista CD:
```
bootrec /fixboot

```
Then proceed with any other steps/changes you need to make. If you run into any problems booting Vista after doing everything, please run the Boot Info Script again and post the results. We can work from there.

---

### Post by pinged on 2009-01-11
Shouldn't this be moved to a different location ie not desktop environments?

---

### Post by vio919 on 2009-01-12
update:

I tried bootrec /fixboot in the recovery disk prompt, but it didn't recognize the command.

I tried step 3 and I can now launch into vista from Grub, but I get the BSOD either at the logon screen or shortly after logging on. :confused:  

Below is an update results.txt.  I haven't been able to get a clean shutdown from vista yet without getting BSOD'd, so it says the NTFS partitions can't be mounted.  If I manage to cleanly shut down I'll post new results.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g force 0 0

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda8: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x418a4189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   976751999   488375968+   f  W95 Ext'd (LBA)
/dev/sda5   *    61432623   163830869    51199123+   7  HPFS/NTFS
/dev/sda6       204796683   976751999   385977658+   7  HPFS/NTFS
/dev/sda7             189    60436529    30218170+  83  Linux
/dev/sda8        60436593    61432559      497983+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 5 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="9078D9B778D99C72" LABEL="VistaU" TYPE="ntfs" 
/dev/sda6: UUID="1680F13980F12043" LABEL="DATA" TYPE="ntfs" 
/dev/sda7: UUID="569125c7-5a90-4193-8cdf-149b17196ce2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="b9fe7100-79ab-4683-b310-042c9fe8389b" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/christian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christian)

=========================== sda7/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Microsoft Windows Vista
rootnoverify	(hd0,4)
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=569125c7-5a90-4193-8cdf-149b17196ce2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=569125c7-5a90-4193-8cdf-149b17196ce2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b9fe7100-79ab-4683-b310-042c9fe8389b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda7/boot: ==================================

total 36364
drwxr-xr-x  3 root root    4096 2009-01-07 16:39 .
drwxr-xr-x 21 root root    4096 2009-01-07 16:36 ..
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-10 22:53 grub
-rw-r--r--  1 root root 7487150 2009-01-07 16:31 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7879155 2008-12-05 02:41 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7488602 2009-01-07 16:39 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7488173 2009-01-07 16:36 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda7/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-10 22:53 .
drwxr-xr-x 3 root root   4096 2009-01-07 16:39 ..
-rw-r--r-- 1 root root    197 2008-12-05 02:42 default
-rw-r--r-- 1 root root     15 2008-12-05 02:42 device.map
-rw-r--r-- 1 root root   8056 2008-12-05 02:42 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-05 02:42 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-05 02:42 installed-version
-rw-r--r-- 1 root root   8608 2008-12-05 02:42 jfs_stage1_5
-rw-r--r-- 1 root root   4341 2009-01-10 22:53 menu.lst
-rw-r--r-- 1 root root   4345 2009-01-08 00:11 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-05 02:42 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-05 02:42 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-05 02:42 stage1
-rw-r--r-- 1 root root 108356 2008-12-05 02:42 stage2
-rw-r--r-- 1 root root   9276 2008-12-05 02:42 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```

---

### Post by caljohnsmith on 2009-01-12
OK, how about booting the Vista Recovery CD again, and using the "diskpart" and "list volume" commands that you previously used, find the drive letter for the Vista partition, and then do:
```
chkdsk /r C:
```
Replace C with the Vista partition drive letter if necessary, and run the command as many times as it takes until it reports no errors. Also, it turns out there is a bug in the 0.10 version of the Boot Info Script that prevents it from correctly analyzing the boot sector of an NTFS partition for errors, but fortunately that bug has been fixed (we think) in the 0.11 version. Since there is some doubt, I think it would be a good idea to check whether your Vista partition boot sector needs fixing with testdisk. To do that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows Vista sda5 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know. We can work from there. :)

---

### Post by carml on 2009-01-12
I think you have to reinstall Windows Vista,and to do so you have to format a partition for Vista,that's why it says you it cannot access the disk.

---

### Post by vio919 on 2009-01-12
> **caljohnsmith said:**
> OK, how about booting the Vista Recovery CD again, and using the "diskpart" and "list volume" commands that you previously used, find the drive letter for the Vista partition, and then do:
```
chkdsk /r C:
```
Replace C with the Vista partition drive letter if necessary, and run the command as many times as it takes until it reports no errors. Also, it turns out there is a bug in the 0.10 version of the Boot Info Script that prevents it from correctly analyzing the boot sector of an NTFS partition for errors, but fortunately that bug has been fixed (we think) in the 0.11 version. Since there is some doubt, I think it would be a good idea to check whether your Vista partition boot sector needs fixing with testdisk. To do that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows Vista sda5 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know. We can work from there. :)

Ok I ran chkdsk twice.  The first time it said it made corrections to the file system, and the second time it said it found no problems.  However, after finishing each time, the last output line said "failed to transfer logged messages to the event log with status 50."  I'm not sure if that's relevant or not.

I then followed your testdisk instructions and it said Extrapolated boot sector and current boot sector are identical.

---

### Post by caljohnsmith on 2009-01-12
OK, how about trying:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda5
```
If ntfsfix says it is successful, next try:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt
```
And please post the output of all the above commands. Also, when you were following the directions in that Vista tutorial, when you ran the bcdedit commands, were they all successful, or did any of them return an error?

---

### Post by vio919 on 2009-01-12
Here's the terminal log:

```
**christian@dell8400:~$ sudo apt-get install ntfsprogs**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ntfsprogs
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 269kB of archives.
After this operation, 688kB of additional disk space will be used.
Get:1 http://gulus.usherbrooke.ca hardy/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 269kB in 3s (76.2kB/s)    
Selecting previously deselected package ntfsprogs.
(Reading database ... 113913 files and directories currently installed.)
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Setting up ntfsprogs (2.0.0-1ubuntu2) ...
**christian@dell8400:~$ sudo ntfsfix /dev/sda5**
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.

```

And yes, the bcdedit commands completed successfully with no errors.

---

### Post by vio919 on 2009-01-13
Sorry, I forgot to do the last part of your post.  Here it is:

```
**christian@dell8400:~$ sudo mount /dev/sda5 /mnt**
**christian@dell8400:~$ ls -l /mnt**
total 4497385
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root          0 2009-01-11 07:01 boot
-rwxrwxrwx 1 root root       7324 2009-01-13 01:30 bootex.log
-rwxrwxrwx 1 root root     332497 2007-11-03 23:29 bootmgr
drwxrwxrwx 1 root root          0 2008-11-26 00:19 Config.Msi
-rwxrwxrwx 3 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 08:00 Documents and Settings
drwxrwxrwx 1 root root          0 2008-11-26 17:47 FolderShareTemp
-rwxrwxrwx 1 root root 2145558528 2009-01-13 01:32 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-10-04 15:49 NVIDIA
-rwxrwxrwx 1 root root 2459373568 2008-11-26 17:03 pagefile.sys
drwxrwxrwx 1 root root          0 2008-10-05 12:35 PerfLogs
drwxrwxrwx 1 root root       4096 2008-11-25 23:22 ProgramData
drwxrwxrwx 1 root root      12288 2008-11-30 00:17 Program Files
drwxrwxrwx 1 root root          0 2008-10-04 23:16 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-10-05 01:00 RECYCLER
drwxrwxrwx 1 root root       8192 2008-12-01 20:35 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-04 23:12 Users
drwxrwxrwx 1 root root      16384 2008-10-28 16:22 Windows
```

---

### Post by caljohnsmith on 2009-01-14
OK, how about trying the following command from the Vista Recovery CD:
```
bootrec /rebuildbcd
```
If that completes without any errors, let me know if that changes anything about Vista's booting behavior.

---

### Post by vio919 on 2009-01-14
I did that command and then it said scanning and it found 1 windows installation.  It then asked:

Add installation to boot list? Yes(Y)/No(N)/All(A):a

so I entered Y and it said "element not found"

And it says that regardless of whether I enter Y, N or A.


Also,  bootrec /fixboot returns the same message; Element not found.

---

### Post by caljohnsmith on 2009-01-14
I'm out of ideas about fixing your Vista install, so unless you can think of anything else, probably your best bet is to save all your important files from your Vista partition and then reinstall Vista. Do you have any kind of Vista install CD that came with your laptop? If you do, I would be careful because they are usually OEM Install CDs, and often they will simply overwrite everything on the HDD in order to reinstall Vista. Good luck and let me know how it goes.

---

### Post by vio919 on 2009-01-14
> **caljohnsmith said:**
> I'm out of ideas about fixing your Vista install, so unless you can think of anything else, probably your best bet is to save all your important files from your Vista partition and then reinstall Vista. Do you have any kind of Vista install CD that came with your laptop? If you do, I would be careful because they are usually OEM Install CDs, and often they will simply overwrite everything on the HDD in order to reinstall Vista. Good luck and let me know how it goes.

Ok, thanks for your efforts.  I'll probably end up formatting the whole hard drive and installing the Windows 7 beta, which I'm currently downloading.  I don't have too many files to back up since it's a pretty new hard drive, so it shouldn't be too much of a hassle.  Thanks again.

Christian

---

