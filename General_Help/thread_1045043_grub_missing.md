---
title: "grub missing"
date: 2009-01-20
forum: General Help
---

### Post by naitsabes on 2009-01-20
So I've been using ubuntu for a while now, and had to install xp the other day so that I can run solidworks (I'd rather not run it in a VM) so I have it set to dualboot.  The only problem is that ever since the xp install, it boots straight into windows without even going to grub first. I have a feeling it overwrote the mbr.  I ran grub > setup (hd0,0) and it didn't fix the problem even with a little coaxing.  

Thanks,
naitsabes

(02:13) Edit 1: Oh, and I've never had this problem because the last time I had windows dualbooting was in 2006 when I already had it installed, and then installed ubuntu/grub on top of it.

---

### Post by kokkus on 2009-01-20
WIndows overwrites the grub coz they always want to b #1.
OK there are a few ways u can solve this problem.
In windows, download the free supergrub program from download.com and use this tool to reset grub.
Or u can also boot the ubuntu CD and in live mode install GRUBEditor to reset and manage grub.
Good Luck:)

---

### Post by naitsabes on 2009-01-20
Alright, thanks kokkus.  I'll give that a try and let you know the results.

---

### Post by caljohnsmith on 2009-01-20
Using Super Grub should work, but if you want to do it from the Grub command line like you were trying to do, I think the only problem is that you need to run "setup (hd0)" instead of "setup (hd0,0)" after doing the "root" command. Using "setup (hd0,0)" will install Grub to the boot sector of sda1, so I hope that isn't your Windows partition. If it is, you won't be able to mount or boot Windows until you fix the boot sector. Let me know if Windows is on sda1, and I can help you fix the boot sector if you want.

---

### Post by naitsabes on 2009-01-20
I tried both methods.  The superbrub method led me to a windows error, which I don't really want to deal with because it doesn't hinder windows from booting.  the grub command line method yields "Error 17: Cannot mount selected partition"

windows is on sda2, ubuntu is on sda1, and the swap is on sda5 under the extended which is sda3

---

### Post by caljohnsmith on 2009-01-20
I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop on the Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by naitsabes on 2009-01-20
Okay, here it is:

```
============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda1 
                       and looks at sector 119423039 of the same hard drive 
                       for the stage2 file and on partition #1 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu jaunty (development branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000400
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       292968736 sectors, but according to the info from 
                       fdisk, it has 312576000 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdc1 already mounted or sdc1 busy
mount: according to mtab, /dev/sdc1 is mounted on /cdrom

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f2ce3df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   125885339    62942638+  83  Linux
/dev/sda2   *   125889120   187321679    30716280    7  HPFS/NTFS
/dev/sda3       187333965   195366464     4016250    5  Extended
/dev/sda5       187334028   195366464     4016218+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 2 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe566192b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   312578047   156288000    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 1052 MB, 1052770304 bytes
2 heads, 63 sectors/track, 16318 cylinders, total 2056192 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x002a97fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     2056191     1028080    b  W95 FAT32

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="Ubuntu" UUID="7315c62f-dc7a-4930-99f5-574b1064fca2" TYPE="ext3" 
/dev/sda2: UUID="E0E8797EE87953AE" TYPE="ntfs" 
/dev/sda5: UUID="8ad55c61-1a61-4edd-8bb7-6c9e83881c9c" TYPE="swap" 
/dev/sdb1: UUID="3E4049A6404965AD" LABEL="SNGDBX" TYPE="ntfs" 
/dev/sdc1: UUID="FCC6-4106" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-3-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-3-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/Ubuntu type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color green/black green/black

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7315c62f-dc7a-4930-99f5-574b1064fca2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7315c62f-dc7a-4930-99f5-574b1064fca2

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid        7315c62f-dc7a-4930-99f5-574b1064fca2
kernel        /boot/vmlinuz-2.6.28-4-generic root=UUID=7315c62f-dc7a-4930-99f5-574b1064fca2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-4-generic
quiet

title         Windows XP
root          (hd0,1)

title        Ubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid        7315c62f-dc7a-4930-99f5-574b1064fca2
kernel        /boot/vmlinuz-2.6.28-4-generic root=UUID=7315c62f-dc7a-4930-99f5-574b1064fca2 ro  single
initrd        /boot/initrd.img-2.6.28-4-generic

title        Ubuntu jaunty (development branch), memtest86+
uuid        7315c62f-dc7a-4930-99f5-574b1064fca2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7315c62f-dc7a-4930-99f5-574b1064fca2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8ad55c61-1a61-4edd-8bb7-6c9e83881c9c none            swap    sw              0       0

================================== sda1/boot: ==================================

total 25028
drwxr-xr-x  3 root root    4096 2009-01-17 05:40 .
drwxr-xr-x 21 root root    4096 2009-01-18 19:34 ..
-rw-r--r--  1 root root  535241 2008-12-13 00:28 abi-2.6.28-3-generic
-rw-r--r--  1 root root  529145 2009-01-16 23:39 abi-2.6.28-4-generic
-rw-r--r--  1 root root   96365 2008-12-13 00:28 config-2.6.28-3-generic
-rw-r--r--  1 root root   96567 2009-01-16 23:39 config-2.6.28-4-generic
drwxr-xr-x  2 root root    4096 2009-01-17 05:40 grub
-rw-r--r--  1 root root 8226226 2009-01-16 01:09 initrd.img-2.6.28-3-generic
-rw-r--r--  1 root root 7592590 2009-01-17 05:40 initrd.img-2.6.28-4-generic
-rw-r--r--  1 root root  124152 2008-11-13 10:46 memtest86+.bin
-rw-r--r--  1 root root 1101681 2008-12-13 00:28 System.map-2.6.28-3-generic
-rw-r--r--  1 root root 1433587 2009-01-16 23:39 System.map-2.6.28-4-generic
-rw-r--r--  1 root root    1073 2008-12-13 00:30 vmcoreinfo-2.6.28-3-generic
-rw-r--r--  1 root root    1073 2009-01-16 23:40 vmcoreinfo-2.6.28-4-generic
-rw-r--r--  1 root root 2388784 2008-12-12 19:28 vmlinuz-2.6.28-3-generic
-rw-r--r--  1 root root 3400432 2009-01-16 23:39 vmlinuz-2.6.28-4-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-17 05:40 .
drwxr-xr-x 3 root root   4096 2009-01-17 05:40 ..
-rw-r--r-- 1 root root    197 2009-01-16 01:09 default
-rw-r--r-- 1 root root     45 2009-01-16 01:09 device.map
-rw-r--r-- 1 root root   8108 2009-01-16 01:09 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-16 01:09 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-16 01:09 installed-version
-rw-r--r-- 1 root root   8712 2009-01-16 01:09 jfs_stage1_5
-rw-r--r-- 1 root root   4659 2009-01-18 22:08 menu.lst
-rw-r--r-- 1 root root   5134 2009-01-17 05:40 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-16 01:09 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-16 01:09 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-16 01:09 stage1
-rw-r--r-- 1 root root 121472 2009-01-16 01:09 stage2
-rw-r--r-- 1 root root   9556 2009-01-16 01:09 xfs_stage1_5

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
F:\ubnldr.mbr="UNetbootin" 

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-20
So which drive are you booting on start up? Do you boot the Ubuntu/XP sda drive or the Vista sdb drive? Also, is your Ubuntu Jaunty partition using the new ext4 file system? It looks like it uses ext3 but I'm not familiar with using ext4 yet. How about copy/pasting your terminal session so I can see the output of all the following commands: 
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

---

### Post by naitsabes on 2009-01-20
I'm trying to boot the Ubuntu drive, which is sda1 and is ext3.  I'm not sure why Vista is on there, because I don't have vista running on anything.  It might be because of the original nature of my second drive.  Anyways, here is the output that you requested:

```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

---

### Post by caljohnsmith on 2009-01-20
It looks like Grub installed OK to the MBR (Master Boot Record) of your sda drive, so if you reboot and make sure your BIOS is set to boot the sda drive, you should be able to boot into Ubuntu. Let me know how that goes.

---

### Post by naitsabes on 2009-01-20
Yes I restarted and was able to get to the grub menu and log into ubuntu.  Thank you all for your help. :)

---

