---
title: "Update bios =&gt; grub error 13"
date: 2009-01-10
forum: General Help
---

### Post by p1ur on 2009-01-10
Hi
I hope someone can help me :-)
I know there is a lot about grub, but I don't know what is the right thing to do for me.
I have en pc with 2 HD, 
on the first I have Windos Vista
on the second Ubuntu.
I have just updated my bios, and now Windows Vista wont start :-(
I get the error:
Error 13: Invalid or unsupported executable format.

Luckily Ubuntu works :-)

But what would a wise man do now?

Thanx in advance
p1ur

---

### Post by caljohnsmith on 2009-01-10
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by p1ur on 2009-01-10
Here is text from the file results.txt.
Some text is in Danish, I will translate if necessary 
```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
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

Disk /dev/sda: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders, i alt 488397168 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0x28901840

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *        2048   446439415   223218684    7  HPFS/NTFS
/dev/sda2       446439424   488392064    20976320+   f  w95 udvidet (LBA)
/dev/sda5       446439487   488392064    20976289    b  W95 FAT32

sfdisk -V /dev/sda:

Advarsel: udvidet partition starter ikke på en cylindergrænse.
DOS og Linux vil opfatte indholdet forskelligt.
Advarsel: partition 1 slutter ikke på en cylindergrænse

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 10.0 Gb, 10005037056 byte
255 heads, 63 sectors/track, 1216 cylinders, i alt 19541088 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0xae2fae2f

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *          63    18603269     9301603+  83  Linux
/dev/sdb2        18603270    19535039      465885    5  Udvidet
/dev/sdb5        18603333    19535039      465853+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: O.k.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: kunne ikke åbne /dev/sdc for læsning

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: kunne ikke åbne /dev/sdd for læsning

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: kunne ikke åbne /dev/sde for læsning

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6AC0EF0FC0EEDFF5" LABEL="BOOT" TYPE="ntfs" 
/dev/sda5: LABEL="RECOVER" UUID="1445-D758" TYPE="vfat" 
/dev/sdb1: UUID="59084193-0fd1-45f1-bf4c-7b0a94ff267f" TYPE="ext3" 
/dev/sdb5: UUID="7c19bf38-01db-48c9-a8fc-323b61c64c47" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/petur/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=petur)
/dev/sda1 on /media/BOOT type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
tmpfs on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=0755)

================================== sda1/Boot: ==================================

totalt 760
drwxrwxrwx 1 root root   4096 2008-10-07 22:41 .
drwxrwxrwx 1 root root  12288 2009-01-10 17:19 ..
-rwxrwxrwx 1 root root  24576 2009-01-10 17:31 BCD
-rwxrwxrwx 1 root root 262144 2009-01-10 17:27 BCD.LOG
-rwxrwxrwx 2 root root      0 2006-12-13 04:25 BCD.LOG1
-rwxrwxrwx 2 root root      0 2006-12-13 04:25 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2007-05-10 16:49 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-07 22:41 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-07 22:41 da-DK
drwxrwxrwx 1 root root      0 2008-10-07 22:41 de-DE
drwxrwxrwx 1 root root      0 2008-10-07 22:41 el-GR
drwxrwxrwx 1 root root      0 2008-10-07 22:41 en-US
drwxrwxrwx 1 root root      0 2008-10-07 22:41 es-ES
drwxrwxrwx 1 root root      0 2008-10-07 22:41 fi-FI
drwxrwxrwx 1 root root      0 2008-10-07 22:41 Fonts
drwxrwxrwx 1 root root      0 2008-10-07 22:41 fr-FR
drwxrwxrwx 1 root root      0 2008-10-07 22:41 hu-HU
drwxrwxrwx 1 root root      0 2008-10-07 22:41 it-IT
drwxrwxrwx 1 root root      0 2008-10-07 22:41 ja-JP
drwxrwxrwx 1 root root      0 2008-10-07 22:41 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 08:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-07 22:41 nb-NO
drwxrwxrwx 1 root root      0 2008-10-07 22:41 nl-NL
drwxrwxrwx 1 root root      0 2008-10-07 22:41 pl-PL
drwxrwxrwx 1 root root      0 2008-10-07 22:41 pt-BR
drwxrwxrwx 1 root root      0 2008-10-07 22:41 pt-PT
drwxrwxrwx 1 root root      0 2008-10-07 22:41 ru-RU
drwxrwxrwx 1 root root      0 2008-10-07 22:41 sv-SE
drwxrwxrwx 1 root root      0 2008-10-07 22:41 tr-TR
drwxrwxrwx 1 root root      0 2008-10-07 22:41 zh-CN
drwxrwxrwx 1 root root      0 2008-10-07 22:41 zh-HK
drwxrwxrwx 1 root root      0 2008-10-07 22:41 zh-TW

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
# kopt=root=UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=59084193-0fd1-45f1-bf4c-7b0a94ff267f

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
uuid		59084193-0fd1-45f1-bf4c-7b0a94ff267f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		59084193-0fd1-45f1-bf4c-7b0a94ff267f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		59084193-0fd1-45f1-bf4c-7b0a94ff267f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		59084193-0fd1-45f1-bf4c-7b0a94ff267f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		59084193-0fd1-45f1-bf4c-7b0a94ff267f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=59084193-0fd1-45f1-bf4c-7b0a94ff267f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=7c19bf38-01db-48c9-a8fc-323b61c64c47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

totalt 23764
drwxr-xr-x  3 root root    4096 2009-01-10 20:12 .
drwxr-xr-x 20 root root    4096 2009-01-10 20:10 ..
-rw-r--r--  1 root root  507665 2008-11-04 22:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-21 00:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 22:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-21 00:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-10 20:10 grub
-rw-r--r--  1 root root 8181280 2009-01-10 20:10 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8181156 2009-01-10 20:12 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 22:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-21 00:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 22:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-21 00:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 22:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-21 00:46 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

totalt 224
drwxr-xr-x 2 root root   4096 2009-01-10 20:10 .
drwxr-xr-x 3 root root   4096 2009-01-10 20:12 ..
-rw-r--r-- 1 root root    197 2009-01-10 18:22 default
-rw-r--r-- 1 root root     30 2009-01-10 18:22 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 18:22 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 18:22 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 18:22 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 18:22 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2009-01-10 20:10 menu.lst
-rw-r--r-- 1 root root   5017 2009-01-10 20:10 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-10 18:22 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 18:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 18:22 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 18:22 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 18:22 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: kunne ikke åbne /dev/sdc for læsning
/dev/sdd: No medium found

sfdisk: kunne ikke åbne /dev/sdd for læsning
/dev/sde: No medium found

sfdisk: kunne ikke åbne /dev/sde for læsning
Advarsel: udvidet partition starter ikke på en cylindergrænse.
DOS og Linux vil opfatte indholdet forskelligt.
Advarsel: udvidet partition starter ikke på en cylindergrænse.
DOS og Linux vil opfatte indholdet forskelligt.
Advarsel: udvidet partition starter ikke på en cylindergrænse.
DOS og Linux vil opfatte indholdet forskelligt.
```

---

### Post by p1ur on 2009-01-10
Some (sort of) translation:

Advarsel: udvidet partition starter ikke på en cylindergrænse. :
Warning: Extended partition does not start on a cylinder border 

DOS og Linux vil opfatte indholdet forskelligt.
DOS and Linux will perceive content differently

Advarsel: partition 1 slutter ikke på en cylindergrænse
Warning. Partition 1 does not end on a cylinder border

---

### Post by caljohnsmith on 2009-01-10
I think I see what the issue might be; you have Grub installed to the MBR (Master Boot Record) of both your drives, so you could boot either drive on start up to get the Grub menu. But currently your Grub menu is configured to boot Windows only if you are booting the the Windows drive on start up. If you instead boot your Ubuntu drive, you can still boot Ubuntu OK since Grub now uses UUIDs to identify the partitions, but your Windows entry won't work like what you are currently experiencing. So the bottom line is it looks like you are booting the Ubuntu drive on start up now, which is actually good, so how about opening up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the Windows entry at the bottom to:
```
title       Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And then if all goes well, I think you should be able to boot into Windows. How about trying that and let me know how it goes.

---

### Post by p1ur on 2009-01-10
Thanx, it works :P 
caljohnsmith you're the man :o

Just a question:
If I remove my (reserve)HD with Ubuntu(?HD1?), will the main HD(?HD0?) still work?

P1ur

P.S. Really nice Avatar :-)

---

### Post by caljohnsmith on 2009-01-10
> **p1ur said:**
> 
Just a question:
If I remove my (reserve)HD with Ubuntu(?HD1?), will the main HD(?HD0?) still work?

That's a really good question, because currently your internal Windows drive won't boot if you remove the Ubuntu drive; you will get a Grub error 21 or something along those lines. So it would make sense to restore a Windows MBR to your internal Windows drive so that you can boot your Windows drive even with your Ubuntu drive disconnected. You can do that with:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then you should be all set. Let me know if you run into any problems though. :)

---

