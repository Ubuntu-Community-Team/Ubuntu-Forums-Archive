---
title: "Dual Boot Grub Error"
date: 2008-12-24
forum: General Help
---

### Post by DrussRob on 2008-12-24
Firstly I should say I have searched for four days on this topic trying different fixes mentioned here on this website as well as others and I have not been able to solve my problem thus far. 

Here's the scene:

Desktop computer with two internal hard drives; a 250 gb master and a 120 gb slave.

Ubuntu is installed wholly to the master drive (250gb), the only other partitions on it are the Linux swap spaces.

The second drive (120gb) was first partitioned into three parts being ext3-ext3-ntfs. The first ext3 partition housed my vdi file for virtualbox. The second ext3 partition was simple storage. The 3rd partition which is ntfs was created to install XP as I couldnt burn through virtualbox using the proprietary program I must use for work.
Once I installed XP on partition 3 I realized I didnt make the partition large enough and was quickly running out of room. So, I went back into Ubuntu and deleted the second ext3 partition and then the 3rd (ntfs) partition (which is now the second) was grown to use the remaining space to have enough room for my work projects.

Now, the problem seems to be coming clearer now eh?

Every time I try to boot into windows I get Grub error 13 or 12.

I've tried every suggestion, hint, tip and trick I've found and nothing seems to work. I've manually edited the boot.ini file for windows, which in retrospect I did prematurely (and mostly out of frustration) because I still have not been able to boot to the windows partition to even get a windows error. OK, maybe enough talking and time for the meat of the situation.

Thanks for ANY help or insight anyone may be able to provide!

**$ sudo fdisk -l**
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa038ccf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241199878+  83  Linux
/dev/sda2           30029       30401     2996122+   5  Extended
/dev/sda5           30029       30401     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b2b9b2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6434    51681073+  83  Linux
/dev/sdb2   *        6435       14593    65537167+   7  HPFS/NTFS

```(What do the above asterix denote? primary?)

**Windows boot.ini**
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

**current menu.lst**
```
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
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=81dd4f27-6fb8-4801-8a42-b919af7875b1

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
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Once again thanks for any help. 

and MERRY CHRISTMAS! :)

---

### Post by caljohnsmith on 2008-12-24
In order to get a clearer picture of your setup, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by DrussRob on 2008-12-24
OK, I've got it. I apologize about the long response time. I was interrupted by some last minute Christmas shopping.

The following is the results.txt file:
```
/dev/sdc has no valid partition table.
/dev/sdd has no valid partition table.
/dev/sde has no valid partition table.
/dev/sdf has no valid partition table.
/dev/sdg has no valid partition table.
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on boot drive #2 in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  Extended Partition

sda5:
    File system:  swap

sdb1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sdb2 starts at sector 103362210.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa038ccf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   482399819   241199878+  83  Linux
/dev/sda2       482399820   488392064     2996122+   5  Extended
/dev/sda5       482399883   488392064     2996091   82  Linux swap / Solaris

/dev/sda: OK


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b2b9b2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   103362209    51681073+  83  Linux
/dev/sdb2   *   103362210   234436544    65537167+   7  HPFS/NTFS

/dev/sda: OK
/dev/sdb: OK


/dev/sda: OK
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading


/dev/sda: OK
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading


/dev/sda: OK
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading


/dev/sda: OK
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading


/dev/sda: OK
/dev/sdb: OK
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

/dev/sda1: UUID="81dd4f27-6fb8-4801-8a42-b919af7875b1" TYPE="ext3" 
/dev/sda5: UUID="a3e2e957-6449-4383-931b-dc181546bfc5" TYPE="swap" 
/dev/sdb1: UUID="ef7ca9cc-3dd2-46e0-a5df-07a082238e55" TYPE="ext3" 
/dev/sdb2: UUID="63C43ED578CD5ABA" TYPE="ntfs" 

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/drussrob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drussrob)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

sda1/boot/grub/menu.lst

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
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=81dd4f27-6fb8-4801-8a42-b919af7875b1

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
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		81dd4f27-6fb8-4801-8a42-b919af7875b1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=81dd4f27-6fb8-4801-8a42-b919af7875b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a3e2e957-6449-4383-931b-dc181546bfc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda1/boot

total 23788
drwxr-xr-x  3 root root    4096 2008-12-18 11:44 .
drwxr-xr-x 20 root root    4096 2008-12-10 16:08 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-24 12:55 grub
-rw-r--r--  1 root root 8193751 2008-12-10 16:08 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8194300 2008-12-18 11:44 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-24 12:55 .
drwxr-xr-x 3 root root   4096 2008-12-18 11:44 ..
-rw-r--r-- 1 root root    197 2008-12-10 15:29 default
-rw-r--r-- 1 root root     60 2008-12-10 15:29 device.map
-rw-r--r-- 1 root root   8108 2008-12-10 15:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-10 15:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-10 15:29 installed-version
-rw-r--r-- 1 root root   8712 2008-12-10 15:29 jfs_stage1_5
-rw-r--r-- 1 root root   4957 2008-12-24 12:55 menu.lst
-rw-r--r-- 1 root root   4957 2008-12-23 15:16 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-10 15:29 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-10 15:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-10 15:29 stage1
-rw-r--r-- 1 root root 121460 2008-12-10 15:29 stage2
-rw-r--r-- 1 root root   9556 2008-12-10 15:29 xfs_stage1_5

sdb2/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


StdErr Messages 

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
```

---

### Post by caljohnsmith on 2008-12-24
OK, I believe I see at least two problems that we should fix: first, your Windows XP sdb2 partition has a Vista boot sector instead of an XP one, and also since it looks like you might be booting your sdb drive instead of the sda drive (that's not a problem), the Windows entry in your menu.lst might be incorrect. Do you have your Windows XP Install CD? If you have that, please boot it, go to the "recovery console" and run:
```
fixboot
```
That should fix your Windows XP boot sector. Next, boot into Ubuntu and do:
```
gksudo gedit /boot/grub/menu.lst
```
And in addition to your current Windows entry, add the following one right after it:
```
title Windows XP (hd0)
root (hd0,1)
chainloader +1
```
Then reboot, try both XP entries in your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by DrussRob on 2008-12-24
I ran fixboot and all went well. 

Rebooted the machine and chose the first (my original) XP selection from Grub and I get the Error 12.

I then chose the second XP selection (one from your post) and it boots XP. It goes past the loading screen (the black screen with the knight rider looking thing moving across the bottom of the logo). It then goes to the first blue colored screen you see, I guess this is usually the welcome screen and then seems to stop. I doesn't lock up but simply stops there. I let it sit here for about 20 minutes to see if maybe it was dealing with the new partition size, but it just sat there with no activity.

---

### Post by caljohnsmith on 2008-12-24
OK, well at least we know you're booting the correct partition now. How about booting your Windows Install CD again, but this time run:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Windows again from Grub, and let me know if anything changes.

---

### Post by DrussRob on 2008-12-24
I ran chkdsk once and it took FORever. It found an error(s) and repaired and finished. I immediately ran it a second time and it found no errors and finished rather quickly (in comparison). I booted windows using the second newly added option and got the same results as before. Stopping at the blue background with the small xp logo sitting to the center right of the screen somewhat. I then tried booting into safe mode and got the same results.

So I rebooted into ubuntu and here I is. :)


btw: thank you for taking the time to go through this with me. I'm somewhat new to linux, but learning something new everyday.

---

### Post by caljohnsmith on 2008-12-24
[QUOTE=DrussRob]btw: thank you for taking the time to go through this with me. I'm somewhat new to linux, but learning something new everyday.[/QUOTE]
You're welcome, and I guess we're in the same boat, because I'm still learning new things every day too when it comes to computer stuff. :)

In your first post you mentioned that you deleted the second ext3 partition on the Windows drive and then expanded the third Windows partition to fill that space; so did you move the beginning of the XP partition in order to fill that space? Also, if Windows was originally on sdb3 (the 3rd partition), then the boot.ini file should have been using "partition(3)", so did you manually edit the boot.ini file since then to make it "partition(2)" now that Windows is on sdb2? "partition(2)" should be correct for your current setup, but I'm just wondering, did you modify any other Windows system files?

---

### Post by DrussRob on 2008-12-24
> 
In your first post you mentioned that you deleted the second ext3 partition on the Windows drive and then expanded the third Windows partition to fill that space; so did you move the beginning of the XP partition in order to fill that space?

I archived all data on the third (ntfs/xp) partition, then... **I just had a brain fart right now**, I believe I told you wrong in the first post. I archived the xp partition to the first partition, which is my virtualbox vdi partition, I then deleted both partitions 2 (ext3) and 3 (ntfs) and then reformatted the empty space left as ntfs, and then emptied the archive back into that newly created ntfs partition. Sorry about that.


> Also, if Windows was originally on sdb3 (the 3rd partition), then the boot.ini file should have been using "partition(3)", so did you manually edit the boot.ini file since then to make it "partition(2)" now that Windows is on sdb2? "partition(2)" should be correct for your current setup, but I'm just wondering, did you modify any other Windows system files?

I did change the boot.ini to reflect the new partition number, but nothing else was changed.

---

### Post by meierfra. on 2008-12-24
Try this (in a terminal in Ubuntu)

```
sudo xxd -s 440 -l 4 /dev/sdb DiskSignature
echo 00: 00000000 |sudo xxd -r -seek 440 - /dev/sdb
```

Then reboot and see whether you can boot in Windows.

Explanation:
When windows assigns drive letters it uses  the  Disk Signature and the start point (in sectors) to identify partitions. Since you moved the start point, Windows treats your Windows partition as a new partition and  assigns   the next available drive letter to it. So your Windows Partition is no longer the C:drive and booting fails.

You can  manually edit the Windows Registry to change the Drive Letter assignment, but it is much easier to convince Windows that the current drive letters are no longer valid  by erasing the Disk Signature.
Windows will then automatically assign new drive letters to all the NTFS partitions. Since your XP partition is your only NTFS partition, it will be the C:drive again and you should be able to boot.

The first line of code backups your current  disk signature. The second line erases it.

---

### Post by meierfra. on 2008-12-24
I just fixed a typo in my previous post. It needs to be /dev/sdb (not /dev/sda)

Thanks to caljohnsmith for noticing it.

---

### Post by DrussRob on 2008-12-24
I tried and it didn't really make a difference. But thank you so very much both of you for trying to help!

Honestly, now that I can access the partition, and I only need to use windows for this one proprietary program I use for work, aaand I can still access the drive from Ubuntu... I think I'm just going to grab the files for that prog off the partition in Ubuntu, back them up and just reinstall XP totally with the new partition layout.

Or, am I overlooking something that might keep me from doing so?

Once again, thank you ;)

---

### Post by meierfra. on 2008-12-25
> just reinstall XP totally with the new partition layout.

That's the fastest solution.


 > am I overlooking something that might keep me from doing so?

Windows will overwrite the MBR in /dev/sdb. So after you reinstalled windows you will have to do one of the following:


1)  Set your bios to boot from the Ubuntu drive and use

title              Windows XP
root               (hd1,1)
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


for your windows entry in menu.lst


2)  Reinstall grub to the MBR of sdb:


```
sudo grub
```
and at the grub prompt

```
device (hd0) /dev/sdb
device (hd1) /dev/sda
root (hd1,0)
setup (hd0)
```


I suggested  to use 1) since it keeps the two drives independent from each other. But if you can't switch the boot order in the bios, do 2).

---

### Post by DrussRob on 2008-12-25
I'll do that then ;)

The scientist in me really wants to keep plucking away at this and solve it without reinstalling, however, in all honesty I'm getting somewhat tired of coddling ms products. I've been "in computers" for years and years and finally I see some light at the end of the tunnel with the emergence of Ubuntu.

It's getting late now so I'll probably attack this again tomorrow afternoon after the kids rip into the presents. I'll check back in and let you know how it went.

Thanks for all your help and suggestions and MERRY CHRISTMAS! :)

---

### Post by DrussRob on 2008-12-29
All went well and I'm up and running. Although I did cheat a bit I guess... After I re-installed XP I used "super grub" to reinstate my grub menu ;)

Thanks for all the help guys!

AND HAPPY NEW YEAR!

---

