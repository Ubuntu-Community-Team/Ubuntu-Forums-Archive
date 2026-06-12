---
title: "Grub Problem"
date: 2009-04-06
forum: General Help
---

### Post by sunseeker888 on 2009-04-06
Hello Chaps

This is the last Pc I am installing Ubuntu. It has been 2 weeks since I have been trying to sort this problem. I could not installed ubuntu, becuase I have 2 dual graphic cards with 3 monitors. Once I removed one graphic card, ubuntu was installed. Now I am using one monitor till I sort some other problem first.

It's grub again

I have 2 hdd, identital, one specifically for vista sda1, and the ubuntu sdb2.

Please see the fdisk, and menu.lst. Can please what's wrong, why I can load vista.
 Can you please tell me what missing in the menu.lst. 

Thanks in advance




fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d1e1e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488384512    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1f79089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+  83  Linux
/dev/sdb2           12749       44619   256003807+  83  Linux
/dev/sdb3           44620       60801   129981915    5  Extended
/dev/sdb5           44620       46149    12289693+  82  Linux swap / Solaris
/dev/sdb6           46150       60801   117692158+   7  HPFS/NTFS



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
timeout		7

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
# kopt=root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2fcfd6c9-0bcd-440c-9564-31634399452f

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub is installed in the MBR of /dev/sdb and looks at sector 4234 of the 
    same hard drive for the stage2 file, but no stage2 files can be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93d1e1e5

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1f79089

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557  83 Linux
/dev/sdb2         204,796,620   716,804,234   512,007,615  83 Linux
/dev/sdb3         716,804,235   976,768,064   259,963,830   5 Extended
/dev/sdb5         716,804,298   741,383,684    24,579,387  82 Linux swap / Solaris
/dev/sdb6         741,383,748   976,768,064   235,384,317   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sdb2: UUID="2fcfd6c9-0bcd-440c-9564-31634399452f" TYPE="ext3" 
/dev/sdb5: UUID="9c4f440d-31e3-4e76-b1d2-2809e49311a8" TYPE="swap" 
/dev/sdb6: UUID="564AE3DF15070EBB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/badboy/.Private on /home/badboy/Private type ecryptfs (rw,ecryptfs_sig=4a002f09942519e2,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=badboy)
gvfs-fuse-daemon on /home/badboy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=badboy)


=========================== sdb2/boot/grub/menu.lst: ===========================

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
timeout		7

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
# kopt=root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2fcfd6c9-0bcd-440c-9564-31634399452f

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP/Vista 
root (hd0,0)
chainloader +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=2fcfd6c9-0bcd-440c-9564-31634399452f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=9c4f440d-31e3-4e76-b1d2-2809e49311a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 232.9GB: boot/grub/menu.lst
 232.9GB: boot/grub/stage2
 233.0GB: boot/initrd.img-2.6.27-11-generic
 232.9GB: boot/initrd.img-2.6.27-7-generic
 233.0GB: boot/vmlinuz-2.6.27-11-generic
 233.0GB: boot/vmlinuz-2.6.27-7-generic
 233.0GB: initrd.img
 232.9GB: initrd.img.old
 233.0GB: vmlinuz
 233.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  2c dc 9c fe 72 7b 45 41  a5 3b f1 9c 70 c9 15 9a  |,...r{EA.;..p...|
00000010  2c 37 4f 86 69 77 42 15  92 4d 74 c8 2b 54 61 e0  |,7O.iwB..Mt.+Ta.|
00000020  de e4 22 02 84 6e 22 a3  30 8d 13 d6 b2 b0 01 14  |.."..n".0.......|
00000030  63 bf db 07 d8 7b 41 56  6e 11 ae e0 10 71 6c 2c  |c....{AVn....ql,|
00000040  b2 5a 2a 4f 5a 1f b9 e4  ea 08 90 a3 4f 62 c3 09  |.Z*OZ.......Ob..|
00000050  5d 97 03 bd da 1f d7 f1  35 cb 0a b9 dd 1f 9e 30  |].......5......0|
00000060  cd de 5e 4d de db ab 3a  da 31 b8 27 3c 08 68 26  |..^M...:.1.'<.h&|
00000070  fe 4a 19 02 82 e1 b6 f7  c5 00 0e b4 e6 4e b8 91  |.J...........N..|
00000080  fb 97 4c ad e1 68 3a a9  20 e2 e0 0b 1c 73 a7 77  |..L..h:. ....s.w|
00000090  36 f4 ab f4 f3 4b d1 3d  d6 65 90 c9 97 6f 92 99  |6....K.=.e...o..|
000000a0  7d 04 76 cb 42 b1 18 f3  0e e3 ea 1a 93 01 f9 e6  |}.v.B...........|
000000b0  38 c5 e0 4c c6 ee 5b 52  0a f8 2b da f5 ea b0 39  |8..L..[R..+....9|
000000c0  f0 62 b4 8a 99 e5 ad a2  33 05 f4 f8 a3 ec 87 1f  |.b......3.......|
000000d0  08 5e 01 de 9f 29 fe b1  53 80 f1 65 a8 55 93 27  |.^...)..S..e.U.'|
000000e0  f9 8f 58 23 74 a8 da 60  c0 30 b6 33 0a 88 7f 41  |..X#t..`.0.3...A|
000000f0  68 1d c7 d9 ce 8d 74 bc  d0 4b 78 66 9a 25 bd ac  |h.....t..Kxf.%..|
00000100  80 e8 95 75 f2 89 ac eb  63 55 19 79 00 71 82 f8  |...u....cU.y.q..|
00000110  70 b2 5b 84 aa 02 c5 71  89 79 1c 10 b8 ad c6 6f  |p.[....q.y.....o|
00000120  1a c5 76 86 01 ac e4 32  7b 81 73 67 7a dd c4 ea  |..v....2{.sgz...|
00000130  02 2b 3d 27 32 09 03 24  3c ec 4e 35 6c f3 db d9  |.+='2..$<.N5l...|
00000140  90 fd bd 3e c2 1f 3c 78  ba f0 b3 63 20 7d 28 f3  |...>..<x...c }(.|
00000150  9c d8 0a 69 45 c8 26 e8  7b b1 31 a8 83 4c 6a a6  |...iE.&.{.1..Lj.|
00000160  ac 65 78 c3 27 e9 90 ff  dc 14 ed 27 d1 ec 2f 13  |.ex.'......'../.|
00000170  9c d4 46 38 c9 a8 c8 aa  62 56 0f 6c d7 20 a2 10  |..F8....bV.l. ..|
00000180  09 6a ac f9 ad 71 6e 01  e9 0a d2 49 9c c1 5c a9  |.j...qn....I..\.|
00000190  c7 b5 bb 99 41 21 cd a6  da e2 02 e0 9a c9 2c 01  |....A!........,.|
000001a0  ab c0 19 02 1c 59 24 b4  30 3e e2 e0 a7 29 9c 28  |.....Y$.0>...).(|
000001b0  89 f0 be 61 18 d9 cb cf  76 6e d9 e8 67 47 9e 25  |...a....vn..gG.%|
000001c0  ad cd e4 3e 84 d7 66 d1  46 b7 b9 f3 a9 55 5d 94  |...>..f.F....U].|
000001d0  a1 b9 17 bc ce 06 b5 5e  47 b6 44 65 8f c7 e8 81  |.......^G.De....|
000001e0  d5 be 73 4d 9e ee 21 7a  ff 8f ff 3e 32 8c 54 4b  |..sM..!z...>2.TK|
000001f0  80 b0 91 4b 03 df a3 ff  98 02 fa 31 9a 7d 4f 17  |...K.......1.}O.|
00000200

```

```



f

---

### Post by sunseeker888 on 2009-04-06
well


I think I know what's the problem.


That vista drive was fully encrypted with PGP. Usually when bios loads up, the pgp bootloader comes up, so I have to put that passphrase.


If Grub has wiped out PGP bootloader, I think I am deep poo.


Maybe I am missing something in Grub too, so it can't see the vista disk too?

---

### Post by LowSky on 2009-04-06
See the change I made to your Grub file, it in red, and please use {code] tages correctly, it makes things easier to read


```


=========================== sdb2/boot/grub/menu.lst: ===========================

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
timeout		7

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
# kopt=root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2fcfd6c9-0bcd-440c-9564-31634399452f

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2fcfd6c9-0bcd-440c-9564-31634399452f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2fcfd6c9-0bcd-440c-9564-31634399452f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP/Vista 
[COLOR="Red"]**root (hd0,5)**[/COLOR]
chainloader +1

 
```

---

### Post by sunseeker888 on 2009-04-06
[QUOTE=LowSky;7023635]See the change I made to your Grub file, it in red, and please use {code] tages correctly, it makes things easier to read




HI Thanks


Sorry about the codes

It did not work. I guess it's because the vista disk is fuly encrypted with PGP enterprise encrytion, and I guess the PGP bootloader is gone now, when I installed ubuntu today :(. The vista contents hdd is finished now, as the bootloader is gone. Luckily I did backup all the files couple days again on external drive.


Maybe I need to go on the pgp forum, they may know, if it's possible to get the pgp bootloader with grub. My day has just go very complicated now.

As vista is on hdd0, and ubuntu on hd1. Will it be more complicated if I have to re-install vista or do another re-install of ubuntu as I prefer grub

---

### Post by meierfra. on 2009-04-06
> if I have to re-install vista or do another re-install of ubuntu 
I don't think you need to reinstall Ubuntu. This is what I would try:


**Step 1  Install grub to the MBR of the Ubuntu  drive:**

```
sudo grub
```
and at the grub prompt

```
root (hd1,1)
setup (hd1)
quit
```


Reboot. But set your bios to boot from the Ubuntu drive.
See whether you can still boot into Ubuntu.


**Step 2 ** Edit menu lst.

Add these entries to menu.lst

title  Vista  (two  map lines)
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title  Vista (one map line)
rootnoverify (hd0)
map (hd1) (hd0)
chainloader +1

**Step 3**  Fix the MBR of your Vista drive.

I have no idea how to do this. If searching the pgp forum does not  provide a solution, reinstall Vista (but set your bios to boot from the Vista drive before hand)

**Step 4**  Try booting Vista

Set your bios to boot from the Ubuntu drive. Try both  Vista entries. If one of them works, deleted the other from menu.lst. If none of them works,  report any error  messages you got.


> Sorry about the codes
You  can still edit post 1 and insert the code tags.

---

