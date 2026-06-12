---
title: "Windows shows loading bar, then reboots"
date: 2008-12-28
forum: General Help
---

### Post by dagwaging on 2008-12-28
So all of a sudden trying to boot into Windows from GRUB causes windows to appear to boot normally, then suddenly reboot the computer and return to GRUB. Basically the Windows text and scrolling progress bar appear, stay for about seven seconds, and then the computer reboots, the BIOS page is shown, and GRUB comes back up. I have a single SSD with a SATA connector and 3 partitions:

```

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0356eef1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2550    10241437+  83  Linux
/dev/sda3   *        2551        3895    10803712+   7  HPFS/NTFS

```

The first partition is the Windows one, followed by Linux, then my file storage. There's the fdisk -l and here's the part of my Menu.lst:

```

title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I have a feeling it's something really stupid and obvious that I'm missing here. I recently disconnected and reconnected my SSD. I may have connected it to a different SATA port than before, yet I can boot into Ubuntu 8.10 perfectly fine. Any idea if this caused it?

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by dagwaging on 2008-12-28
Heh, you treat me like I don't know what a terminal is. :P
Anyway, I don't see why I would need to use a Live CD, especially since I have no CD drive.

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 40965750.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders, total 62586880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0356eef1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406    7  HPFS/NTFS
/dev/sda2        20482875    40965749    10241437+  83  Linux
/dev/sda3   *    40965750    62573174    10803712+   7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="86A483E0A483D15B" TYPE="ntfs" 
/dev/sda2: LABEL="Linux" UUID="4afde52c-d838-4e66-b32c-204c85648592" TYPE="ext3" 
/dev/sda3: UUID="0DAB2BC9566159E8" LABEL="Files" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zane)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect



=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4afde52c-d838-4e66-b32c-204c85648592 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4afde52c-d838-4e66-b32c-204c85648592

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
uuid		4afde52c-d838-4e66-b32c-204c85648592
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4afde52c-d838-4e66-b32c-204c85648592 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4afde52c-d838-4e66-b32c-204c85648592
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4afde52c-d838-4e66-b32c-204c85648592 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4afde52c-d838-4e66-b32c-204c85648592
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4afde52c-d838-4e66-b32c-204c85648592 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2008-12-26 23:06 .
drwxr-xr-x 20 root root    4096 2008-12-26 23:05 ..
-rw-r--r--  1 root root  507665 2008-10-24 04:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 04:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-28 18:17 grub
-rw-r--r--  1 root root 8179945 2008-12-26 23:05 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 04:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 04:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 04:29 vmlinuz-2.6.27-7-generic

=============================== sda2/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2008-12-28 18:17 .
drwxr-xr-x 3 root root   4096 2008-12-26 23:06 ..
-rw-r--r-- 1 root root    197 2008-12-26 23:06 default
-rw-r--r-- 1 root root     15 2008-12-26 23:06 device.map
-rw-r--r-- 1 root root   8108 2008-12-26 23:06 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-26 23:06 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 23:06 installed-version
-rw-r--r-- 1 root root   8712 2008-12-26 23:06 jfs_stage1_5
-rw-r--r-- 1 root root   4090 2008-12-27 13:15 menu_edit.lst
-rw-r--r-- 1 root root   4615 2008-12-28 18:17 menu.lst
-rw-r--r-- 1 root root   4615 2008-12-28 17:58 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-26 23:06 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-26 23:06 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-26 23:06 stage1
-rw-r--r-- 1 root root 121460 2008-12-26 23:06 stage2
-rw-r--r-- 1 root root   9556 2008-12-26 23:06 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2008-12-28
OK, so according to according to the script results, everything appears configured OK to boot Windows from Grub, so I think you have a Windows problem and not a Grub problem at this point. If you have your Windows Install CD, I would boot that, go to the "recovery console" and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then reboot and see if you get any further booting Windows. Let me know how it goes.

---

### Post by dagwaging on 2008-12-28
> I don't see why I would need to use a Live CD, especially since I have **no CD drive.** ...
Okay, so I found an old IDE CD drive, hooked it up, popped my XP Setup disk in, and ran chkdsk. No dice. Same thing happened.

---

