---
title: "[SOLVED] Adding Vista to Grub"
date: 2009-01-06
forum: General Help
---

### Post by jon419 on 2009-01-06
I would like to know what I should add to the Grub menu.lst file in order to get Windows Vista to boot from Grub.  Hoping someone can shed a little light on this issue for me:

Here is my fdisk -l:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77a3840f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38158   306504103+  83  Linux
/dev/sda2           38159       38913     6064537+   5  Extended
/dev/sda5           38159       38913     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS
```

The Windows Vista OS is on the Disk /dev/sdb which is the second SATA drive in my computer.

Thanks for any help you can provide.

---

### Post by caljohnsmith on 2009-01-06
How about first opening your menu.lst by doing:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try the Vista entry from your Grub menu, and let me know exactly what happens. If you get a "BOOTMGR missing" error, then please do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by blazemore on 2009-01-06
have you tried running
```
sudo update-grub
```

---

### Post by jon419 on 2009-01-06
I will try both when I get home tonight from work.  Thanks for the info.  Its been a few years since I have used a linux distro.  I am amazed at how far it has come.

---

### Post by jon419 on 2009-01-06
Ok, I added the following to my /boot/grub/menu.lst file:

```
title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

And I got the error BOOTMGR.EXE is missing.  Press CTRL-ALT-DEL to Restart.

Here is the output from that script you wanted me to run:

```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77a3840f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   613008269   306504103+  83  Linux
/dev/sda2       613008270   625137344     6064537+   5  Extended
/dev/sda5       613008333   625137344     6064506   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488394751   244196352    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f2191086-94fc-48fe-b06d-0214efe4c347" TYPE="ext3" 
/dev/sda5: UUID="ae3598b2-007d-4a5d-ad35-87bebe9a36dc" TYPE="swap" 
/dev/sdb1: UUID="A2C4CFBBC4CF9049" TYPE="ntfs" 

=============================== "mount" output: ===============================

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
gvfs-fuse-daemon on /home/jon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jon)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jon)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f2191086-94fc-48fe-b06d-0214efe4c347 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f2191086-94fc-48fe-b06d-0214efe4c347

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
uuid		f2191086-94fc-48fe-b06d-0214efe4c347
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2191086-94fc-48fe-b06d-0214efe4c347 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2191086-94fc-48fe-b06d-0214efe4c347
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2191086-94fc-48fe-b06d-0214efe4c347 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f2191086-94fc-48fe-b06d-0214efe4c347
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2191086-94fc-48fe-b06d-0214efe4c347 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f2191086-94fc-48fe-b06d-0214efe4c347
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2191086-94fc-48fe-b06d-0214efe4c347 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f2191086-94fc-48fe-b06d-0214efe4c347
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f2191086-94fc-48fe-b06d-0214efe4c347 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ae3598b2-007d-4a5d-ad35-87bebe9a36dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23772
drwxr-xr-x  3 root root    4096 2009-01-03 14:15 .
drwxr-xr-x 20 root root    4096 2009-01-03 14:14 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-06 18:40 grub
-rw-r--r--  1 root root 8185761 2009-01-03 14:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8186637 2009-01-03 14:15 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-06 18:40 .
drwxr-xr-x 3 root root   4096 2009-01-03 14:15 ..
-rw-r--r-- 1 root root    197 2009-01-03 07:59 default
-rw-r--r-- 1 root root     30 2009-01-03 07:59 device.map
-rw-r--r-- 1 root root   8108 2009-01-03 07:59 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-03 07:59 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 07:59 installed-version
-rw-r--r-- 1 root root   8712 2009-01-03 07:59 jfs_stage1_5
-rw-r--r-- 1 root root   4905 2009-01-06 18:40 menu.lst
-rw-r--r-- 1 root root   4792 2009-01-03 16:37 menu.lst~
-rw-r--r-- 1 root root   4792 2009-01-03 16:38 menu.lst.bak
-rw-r--r-- 1 root root   7352 2009-01-03 07:59 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-03 07:59 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 07:59 stage1
-rw-r--r-- 1 root root 121460 2009-01-03 07:59 stage2
-rw-r--r-- 1 root root   9556 2009-01-03 07:59 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
```

---

### Post by caljohnsmith on 2009-01-06
I was afraid you would get a bootmgr missing error, and it looks like you are indeed missing your Vista boot files. Do you have your Vista Install CD? You will need that in the steps needed to fix Vista. How about following [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") on how to replace Vista's missing boot files and configure Vista to boot again. You can follow steps 1 and 2, skip step 3 since your menu.lst entry for Vista is OK, do step 4, and then skip step 5 since your Vista boot sector appears to be OK. Let me know how that goes or if you run into problems, and we can work from there if you want.

---

### Post by jon419 on 2009-01-06
Thanks caljohnsmith, everything is working beautifully now!  I appreciate the help more than you can imagine.

---

### Post by caljohnsmith on 2009-01-06
> **jon419 said:**
> Thanks caljohnsmith, everything is working beautifully now!  I appreciate the help more than you can imagine.
You're certainly welcome, but all the credit really goes to forum member meierfra for fixing your problem; he's the author of the script you ran, and he's also wrote that tutorial you followed. I'm glad that you didn't run into any problems and have Vista booting OK; cheers and enjoy Ubuntu and Vista. :)

---

