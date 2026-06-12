---
title: "Ubuntu now on secondary drive"
date: 2009-01-21
forum: General Help
---

### Post by aznewsh on 2009-01-21
I installed a new fast primary HD primarily for gaming so this now has a new install of XP on it. I did however keep my old drive as a secondary drive so i could easily get at my old data in the windows partition which will eventually be storage only. The other partition on that drive is where my ubuntu install resides and since the grub is also on this secondary drive, how can I boot into Ubuntu without going into bios and changing the primary drives around - I guess essentially what i am asking is how to move the grub from the secondary drive to the new primary drive and what will need editing?

---

### Post by caljohnsmith on 2009-01-21
If you were to set your BIOS to boot the Ubuntu drive, you could simply add an entry in your Grub menu to boot Windows on the other drive. That way you wouldn't have to switch your BIOS every time you wanted to boot the other OS. But if you want to install Grub to your Windows drive, keep in mind that will make your drives dependent on each other for booting, so if anything goes wrong with either drive, most likely you won't be able to boot into either Windows or Ubuntu. Either way you decide, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your current setup.

---

### Post by aznewsh on 2009-01-22
Thanks for the fast response...

I think looking at it that way, there really is no reason to not let the grub stay where it is and make that the primary drive.

So assuming I did this how would I add the new windows to the grub menu?

I will post the detail you requested when I get home.

---

### Post by aznewsh on 2009-01-22
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
00000000  68 62 69 6e 00 40 6a 01  00 10 00 00 00 00 00 00  |hbin.@j.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  80 ff ff ff 6e 6b 20 00  70 11 c1 57 59 f4 c6 01  |....nk .p..WY...|
00000030  00 00 00 00 e8 b1 6b 00  00 00 00 00 00 00 00 00  |......k.........|
00000040  ff ff ff ff ff ff ff ff  01 00 00 00 d0 51 6a 01  |.............Qj.|
00000050  70 59 f7 00 ff ff ff ff  00 00 00 00 00 00 00 00  |pY..............|
00000060  28 00 00 00 04 00 00 00  e0 97 78 00 2f 00 00 00  |(.........x./...|
00000070  46 45 41 54 55 52 45 5f  44 49 53 41 42 4c 45 5f  |FEATURE_DISABLE_|
00000080  55 4e 49 43 4f 44 45 5f  48 41 4e 44 4c 45 5f 43  |UNICODE_HANDLE_C|
00000090  4c 4f 53 49 4e 47 5f 43  41 4c 4c 42 41 43 4b 00  |LOSING_CALLBACK.|
000000a0  80 ff ff ff 6e 6b 20 00  70 11 c1 57 59 f4 c6 01  |....nk .p..WY...|
000000b0  00 00 00 00 e8 b1 6b 00  00 00 00 00 00 00 00 00  |......k.........|
000000c0  ff ff ff ff ff ff ff ff  03 00 00 00 b0 3f c1 00  |.............?..|
000000d0  70 59 f7 00 ff ff ff ff  00 00 00 00 00 00 00 00  |pY..............|
000000e0  18 00 00 00 04 00 00 00  b0 3a 6a 01 2f 00 00 00  |.........:j./...|
000000f0  46 45 41 54 55 52 45 5f  45 4e 41 42 4c 45 5f 53  |FEATURE_ENABLE_S|
00000100  43 52 49 50 54 5f 50 41  53 54 45 5f 55 52 4c 41  |CRIPT_PASTE_URLA|
00000110  43 54 49 4f 4e 5f 49 46  5f 50 52 4f 4d 50 54 01  |CTION_IF_PROMPT.|
00000120  d8 ff ff ff 76 6b 0a 00  04 00 00 80 01 00 00 00  |....vk..........|
00000130  04 00 00 00 01 00 78 00  64 65 76 65 6e 76 2e 65  |......x.devenv.e|
00000140  78 65 00 00 76 6b 04 00  d8 ff ff ff 76 6b 0c 00  |xe..vk......vk..|
00000150  04 00 00 80 01 00 00 00  04 00 00 00 01 00 78 00  |..............x.|
00000160  64 65 78 70 6c 6f 72 65  2e 65 78 65 d0 a5 78 00  |dexplore.exe..x.|
00000170  d8 ff ff ff 76 6b 0c 00  04 00 00 80 01 00 00 00  |....vk..........|
00000180  04 00 00 00 01 00 78 00  68 65 6c 70 70 61 6e 65  |......x.helppane|
00000190  2e 65 78 65 e0 a7 78 00  90 ff ff ff 6e 6b 20 00  |.exe..x.....nk .|
000001a0  70 11 c1 57 59 f4 c6 01  00 00 00 00 e8 b1 6b 00  |p..WY.........k.|
000001b0  00 00 00 00 00 00 00 00  ff ff ff ff ff ff ff ff  |................|
000001c0  01 00 00 00 b0 5d 6a 01  70 59 f7 00 ff ff ff ff  |.....]j.pY......|
000001d0  00 00 00 00 00 00 00 00  16 00 00 00 04 00 00 00  |................|
000001e0  48 aa 78 00 19 00 00 00  46 45 41 54 55 52 45 5f  |H.x.....FEATURE_|
000001f0  49 47 4e 4f 52 45 5f 58  4d 4c 5f 50 52 4f 4c 4f  |IGNORE_XML_PROLO|
00000200  47 ab 78 00 80 ab 78 00  d8 ff ff ff 76 6b 0b 00  |G.x...x.....vk..|
00000210  04 00 00 80 00 00 00 00  04 00 00 00 01 00 78 00  |..............x.|
00000220  6d 73 69 65 78 65 63 2e  65 78 65 01 68 c5 8a 00  |msiexec.exe.h...|
00000230  90 ff ff ff 6e 6b 20 00  70 11 c1 57 59 f4 c6 01  |....nk .p..WY...|
00000240  00 00 00 00 e8 b1 6b 00  00 00 00 00 00 00 00 00  |......k.........|
00000250  ff ff ff ff ff ff ff ff  01 00 00 00 f0 5f 6a 01  |............._j.|
00000260  70 59 f7 00 ff ff ff ff  00 00 00 00 00 00 00 00  |pY..............|
00000270  18 00 00 00 04 00 00 00  01 00 00 00 1e 00 00 00  |................|
00000280  46 45 41 54 55 52 45 5f  49 4e 54 45 52 4e 45 54  |FEATURE_INTERNET|
00000290  5f 53 48 45 4c 4c 5f 46  4f 4c 44 45 52 53 10 00  |_SHELL_FOLDERS..|
000002a0  d8 ff ff ff 76 6b 0c 00  04 00 00 80 00 00 00 00  |....vk..........|
000002b0  04 00 00 00 01 00 72 61  69 65 78 70 6c 6f 72 65  |......raiexplore|
000002c0  2e 65 78 65 76 6b 10 00  90 ff ff ff 6e 6b 20 00  |.exevk......nk .|
000002d0  70 11 c1 57 59 f4 c6 01  00 00 00 00 e8 b1 6b 00  |p..WY.........k.|
000002e0  00 00 00 00 00 00 00 00  ff ff ff ff ff ff ff ff  |................|
000002f0  01 00 00 00 f8 5f 6a 01  70 59 f7 00 ff ff ff ff  |....._j.pY......|
00000300  00 00 00 00 00 00 00 00  18 00 00 00 04 00 00 00  |................|
00000310  20 00 00 00 19 00 00 00  46 45 41 54 55 52 45 5f  | .......FEATURE_|
00000320  4c 45 47 41 43 59 5f 44  49 53 50 50 41 52 41 4d  |LEGACY_DISPPARAM|
00000330  53 00 00 00 6e 6b 20 00  d8 ff ff ff 76 6b 0c 00  |S...nk .....vk..|
00000340  04 00 00 80 00 00 00 00  04 00 00 00 01 00 00 00  |................|
00000350  68 65 6c 70 70 61 6e 65  2e 65 78 65 e8 ef 75 00  |helppane.exe..u.|
00000360  d8 ff ff ff 76 6b 09 00  04 00 00 80 01 00 00 00  |....vk..........|
00000370  04 00 00 00 01 00 00 00  6d 73 69 6d 6e 2e 65 78  |........msimn.ex|
00000380  65 43 54 49 56 45 58 5f  d8 ff ff ff 76 6b 0b 00  |eCTIVEX_....vk..|
00000390  04 00 00 80 01 00 00 00  04 00 00 00 01 00 d7 4e  |...............N|
000003a0  77 69 6e 6d 61 69 6c 2e  65 78 65 00 f1 58 d7 4e  |winmail.exe..X.N|
000003b0  90 ff ff ff 6e 6b 20 00  70 11 c1 57 59 f4 c6 01  |....nk .p..WY...|
000003c0  00 00 00 00 e8 b1 6b 00  00 00 00 00 00 00 00 00  |......k.........|
000003d0  ff ff ff ff ff ff ff ff  03 00 00 00 18 5a c6 00  |.............Z..|
000003e0  70 59 f7 00 ff ff ff ff  00 00 00 00 00 00 00 00  |pY..............|
000003f0  16 00 00 00 04 00 00 00  5c 00 57 00 1c 00 00 00  |........\.W.....|
00000400
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       227075000 sectors, but according to the info from 
                       fdisk, it has 232524810 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab5dab5d

/dev/sda1     *           63  293,025,599  293,025,537   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1c6f1c6

/dev/sdb1     *           63  232,524,872  232,524,810   7 HPFS/NTFS
/dev/sdb2        232,540,875  586,099,394  353,558,520   5 Extended
/dev/sdb5        232,540,938  573,954,254  341,413,317  83 Linux
/dev/sdb6        573,954,318  586,099,394   12,145,077  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C61C50791C506709" TYPE="ntfs" 
/dev/sdb1: UUID="3688B81188B7CD9D" TYPE="ntfs" 
/dev/sdb5: UUID="a09edbbc-28b4-4738-9b65-daee697c84f1" TYPE="ext3" 
/dev/sdb6: UUID="f6def011-910b-4efb-a228-43e2748a0a64" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/gn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gn)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=gn)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb5/boot/grub/menu.lst: ===========================

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
default		4

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
# kopt=root=UUID=a09edbbc-28b4-4738-9b65-daee697c84f1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a09edbbc-28b4-4738-9b65-daee697c84f1

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
uuid		a09edbbc-28b4-4738-9b65-daee697c84f1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a09edbbc-28b4-4738-9b65-daee697c84f1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a09edbbc-28b4-4738-9b65-daee697c84f1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a09edbbc-28b4-4738-9b65-daee697c84f1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		a09edbbc-28b4-4738-9b65-daee697c84f1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a09edbbc-28b4-4738-9b65-daee697c84f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f6def011-910b-4efb-a228-43e2748a0a64 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 11976
drwxr-xr-x  3 root root    4096 2008-12-21 07:39 .
drwxr-xr-x 20 root root    4096 2008-12-02 16:54 ..
-rw-r--r--  1 root root  507665 2008-11-20 16:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-20 16:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-02 16:54 grub
-rw-r--r--  1 root root 8205703 2008-12-21 07:39 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-20 16:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-20 16:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244304 2008-11-20 16:46 vmlinuz-2.6.27-9-generic

=============================== sdb5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-02 16:54 .
drwxr-xr-x 3 root root   4096 2008-12-21 07:39 ..
-rw-r--r-- 1 root root    197 2008-11-08 07:57 default
-rw-r--r-- 1 root root     15 2008-11-08 07:57 device.map
-rw-r--r-- 1 root root   8108 2008-11-08 07:57 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-08 07:57 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-08 07:57 installed-version
-rw-r--r-- 1 root root   8712 2008-11-08 07:57 jfs_stage1_5
-rw-r--r-- 1 root root   4621 2008-12-02 16:54 menu.lst
-rw-r--r-- 1 root root   4621 2008-12-02 16:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-08 07:57 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-08 07:57 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-08 07:57 stage1
-rw-r--r-- 1 root root 121460 2008-11-08 07:57 stage2
-rw-r--r-- 1 root root   9556 2008-11-08 07:57 xfs_stage1_5

=================== sdb5: Location  of files loaded by Grub: ===================


 260.8GB: boot/grub/menu.lst
 260.8GB: boot/grub/stage2
 260.8GB: boot/initrd.img-2.6.27-9-generic
 260.7GB: boot/vmlinuz-2.6.27-9-generic
 260.8GB: initrd.img
 260.7GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-22
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Windows entry with:
```
title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Then reboot, and see if you can boot Windows on your 150 GB sda drive from your Grub menu. Let me know how that goes or if you run into problems.

---

### Post by Yashiro on 2009-01-22
Just boot from your old drive and alter grub to point to the new Windows drive in /boot/grub/menu.lst (which is on the sd5/ext3).

title		Microsoft Windows XP Professional
root		**(hd0,0)**
savedefault
makeactive
chainloader	+1

Edit *that* to point at the right partition. **(hd1,0)** probably.

---

### Post by aznewsh on 2009-01-22
Caljohnsmith - That worked perfectly - thank you

Yashiro - since the first response worked I didn't need to try your solution but appreciate your response.


Thanks again guys!

---

### Post by caljohnsmith on 2009-01-22
Glad that worked OK; cheers and enjoy Windows and Ubuntu. :)

---

