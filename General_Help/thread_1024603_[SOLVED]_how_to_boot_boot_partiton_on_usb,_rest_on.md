---
title: "[SOLVED] how to boot? /boot partiton on usb, rest on encrypted lvm"
date: 2008-12-29
forum: General Help
---

### Post by él Mero on 2008-12-29
[FONT="Courier New"]Hi all!

This is my first "real" linux install and of course I wanted to make it as hard as possible ;) (hard for me at least)

This is what I wanted:
[LIST=1]
[*]Encryption of the entire hard drive, and using lvm to put in /, /home and swap.
[*]Placing the /boot partition on my USB stick. 
[/LIST]

To achieve this I used the alternate installation CD, i.e. when reaching to the partitioning stage of the installation I did the two things earlier mentioned, /boot on usb, rest on hard drive.

Everything installed and no complaints.[/FONT]

Installation successful, time for rebooting... it doesn't boot (doesn't ask for a passwd or anything).

I have a motherboard that supports booting from USB and a USB stick that is able to do so, this has already been verified.

What have I missed?

---

### Post by caljohnsmith on 2008-12-29
Do you have a Live CD from which you can run commands? If not, I would recommend downloading one so you can use it for troubleshooting. If you can do that, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by él Mero on 2008-12-29
> **caljohnsmith said:**
> Do you have a Live CD from which you can run commands?
Yep, been using it to debug for about 24h now ^^

Here's the "RESULTS.txt":

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => No known boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: unknown filesystem type 'linux_raid_member'

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: unknown filesystem type 'linux_raid_member'

sdc1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Mounting failed:  
mount: unknown filesystem type 'crypto_LUKS'

sde1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4676faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001   fd  Linux raid autodetect

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf994f2d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   fd  Linux raid autodetect

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdbbe243e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   293041664   146520801   83  Linux

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb1cd24e


sfdisk -V /dev/sdd:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdd: unrecognized partition table type

sfdisk: no partition table present.

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

Disk /dev/sde: 1024 MB, 1024966656 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24d01a20

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63     1992059      995998+  83  Linux

sfdisk -V /dev/sde:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sde: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="953a0f61-e623-d22d-4abd-708a04cc7f7c" TYPE="mdraid" 
/dev/sdb1: UUID="953a0f61-e623-d22d-4abd-708a04cc7f7c" TYPE="mdraid" 
/dev/sdc1: UUID="1e1e6f09-5164-448a-99d2-0aa75b3e4e5c" TYPE="crypt_LUKS" 
/dev/loop0: TYPE="squashfs" 
/dev/sde1: UUID="b15d1ad9-b09e-41ac-8bfc-e1104724b38b" TYPE="ext2" 

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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=/dev/mapper/lvm-root ro

## default grub root device
## e.g. groot=(hd0,0)
## groot=f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
   groot=b15d1ad9-b09e-41ac-8bfc-e1104724b38b

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
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/lvm-root ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

================================== sde1/boot: ==================================

total 14048
drwxr-xr-x 4 root root    4096 2008-12-29 14:05 .
drwxr-xr-x 3 root root    4096 2008-12-29 14:05 ..
-rwx------ 1 root root  503560 2008-12-29 14:05 abi-2.6.27-7-generic
-rwx------ 1 root root   85316 2008-12-29 14:05 config-2.6.27-7-generic
drwx------ 2 root root    4096 2008-12-29 15:19 grub
-rwx------ 1 root root 9909046 2008-12-29 14:05 initrd.img-2.6.27-7-generic
drwx------ 2 root root    4096 2008-12-29 14:05 lost+found
-rwx------ 1 root root  124152 2008-12-29 14:05 memtest86+.bin
-rwx------ 1 root root 1352144 2008-12-29 14:05 System.map-2.6.27-7-generic
-rwx------ 1 root root    1130 2008-12-29 14:05 vmcoreinfo-2.6.27-7-generic
-rwx------ 1 root root 2339712 2008-12-29 14:05 vmlinuz-2.6.27-7-generic

=============================== sde1/boot/grub: ===============================

total 344
drwx------ 2 root root   4096 2008-12-29 15:19 .
drwxr-xr-x 4 root root   4096 2008-12-29 14:05 ..
-rwx------ 1 root root    191 2008-12-29 14:05 default
-rwx------ 1 root root     15 2008-12-29 14:05 device.map
-rwx------ 1 root root   8108 2008-12-29 14:05 e2fs_stage1_5
-rwx------ 1 root root   7856 2008-12-29 14:05 fat_stage1_5
-rwx------ 1 root root   8712 2008-12-29 14:05 jfs_stage1_5
-rwx------ 1 root root   4393 2008-12-29 15:19 menu.lst
-rw------- 1 root root   4393 2008-12-29 15:17 menu.lst~
-rwx------ 1 root root   7352 2008-12-29 14:05 minix_stage1_5
-rwx------ 1 root root   9756 2008-12-29 14:05 reiserfs_stage1_5
-rwx------ 1 root root    512 2008-12-29 14:05 stage1
-rwx------ 1 root root 121460 2008-12-29 14:05 stage2
-rwx------ 1 root root 121460 2008-12-29 14:05 stage2_eltorito
-rwx------ 1 root root   9556 2008-12-29 14:05 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sda

00000000  15 2c cb 6b dd 82 69 44  f2 59 02 bd b1 ac eb d1  |.,.k..iD.Y......|
00000010  0f 91 38 c7 54 49 d5 1b  9a 09 67 2d 05 86 e0 ac  |..8.TI....g-....|
00000020  bf 43 e4 c0 ba 9a df fa  25 8c e3 fc ab 48 42 e7  |.C......%....HB.|
00000030  6e 7c f0 89 c6 5f 95 44  ba 7b 75 bc 3a 3b 00 48  |n|..._.D.{u.:;.H|
00000040  22 39 38 16 ef 44 c7 1c  3f 32 dc c2 0b 6c c9 50  |"98..D..?2...l.P|
00000050  a3 32 5e 19 6d b2 03 65  5c cd 97 1f 32 a4 0c 43  |.2^.m..e\...2..C|
00000060  76 e4 bf 06 35 d6 98 c2  78 26 e6 a8 88 6e f7 24  |v...5...x&...n.$|
00000070  e4 8a 7a 0f ff 9b 95 97  ba d7 c6 ee a4 17 7b b5  |..z...........{.|
00000080  f3 1e 6f 27 42 aa ca 05  08 3d f8 45 dc a8 45 7a  |..o'B....=.E..Ez|
00000090  6b 5c 3d 02 35 70 c6 f1  0a 72 f9 c1 48 ed c5 b6  |k\=.5p...r..H...|
000000a0  d1 be 42 12 ce 17 d6 fd  27 50 0a 33 be 71 2a 6b  |..B.....'P.3.q*k|
000000b0  6e 80 9e 8b c6 8b 0b 8d  85 74 29 2f d5 7f 63 5d  |n........t)/..c]|
000000c0  48 9d 30 5f 93 76 34 c2  0d 38 15 08 e5 22 1e 0f  |H.0_.v4..8..."..|
000000d0  26 cf 96 41 6c 43 de 81  64 b7 4d d0 05 24 cc c3  |&..AlC..d.M..$..|
000000e0  90 91 30 a5 48 1d 5a 6b  f1 cc 11 5c 0b 11 9a 7d  |..0.H.Zk...\...}|
000000f0  cb 1f 1c be de f0 b7 e5  dd 12 5e 3e 8e 34 78 ff  |..........^>.4x.|
00000100  e0 74 3b 7d a5 66 c3 11  0d e4 f4 c8 e6 98 15 ce  |.t;}.f..........|
00000110  96 4a 29 98 d4 ea 0d d3  29 5d 53 0f 2a 08 e0 2b  |.J).....)]S.*..+|
00000120  72 1d 47 7f 62 a8 e4 cc  98 58 b9 e4 30 0e 08 19  |r.G.b....X..0...|
00000130  bd 27 b4 67 05 8a 58 61  80 70 24 dc 8f f6 7c 5d  |.'.g..Xa.p$...|]|
00000140  7d 64 4f 43 36 3b 37 b4  c9 00 55 48 9f cb ea 78  |}dOC6;7...UH...x|
00000150  79 8e b6 c5 2b 26 11 a8  1a 24 ca 3c 76 58 c3 ad  |y...+&...$.<vX..|
00000160  38 21 49 60 db 77 34 e0  da b5 c2 8c ec 27 34 01  |8!I`.w4......'4.|
00000170  02 58 26 48 fc 18 af bf  2f 4f 3d c9 98 85 2d 35  |.X&H..../O=...-5|
00000180  dd 2d 2d 6f 07 b4 52 69  01 4e f8 47 d0 7b 5d cd  |.--o..Ri.N.G.{].|
00000190  90 5b fc 88 32 b7 ab bf  f7 cb 74 19 ab d5 33 0b  |.[..2.....t...3.|
000001a0  a2 5e f3 07 74 4b 09 66  77 a3 ee 11 01 1d de f3  |.^..tK.fw.......|
000001b0  5a 71 31 1f 83 5b 7c c0  aa 6f 67 c4 68 a0 00 01  |Zq1..[|..og.h...|
000001c0  01 00 fd fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdb

00000000  f3 98 2f 07 1a be 25 29  e3 18 42 95 98 50 d5 6b  |../...%)..B..P.k|
00000010  a5 b3 47 82 5a e5 fe b8  ed d3 80 86 be ea dc d8  |..G.Z...........|
00000020  df 87 46 1b d4 ae 01 97  97 fe 82 ff e0 e4 d2 46  |..F............F|
00000030  a2 10 34 b5 d9 25 08 3b  83 b5 ef 04 ec 6c 30 4c  |..4..%.;.....l0L|
00000040  2f 8b 5a 76 fa 98 2b 58  91 54 b1 da 16 ee af bf  |/.Zv..+X.T......|
00000050  07 76 42 c2 08 94 c4 e5  e3 7a f1 06 cd 17 48 b3  |.vB......z....H.|
00000060  eb 8e b4 3f 14 e6 6c 15  d9 03 18 4d c2 d5 35 7d  |...?..l....M..5}|
00000070  db cf ba d2 6f 9b fc 5f  14 0c cf b4 e7 54 ee b3  |....o.._.....T..|
00000080  19 77 9d 9f ab ff 8c 76  75 f2 ff 81 6d 01 2c 29  |.w.....vu...m.,)|
00000090  26 02 e4 0c 97 a0 76 50  1e 51 d1 37 c5 89 e8 f4  |&.....vP.Q.7....|
000000a0  c3 2e 5b be 46 4b 53 22  6f 08 ad 9d 9e da 5c 6a  |..[.FKS"o.....\j|
000000b0  f1 f7 08 99 07 0d fb 61  0a 33 3e b7 ec 20 ff 1f  |.......a.3>.. ..|
000000c0  f0 9a 36 c3 6d 32 89 c2  cf 2f 6c ca de c8 8c e9  |..6.m2.../l.....|
000000d0  43 96 6e a0 47 48 53 3a  df 99 60 5b e6 7f fb dc  |C.n.GHS:..`[....|
000000e0  a9 a5 78 d6 a8 1c f5 fd  9b 4e 82 30 b4 33 86 4e  |..x......N.0.3.N|
000000f0  24 c7 5e 4a e0 bb 46 82  a5 6a 7d 4c 39 10 a4 d2  |$.^J..F..j}L9...|
00000100  f5 36 67 21 80 71 60 7c  dd 4c 38 f6 a8 83 10 40  |.6g!.q`|.L8....@|
00000110  9c 72 1f bf 59 cc 9c e1  64 90 de b2 70 39 c2 aa  |.r..Y...d...p9..|
00000120  dc 36 4d c9 7c 99 92 e7  9c 13 d6 45 42 20 f3 67  |.6M.|......EB .g|
00000130  b4 7f fa 26 3a e5 1c 01  25 f2 cb b4 10 64 1c 0c  |...&:...%....d..|
00000140  66 8b 70 f9 25 fd 53 e5  e1 8a a4 44 0b 72 f7 6c  |f.p.%.S....D.r.l|
00000150  73 d6 37 a7 0c 6d 90 87  ef 78 8b 7a a3 f8 7b 9e  |s.7..m...x.z..{.|
00000160  9c 1e 19 d7 01 03 6b 1e  b3 99 ea 1c 8a e2 e3 f7  |......k.........|
00000170  e2 5f 1e 6c 56 cc be 1e  cb 0a 68 2d b1 5d a7 0b  |._.lV.....h-.]..|
00000180  85 d7 8f 8b 9a 14 a1 3b  1a 28 ef f4 47 d6 81 af  |.......;.(..G...|
00000190  07 03 f6 9a a0 69 6e 6c  c0 90 a8 f5 c0 fa 68 f9  |.....inl......h.|
000001a0  29 9e 1c 3e 78 99 be e4  1e 1f fc f5 cb b7 97 3d  |)..>x..........=|
000001b0  ec a8 09 5c 73 ae 6a 19  d6 f2 94 f9 5a 39 00 01  |...\s.j.....Z9..|
000001c0  01 00 fd fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdc

00000000  a2 ce fd 94 2b c8 55 b0  48 e1 9e 53 af 7d 72 4e  |....+.U.H..S.}rN|
00000010  5f a2 ee 7b 48 31 41 52  b9 e4 f6 4c 8d 06 01 f8  |_..{H1AR...L....|
00000020  15 f6 8b de c4 59 7d 17  9d 22 ce a8 5d 43 8d a3  |.....Y}.."..]C..|
00000030  68 30 ae fc 74 18 94 2c  f7 e2 62 87 51 ea 02 5e  |h0..t..,..b.Q..^|
00000040  b9 78 f1 d4 e9 04 d1 81  89 2c ad c8 5d 71 09 f8  |.x.......,..]q..|
00000050  2d b5 b1 25 78 75 3e c5  d7 c6 69 0a 33 11 0f 01  |-..%xu>...i.3...|
00000060  a6 8e 08 6f 32 81 a8 66  24 37 11 ab 46 bf 3f c8  |...o2..f$7..F.?.|
00000070  c7 69 d1 ef eb 00 98 95  72 c7 e1 ca ca 34 82 5a  |.i......r....4.Z|
00000080  f4 6e a7 a6 36 88 5a 3f  86 7b d4 47 b1 e6 85 88  |.n..6.Z?.{.G....|
00000090  4e 84 e5 51 66 71 f8 15  e0 1c a4 c1 af 0b b3 e1  |N..Qfq..........|
000000a0  ba 52 a6 71 8e d1 3f 84  c6 30 cc 97 36 9c 35 b2  |.R.q..?..0..6.5.|
000000b0  da 3e c5 44 81 80 b8 bc  39 ff 89 e7 79 4e f8 0c  |.>.D....9...yN..|
000000c0  11 70 dd c9 d2 14 af ac  fd 8e d3 91 6c 9a a6 be  |.p..........l...|
000000d0  82 cf 49 bf d4 e4 2f 02  94 a6 68 33 c1 b5 aa 55  |..I.../...h3...U|
000000e0  11 02 24 a5 99 08 03 2f  42 cd c0 2d ec 98 30 23  |..$..../B..-..0#|
000000f0  5f 6f 4a bb f6 57 b5 60  0a 4a 19 9d 1f f8 22 34  |_oJ..W.`.J...."4|
00000100  d1 3e 54 fe 7c 67 92 86  ae 25 6c 63 4e 4d 2b 59  |.>T.|g...%lcNM+Y|
00000110  89 56 9e 2f 80 90 a3 4e  b3 24 74 1e 2b cf b7 20  |.V./...N.$t.+.. |
00000120  6a 5d 44 cb 13 e8 b4 28  59 ce ad 2c 29 73 f0 d9  |j]D....(Y..,)s..|
00000130  17 bc 1f 13 0a 46 4f 43  a6 6a 52 ad 7c f2 c1 92  |.....FOC.jR.|...|
00000140  f4 98 cb 05 f6 42 c1 8d  5b ff 5d 80 16 c1 d6 1a  |.....B..[.].....|
00000150  22 d8 a4 60 2b 33 13 b7  fc 55 8a 43 ab 18 98 01  |"..`+3...U.C....|
00000160  86 25 c4 a3 bc 2f 11 2f  cb f2 53 56 ad ef 34 95  |.%..././..SV..4.|
00000170  c2 e4 05 0d 7c 0d 46 23  cc 1d f4 d7 50 fb 95 e5  |....|.F#....P...|
00000180  39 3d 04 9d fe 65 fc 83  c2 de 67 a6 86 b4 64 c1  |9=...e....g...d.|
00000190  0e 16 1b 13 95 8d 40 fe  30 fa 68 62 02 51 0e b7  |......@.0.hb.Q..|
000001a0  25 18 64 ec 53 9d db 03  58 fa 71 69 38 ca be 16  |%.d.S...X.qi8...|
000001b0  1f a8 bc 69 0d 6c 59 c1  3e 24 be db 5a d4 00 01  |...i.lY.>$..Z...|
000001c0  01 00 83 fe ff ff 3f 00  00 00 c2 75 77 11 00 00  |......?....uw...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdd

00000000  de 1e c4 d0 25 66 d7 1d  ef 3a 02 dd 28 67 36 51  |....%f...:..(g6Q|
00000010  db 5a 7a 71 f7 d5 d6 38  54 e7 6f 43 f1 1a f3 9a  |.Zzq...8T.oC....|
00000020  80 ee 37 ce 24 86 1f 44  79 a2 bf d0 d5 cd bf 85  |..7.$..Dy.......|
00000030  cd d8 04 cc fb 86 8c b4  ff 89 9a 89 c4 ad 14 a8  |................|
00000040  05 54 29 91 0f 22 36 3e  c8 f9 eb b4 f0 28 aa d7  |.T).."6>.....(..|
00000050  a7 df 2f 82 2f e7 76 d7  f4 8f d9 d4 c9 ea 7a 27  |.././.v.......z'|
00000060  75 37 e0 44 6e a1 e5 b4  e4 29 cf b0 01 e0 bd ee  |u7.Dn....)......|
00000070  70 59 45 bb 1c 5e 5b 4a  3a e2 74 4c 89 37 ec c0  |pYE..^[J:.tL.7..|
00000080  d8 81 a5 0d ca 6b f2 4e  d6 18 b3 ed 91 5d c1 73  |.....k.N.....].s|
00000090  30 2d 8c 9e 48 54 02 b5  d9 68 b3 18 8b fd 33 1b  |0-..HT...h....3.|
000000a0  37 19 c0 14 a9 e8 25 b3  a5 b0 de 92 27 06 7d 0d  |7.....%.....'.}.|
000000b0  ef 43 4d 54 3d 32 34 be  da 0b de 61 57 a5 17 df  |.CMT=24....aW...|
000000c0  99 e7 79 82 96 80 48 8c  59 d7 9a c8 4c 45 bb 65  |..y...H.Y...LE.e|
000000d0  b6 83 cf 04 83 5e b9 10  44 b2 3c 4e 76 95 60 b5  |.....^..D.<Nv.`.|
000000e0  07 d3 18 7f 16 9b 21 80  fb 77 2d b7 87 81 41 23  |......!..w-...A#|
000000f0  8c d5 5c d7 a0 42 59 51  1f 45 16 08 6f 37 d6 44  |..\..BYQ.E..o7.D|
00000100  88 c5 e4 32 b3 a1 7a 38  91 77 e0 86 60 23 d8 ee  |...2..z8.w..`#..|
00000110  7a 21 3a f5 1e 44 dc 2a  73 ab b4 b6 ca f2 41 35  |z!:..D.*s.....A5|
00000120  24 a5 26 c4 f4 fa 19 5b  26 bf fb 5e 5f 91 48 6e  |$.&....[&..^_.Hn|
00000130  87 4f b2 85 85 ce 09 42  49 ce 5e 81 10 2d 68 2f  |.O.....BI.^..-h/|
00000140  e3 5b 27 5d 61 0e c6 92  bf 37 c6 66 0d 34 59 4c  |.[']a....7.f.4YL|
00000150  bb 47 0c b0 5b 47 a9 42  a8 95 5c 91 c8 52 14 db  |.G..[G.B..\..R..|
00000160  ce cf 2c 23 83 45 4b 85  66 c7 89 c7 f1 74 d3 30  |..,#.EK.f....t.0|
00000170  1e f1 90 9d 2a 17 84 d1  99 e8 f5 0d 7a c8 0d e0  |....*.......z...|
00000180  ec ea 80 41 e1 08 6f db  22 57 8b a8 94 ba 7d c1  |...A..o."W....}.|
00000190  b9 35 86 75 79 a5 62 98  23 af 73 1d af f7 1b e8  |.5.uy.b.#.s.....|
000001a0  46 92 6a dd 04 bd f9 3d  fc cf 15 32 7c 6c 20 a8  |F.j....=...2|l .|
000001b0  93 fc 35 5f d1 5b 0b 3e  4e d2 1c eb ed 47 06 98  |..5_.[.>N....G..|
000001c0  e2 b0 31 20 72 ce b2 52  fa 17 6f 8c 33 f4 84 8d  |..1 r..R..o.3...|
000001d0  b4 2c e6 84 b9 a0 46 6c  22 3a 39 9c bf 20 95 9a  |.,....Fl":9.. ..|
000001e0  ca 2d 1e 31 b5 a1 62 c3  27 17 e1 e0 41 b8 71 16  |.-.1..b.'...A.q.|
000001f0  25 af e1 0b b9 dc dd ca  a8 cd 11 5b aa ea 92 96  |%..........[....|
00000200

Unknown MBR on /dev/sde

00000000  d2 4b 8d 32 14 8a ab e7  93 63 ff 9e 1c 6d 5c 90  |.K.2.....c...m\.|
00000010  29 a7 59 06 9d f2 01 ea  98 87 b5 5c 4d 3a 51 a0  |).Y........\M:Q.|
00000020  6c 43 ac 8e 2f c2 6c d6  8e 07 ef 05 7e ef 2a 70  |lC../.l.....~.*p|
00000030  d5 dc c2 7f 03 58 7e 10  f0 12 23 3a 55 2b 3f ea  |.....X~...#:U+?.|
00000040  3e 20 46 e3 0e 12 21 1b  58 b3 c4 8e 26 56 40 2a  |> F...!.X...&V@*|
00000050  f2 ad 6c ec a3 61 92 e9  7e 54 ef e6 fb 1f c2 2e  |..l..a..~T......|
00000060  cc ba 02 ff b8 35 88 4a  95 12 f6 81 51 6c fe 65  |.....5.J....Ql.e|
00000070  47 42 27 8b d3 c6 c7 c4  6f a2 cf 69 48 16 c4 ca  |GB'.....o..iH...|
00000080  6b 6d 3a 14 7d 26 50 74  03 00 2e 24 2c 99 83 71  |km:.}&Pt...$,..q|
00000090  fa 1e 9e 74 77 8f d5 c8  5d 99 e7 d4 ac 9a e3 10  |...tw...].......|
000000a0  3a 51 86 60 7e 99 f6 d7  8e 68 94 67 6a 3d 5c a8  |:Q.`~....h.gj=\.|
000000b0  99 94 f8 76 a7 da b5 b1  49 9f 09 15 ce 7d 94 0e  |...v....I....}..|
000000c0  1e 3c 97 68 5f 83 67 31  6d 0f b8 86 18 50 b1 6a  |.<.h_.g1m....P.j|
000000d0  51 bb 1f 21 43 2b 71 02  36 a6 45 9c 74 2c 88 d7  |Q..!C+q.6.E.t,..|
000000e0  09 19 91 fb ac 83 4d 67  34 aa 4b 19 d6 2d a0 92  |......Mg4.K..-..|
000000f0  04 a8 ba 37 72 16 8b 60  2f 82 3c 6a 53 09 97 4d  |...7r..`/.<jS..M|
00000100  40 aa 65 ca f8 15 a7 7c  fb 47 36 64 8a 37 87 bb  |@.e....|.G6d.7..|
00000110  f6 01 8c 4b bf d5 9b 1d  67 74 15 99 38 17 74 ec  |...K....gt..8.t.|
00000120  57 66 e1 60 27 0f b3 48  45 1d 9d 1d 65 88 8a eb  |Wf.`'..HE...e...|
00000130  06 ae ec a6 e0 28 78 fe  6b 2e ab 81 ef 48 25 78  |.....(x.k....H%x|
00000140  1b 73 9a 7c 36 ce b0 89  e8 e8 7f e2 58 40 65 d0  |.s.|6.......X@e.|
00000150  5c fe c5 31 7a e6 65 50  63 a1 76 53 95 45 d2 32  |\..1z.ePc.vS.E.2|
00000160  8b 89 b8 95 86 21 5f c8  97 d4 b0 41 d5 aa e0 a8  |.....!_....A....|
00000170  42 ea 18 0c b0 9d 85 b9  c8 82 d8 2b 78 1f 18 83  |B..........+x...|
00000180  61 6e 25 ad 2d 35 52 f9  97 ef 4a b1 20 7a a5 cd  |an%.-5R...J. z..|
00000190  ba 3e 7e 31 1f c2 5f 52  e4 38 db e4 e1 91 36 b6  |.>~1.._R.8....6.|
000001a0  7a 42 10 cc 34 13 4c a9  eb 4a 9e 06 ad 80 34 fa  |zB..4.L..J....4.|
000001b0  31 68 f0 17 c5 47 b1 09  20 1a d0 24 58 7f 00 01  |1h...G.. ..$X...|
000001c0  01 00 83 fe 3f 7b 3f 00  00 00 3d 65 1e 00 00 00  |....?{?...=e....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sdc1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  11 e2 f8 eb 48 39 76 27  7f d4 67 e0 f6 cb 74 6e  |....H9v'..g...tn|
00000080  49 be 50 ef 08 47 ee 02  51 44 db 0a 70 96 76 d7  |I.P..G..QD..p.v.|
00000090  32 7f b9 de 98 5c cd 5f  41 7c 26 a2 bc b5 16 df  |2....\._A|&.....|
000000a0  f5 62 f2 29 00 00 00 0a  31 65 31 65 36 66 30 39  |.b.)....1e1e6f09|
000000b0  2d 35 31 36 34 2d 34 34  38 61 2d 39 39 64 32 2d  |-5164-448a-99d2-|
000000c0  30 61 61 37 35 62 33 65  34 65 35 63 00 00 00 00  |0aa75b3e4e5c....|
000000d0  00 ac 71 f3 00 06 71 67  3d 46 90 38 a4 45 09 19  |..q...qg=F.8.E..|
000000e0  1b 62 fa ad b3 52 03 69  04 c9 ad 4c 47 f3 10 0b  |.b...R.i...LG...|
000000f0  52 e6 28 f5 60 d7 29 d8  00 00 00 08 00 00 0f a0  |R.(.`.).........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Disk /dev/sdd doesn't contain a valid partition table
```

Hm, missing bootloader? Seems like that could be an issue ^^ 

Maybe there's more than that? Appreciate you taking you're time to help me caljohnsmith.

**Edit:** Maybe I should clarify that sda and sdb are 2 raided (mirrored) 500GB hard drives, sdc is my 150GB encrypted lvm hard drive, sdd I don't use and sde is my USB stick.

---

### Post by caljohnsmith on 2008-12-29
OK, from your Live CD try:
```
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, set your BIOS to boot your USB stick, and see if you get the Grub menu OK. If you get the Grub menu, it looks like you might be able to boot Ubuntu, but I'm not sure about that. Let me know how it goes or if you run into problems. :)

---

### Post by él Mero on 2008-12-29
> **caljohnsmith said:**
> Let me know how it goes or if you run into problems. :)
I had such a nice speech prepared: "Hi caljohnsmith! Currently I'm sitting at my newly booted encrypted hard drive and typing this message"... but I don't ^^

I couldn't see the Grub menu and the booting process pretty much behaved as it has been for the last 24h, not at all.

I'm sorry I don't have more information than that, perhaps I can intrigue you with an updated RESULTS.txt?
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => Grub is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: unknown filesystem type 'linux_raid_member'

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: unknown filesystem type 'linux_raid_member'

sdc1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Mounting failed:  
mount: unknown filesystem type 'crypto_LUKS'

sde1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4676faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001   fd  Linux raid autodetect

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf994f2d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   fd  Linux raid autodetect

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdbbe243e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   293041664   146520801   83  Linux

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb1cd24e


sfdisk -V /dev/sdd:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdd: unrecognized partition table type

sfdisk: no partition table present.

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

Disk /dev/sde: 1024 MB, 1024966656 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24d01a20

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63     1992059      995998+  83  Linux

sfdisk -V /dev/sde:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sde: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="953a0f61-e623-d22d-4abd-708a04cc7f7c" TYPE="mdraid" 
/dev/sdb1: UUID="953a0f61-e623-d22d-4abd-708a04cc7f7c" TYPE="mdraid" 
/dev/sdc1: UUID="1e1e6f09-5164-448a-99d2-0aa75b3e4e5c" TYPE="crypt_LUKS" 
/dev/loop0: TYPE="squashfs" 
/dev/sde1: UUID="b15d1ad9-b09e-41ac-8bfc-e1104724b38b" TYPE="ext2" 

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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=/dev/mapper/lvm-root ro

## default grub root device
## e.g. groot=(hd0,0)
## groot=f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
   groot=b15d1ad9-b09e-41ac-8bfc-e1104724b38b

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
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/lvm-root ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
##uuid		f33db5ae-7a39-4aab-a786-ff1eb5d4c54b
uuid		b15d1ad9-b09e-41ac-8bfc-e1104724b38b
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

================================== sde1/boot: ==================================

total 14048
drwxr-xr-x 4 root root    4096 2008-12-29 14:05 .
drwxr-xr-x 3 root root    4096 2008-12-29 14:05 ..
-rwx------ 1 root root  503560 2008-12-29 14:05 abi-2.6.27-7-generic
-rwx------ 1 root root   85316 2008-12-29 14:05 config-2.6.27-7-generic
drwx------ 2 root root    4096 2008-12-29 15:19 grub
-rwx------ 1 root root 9909046 2008-12-29 14:05 initrd.img-2.6.27-7-generic
drwx------ 2 root root    4096 2008-12-29 14:05 lost+found
-rwx------ 1 root root  124152 2008-12-29 14:05 memtest86+.bin
-rwx------ 1 root root 1352144 2008-12-29 14:05 System.map-2.6.27-7-generic
-rwx------ 1 root root    1130 2008-12-29 14:05 vmcoreinfo-2.6.27-7-generic
-rwx------ 1 root root 2339712 2008-12-29 14:05 vmlinuz-2.6.27-7-generic

=============================== sde1/boot/grub: ===============================

total 344
drwx------ 2 root root   4096 2008-12-29 15:19 .
drwxr-xr-x 4 root root   4096 2008-12-29 14:05 ..
-rwx------ 1 root root    191 2008-12-29 14:05 default
-rwx------ 1 root root     15 2008-12-29 14:05 device.map
-rwx------ 1 root root   8108 2008-12-29 14:05 e2fs_stage1_5
-rwx------ 1 root root   7856 2008-12-29 14:05 fat_stage1_5
-rwx------ 1 root root   8712 2008-12-29 14:05 jfs_stage1_5
-rwx------ 1 root root   4393 2008-12-29 15:19 menu.lst
-rw------- 1 root root   4393 2008-12-29 15:17 menu.lst~
-rwx------ 1 root root   7352 2008-12-29 14:05 minix_stage1_5
-rwx------ 1 root root   9756 2008-12-29 14:05 reiserfs_stage1_5
-rwx------ 1 root root    512 2008-12-29 14:05 stage1
-rwx------ 1 root root 121460 2008-12-29 14:05 stage2
-rwx------ 1 root root 121460 2008-12-29 14:05 stage2_eltorito
-rwx------ 1 root root   9556 2008-12-29 14:05 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sda

00000000  15 2c cb 6b dd 82 69 44  f2 59 02 bd b1 ac eb d1  |.,.k..iD.Y......|
00000010  0f 91 38 c7 54 49 d5 1b  9a 09 67 2d 05 86 e0 ac  |..8.TI....g-....|
00000020  bf 43 e4 c0 ba 9a df fa  25 8c e3 fc ab 48 42 e7  |.C......%....HB.|
00000030  6e 7c f0 89 c6 5f 95 44  ba 7b 75 bc 3a 3b 00 48  |n|..._.D.{u.:;.H|
00000040  22 39 38 16 ef 44 c7 1c  3f 32 dc c2 0b 6c c9 50  |"98..D..?2...l.P|
00000050  a3 32 5e 19 6d b2 03 65  5c cd 97 1f 32 a4 0c 43  |.2^.m..e\...2..C|
00000060  76 e4 bf 06 35 d6 98 c2  78 26 e6 a8 88 6e f7 24  |v...5...x&...n.$|
00000070  e4 8a 7a 0f ff 9b 95 97  ba d7 c6 ee a4 17 7b b5  |..z...........{.|
00000080  f3 1e 6f 27 42 aa ca 05  08 3d f8 45 dc a8 45 7a  |..o'B....=.E..Ez|
00000090  6b 5c 3d 02 35 70 c6 f1  0a 72 f9 c1 48 ed c5 b6  |k\=.5p...r..H...|
000000a0  d1 be 42 12 ce 17 d6 fd  27 50 0a 33 be 71 2a 6b  |..B.....'P.3.q*k|
000000b0  6e 80 9e 8b c6 8b 0b 8d  85 74 29 2f d5 7f 63 5d  |n........t)/..c]|
000000c0  48 9d 30 5f 93 76 34 c2  0d 38 15 08 e5 22 1e 0f  |H.0_.v4..8..."..|
000000d0  26 cf 96 41 6c 43 de 81  64 b7 4d d0 05 24 cc c3  |&..AlC..d.M..$..|
000000e0  90 91 30 a5 48 1d 5a 6b  f1 cc 11 5c 0b 11 9a 7d  |..0.H.Zk...\...}|
000000f0  cb 1f 1c be de f0 b7 e5  dd 12 5e 3e 8e 34 78 ff  |..........^>.4x.|
00000100  e0 74 3b 7d a5 66 c3 11  0d e4 f4 c8 e6 98 15 ce  |.t;}.f..........|
00000110  96 4a 29 98 d4 ea 0d d3  29 5d 53 0f 2a 08 e0 2b  |.J).....)]S.*..+|
00000120  72 1d 47 7f 62 a8 e4 cc  98 58 b9 e4 30 0e 08 19  |r.G.b....X..0...|
00000130  bd 27 b4 67 05 8a 58 61  80 70 24 dc 8f f6 7c 5d  |.'.g..Xa.p$...|]|
00000140  7d 64 4f 43 36 3b 37 b4  c9 00 55 48 9f cb ea 78  |}dOC6;7...UH...x|
00000150  79 8e b6 c5 2b 26 11 a8  1a 24 ca 3c 76 58 c3 ad  |y...+&...$.<vX..|
00000160  38 21 49 60 db 77 34 e0  da b5 c2 8c ec 27 34 01  |8!I`.w4......'4.|
00000170  02 58 26 48 fc 18 af bf  2f 4f 3d c9 98 85 2d 35  |.X&H..../O=...-5|
00000180  dd 2d 2d 6f 07 b4 52 69  01 4e f8 47 d0 7b 5d cd  |.--o..Ri.N.G.{].|
00000190  90 5b fc 88 32 b7 ab bf  f7 cb 74 19 ab d5 33 0b  |.[..2.....t...3.|
000001a0  a2 5e f3 07 74 4b 09 66  77 a3 ee 11 01 1d de f3  |.^..tK.fw.......|
000001b0  5a 71 31 1f 83 5b 7c c0  aa 6f 67 c4 68 a0 00 01  |Zq1..[|..og.h...|
000001c0  01 00 fd fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdb

00000000  f3 98 2f 07 1a be 25 29  e3 18 42 95 98 50 d5 6b  |../...%)..B..P.k|
00000010  a5 b3 47 82 5a e5 fe b8  ed d3 80 86 be ea dc d8  |..G.Z...........|
00000020  df 87 46 1b d4 ae 01 97  97 fe 82 ff e0 e4 d2 46  |..F............F|
00000030  a2 10 34 b5 d9 25 08 3b  83 b5 ef 04 ec 6c 30 4c  |..4..%.;.....l0L|
00000040  2f 8b 5a 76 fa 98 2b 58  91 54 b1 da 16 ee af bf  |/.Zv..+X.T......|
00000050  07 76 42 c2 08 94 c4 e5  e3 7a f1 06 cd 17 48 b3  |.vB......z....H.|
00000060  eb 8e b4 3f 14 e6 6c 15  d9 03 18 4d c2 d5 35 7d  |...?..l....M..5}|
00000070  db cf ba d2 6f 9b fc 5f  14 0c cf b4 e7 54 ee b3  |....o.._.....T..|
00000080  19 77 9d 9f ab ff 8c 76  75 f2 ff 81 6d 01 2c 29  |.w.....vu...m.,)|
00000090  26 02 e4 0c 97 a0 76 50  1e 51 d1 37 c5 89 e8 f4  |&.....vP.Q.7....|
000000a0  c3 2e 5b be 46 4b 53 22  6f 08 ad 9d 9e da 5c 6a  |..[.FKS"o.....\j|
000000b0  f1 f7 08 99 07 0d fb 61  0a 33 3e b7 ec 20 ff 1f  |.......a.3>.. ..|
000000c0  f0 9a 36 c3 6d 32 89 c2  cf 2f 6c ca de c8 8c e9  |..6.m2.../l.....|
000000d0  43 96 6e a0 47 48 53 3a  df 99 60 5b e6 7f fb dc  |C.n.GHS:..`[....|
000000e0  a9 a5 78 d6 a8 1c f5 fd  9b 4e 82 30 b4 33 86 4e  |..x......N.0.3.N|
000000f0  24 c7 5e 4a e0 bb 46 82  a5 6a 7d 4c 39 10 a4 d2  |$.^J..F..j}L9...|
00000100  f5 36 67 21 80 71 60 7c  dd 4c 38 f6 a8 83 10 40  |.6g!.q`|.L8....@|
00000110  9c 72 1f bf 59 cc 9c e1  64 90 de b2 70 39 c2 aa  |.r..Y...d...p9..|
00000120  dc 36 4d c9 7c 99 92 e7  9c 13 d6 45 42 20 f3 67  |.6M.|......EB .g|
00000130  b4 7f fa 26 3a e5 1c 01  25 f2 cb b4 10 64 1c 0c  |...&:...%....d..|
00000140  66 8b 70 f9 25 fd 53 e5  e1 8a a4 44 0b 72 f7 6c  |f.p.%.S....D.r.l|
00000150  73 d6 37 a7 0c 6d 90 87  ef 78 8b 7a a3 f8 7b 9e  |s.7..m...x.z..{.|
00000160  9c 1e 19 d7 01 03 6b 1e  b3 99 ea 1c 8a e2 e3 f7  |......k.........|
00000170  e2 5f 1e 6c 56 cc be 1e  cb 0a 68 2d b1 5d a7 0b  |._.lV.....h-.]..|
00000180  85 d7 8f 8b 9a 14 a1 3b  1a 28 ef f4 47 d6 81 af  |.......;.(..G...|
00000190  07 03 f6 9a a0 69 6e 6c  c0 90 a8 f5 c0 fa 68 f9  |.....inl......h.|
000001a0  29 9e 1c 3e 78 99 be e4  1e 1f fc f5 cb b7 97 3d  |)..>x..........=|
000001b0  ec a8 09 5c 73 ae 6a 19  d6 f2 94 f9 5a 39 00 01  |...\s.j.....Z9..|
000001c0  01 00 fd fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdc

00000000  a2 ce fd 94 2b c8 55 b0  48 e1 9e 53 af 7d 72 4e  |....+.U.H..S.}rN|
00000010  5f a2 ee 7b 48 31 41 52  b9 e4 f6 4c 8d 06 01 f8  |_..{H1AR...L....|
00000020  15 f6 8b de c4 59 7d 17  9d 22 ce a8 5d 43 8d a3  |.....Y}.."..]C..|
00000030  68 30 ae fc 74 18 94 2c  f7 e2 62 87 51 ea 02 5e  |h0..t..,..b.Q..^|
00000040  b9 78 f1 d4 e9 04 d1 81  89 2c ad c8 5d 71 09 f8  |.x.......,..]q..|
00000050  2d b5 b1 25 78 75 3e c5  d7 c6 69 0a 33 11 0f 01  |-..%xu>...i.3...|
00000060  a6 8e 08 6f 32 81 a8 66  24 37 11 ab 46 bf 3f c8  |...o2..f$7..F.?.|
00000070  c7 69 d1 ef eb 00 98 95  72 c7 e1 ca ca 34 82 5a  |.i......r....4.Z|
00000080  f4 6e a7 a6 36 88 5a 3f  86 7b d4 47 b1 e6 85 88  |.n..6.Z?.{.G....|
00000090  4e 84 e5 51 66 71 f8 15  e0 1c a4 c1 af 0b b3 e1  |N..Qfq..........|
000000a0  ba 52 a6 71 8e d1 3f 84  c6 30 cc 97 36 9c 35 b2  |.R.q..?..0..6.5.|
000000b0  da 3e c5 44 81 80 b8 bc  39 ff 89 e7 79 4e f8 0c  |.>.D....9...yN..|
000000c0  11 70 dd c9 d2 14 af ac  fd 8e d3 91 6c 9a a6 be  |.p..........l...|
000000d0  82 cf 49 bf d4 e4 2f 02  94 a6 68 33 c1 b5 aa 55  |..I.../...h3...U|
000000e0  11 02 24 a5 99 08 03 2f  42 cd c0 2d ec 98 30 23  |..$..../B..-..0#|
000000f0  5f 6f 4a bb f6 57 b5 60  0a 4a 19 9d 1f f8 22 34  |_oJ..W.`.J...."4|
00000100  d1 3e 54 fe 7c 67 92 86  ae 25 6c 63 4e 4d 2b 59  |.>T.|g...%lcNM+Y|
00000110  89 56 9e 2f 80 90 a3 4e  b3 24 74 1e 2b cf b7 20  |.V./...N.$t.+.. |
00000120  6a 5d 44 cb 13 e8 b4 28  59 ce ad 2c 29 73 f0 d9  |j]D....(Y..,)s..|
00000130  17 bc 1f 13 0a 46 4f 43  a6 6a 52 ad 7c f2 c1 92  |.....FOC.jR.|...|
00000140  f4 98 cb 05 f6 42 c1 8d  5b ff 5d 80 16 c1 d6 1a  |.....B..[.].....|
00000150  22 d8 a4 60 2b 33 13 b7  fc 55 8a 43 ab 18 98 01  |"..`+3...U.C....|
00000160  86 25 c4 a3 bc 2f 11 2f  cb f2 53 56 ad ef 34 95  |.%..././..SV..4.|
00000170  c2 e4 05 0d 7c 0d 46 23  cc 1d f4 d7 50 fb 95 e5  |....|.F#....P...|
00000180  39 3d 04 9d fe 65 fc 83  c2 de 67 a6 86 b4 64 c1  |9=...e....g...d.|
00000190  0e 16 1b 13 95 8d 40 fe  30 fa 68 62 02 51 0e b7  |......@.0.hb.Q..|
000001a0  25 18 64 ec 53 9d db 03  58 fa 71 69 38 ca be 16  |%.d.S...X.qi8...|
000001b0  1f a8 bc 69 0d 6c 59 c1  3e 24 be db 5a d4 00 01  |...i.lY.>$..Z...|
000001c0  01 00 83 fe ff ff 3f 00  00 00 c2 75 77 11 00 00  |......?....uw...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdd

00000000  de 1e c4 d0 25 66 d7 1d  ef 3a 02 dd 28 67 36 51  |....%f...:..(g6Q|
00000010  db 5a 7a 71 f7 d5 d6 38  54 e7 6f 43 f1 1a f3 9a  |.Zzq...8T.oC....|
00000020  80 ee 37 ce 24 86 1f 44  79 a2 bf d0 d5 cd bf 85  |..7.$..Dy.......|
00000030  cd d8 04 cc fb 86 8c b4  ff 89 9a 89 c4 ad 14 a8  |................|
00000040  05 54 29 91 0f 22 36 3e  c8 f9 eb b4 f0 28 aa d7  |.T).."6>.....(..|
00000050  a7 df 2f 82 2f e7 76 d7  f4 8f d9 d4 c9 ea 7a 27  |.././.v.......z'|
00000060  75 37 e0 44 6e a1 e5 b4  e4 29 cf b0 01 e0 bd ee  |u7.Dn....)......|
00000070  70 59 45 bb 1c 5e 5b 4a  3a e2 74 4c 89 37 ec c0  |pYE..^[J:.tL.7..|
00000080  d8 81 a5 0d ca 6b f2 4e  d6 18 b3 ed 91 5d c1 73  |.....k.N.....].s|
00000090  30 2d 8c 9e 48 54 02 b5  d9 68 b3 18 8b fd 33 1b  |0-..HT...h....3.|
000000a0  37 19 c0 14 a9 e8 25 b3  a5 b0 de 92 27 06 7d 0d  |7.....%.....'.}.|
000000b0  ef 43 4d 54 3d 32 34 be  da 0b de 61 57 a5 17 df  |.CMT=24....aW...|
000000c0  99 e7 79 82 96 80 48 8c  59 d7 9a c8 4c 45 bb 65  |..y...H.Y...LE.e|
000000d0  b6 83 cf 04 83 5e b9 10  44 b2 3c 4e 76 95 60 b5  |.....^..D.<Nv.`.|
000000e0  07 d3 18 7f 16 9b 21 80  fb 77 2d b7 87 81 41 23  |......!..w-...A#|
000000f0  8c d5 5c d7 a0 42 59 51  1f 45 16 08 6f 37 d6 44  |..\..BYQ.E..o7.D|
00000100  88 c5 e4 32 b3 a1 7a 38  91 77 e0 86 60 23 d8 ee  |...2..z8.w..`#..|
00000110  7a 21 3a f5 1e 44 dc 2a  73 ab b4 b6 ca f2 41 35  |z!:..D.*s.....A5|
00000120  24 a5 26 c4 f4 fa 19 5b  26 bf fb 5e 5f 91 48 6e  |$.&....[&..^_.Hn|
00000130  87 4f b2 85 85 ce 09 42  49 ce 5e 81 10 2d 68 2f  |.O.....BI.^..-h/|
00000140  e3 5b 27 5d 61 0e c6 92  bf 37 c6 66 0d 34 59 4c  |.[']a....7.f.4YL|
00000150  bb 47 0c b0 5b 47 a9 42  a8 95 5c 91 c8 52 14 db  |.G..[G.B..\..R..|
00000160  ce cf 2c 23 83 45 4b 85  66 c7 89 c7 f1 74 d3 30  |..,#.EK.f....t.0|
00000170  1e f1 90 9d 2a 17 84 d1  99 e8 f5 0d 7a c8 0d e0  |....*.......z...|
00000180  ec ea 80 41 e1 08 6f db  22 57 8b a8 94 ba 7d c1  |...A..o."W....}.|
00000190  b9 35 86 75 79 a5 62 98  23 af 73 1d af f7 1b e8  |.5.uy.b.#.s.....|
000001a0  46 92 6a dd 04 bd f9 3d  fc cf 15 32 7c 6c 20 a8  |F.j....=...2|l .|
000001b0  93 fc 35 5f d1 5b 0b 3e  4e d2 1c eb ed 47 06 98  |..5_.[.>N....G..|
000001c0  e2 b0 31 20 72 ce b2 52  fa 17 6f 8c 33 f4 84 8d  |..1 r..R..o.3...|
000001d0  b4 2c e6 84 b9 a0 46 6c  22 3a 39 9c bf 20 95 9a  |.,....Fl":9.. ..|
000001e0  ca 2d 1e 31 b5 a1 62 c3  27 17 e1 e0 41 b8 71 16  |.-.1..b.'...A.q.|
000001f0  25 af e1 0b b9 dc dd ca  a8 cd 11 5b aa ea 92 96  |%..........[....|
00000200

Unknown BootLoader  on /dev/sdc1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  11 e2 f8 eb 48 39 76 27  7f d4 67 e0 f6 cb 74 6e  |....H9v'..g...tn|
00000080  49 be 50 ef 08 47 ee 02  51 44 db 0a 70 96 76 d7  |I.P..G..QD..p.v.|
00000090  32 7f b9 de 98 5c cd 5f  41 7c 26 a2 bc b5 16 df  |2....\._A|&.....|
000000a0  f5 62 f2 29 00 00 00 0a  31 65 31 65 36 66 30 39  |.b.)....1e1e6f09|
000000b0  2d 35 31 36 34 2d 34 34  38 61 2d 39 39 64 32 2d  |-5164-448a-99d2-|
000000c0  30 61 61 37 35 62 33 65  34 65 35 63 00 00 00 00  |0aa75b3e4e5c....|
000000d0  00 ac 71 f3 00 06 71 67  3d 46 90 38 a4 45 09 19  |..q...qg=F.8.E..|
000000e0  1b 62 fa ad b3 52 03 69  04 c9 ad 4c 47 f3 10 0b  |.b...R.i...LG...|
000000f0  52 e6 28 f5 60 d7 29 d8  00 00 00 08 00 00 0f a0  |R.(.`.).........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Disk /dev/sdd doesn't contain a valid partition table
```

---

### Post by caljohnsmith on 2008-12-29
So what exactly happens on start up? Do you get any error messages? According to the new script results you posted, Grub is correctly installed to your sde USB stick, so if you can set your BIOS to boot it on start up, you should get the Grub menu. Have you gone into your BIOS and made sure the USB stick is first in the boot order?

---

### Post by él Mero on 2008-12-29
> **caljohnsmith said:**
> So what exactly happens on start up? Do you get any error messages? According to the new script results you posted, Grub is correctly installed to your sde USB stick, so if you can set your BIOS to boot it on start up, you should get the Grub menu. Have you gone into your BIOS and made sure the USB stick is first in the boot order?
Ok, let's try this one more time...

Hi caljohnsmith! Currently I'm sitting at my newly booted encrypted hard drive and typing this message ^^

I did two things before I got it working.

I copied the contents of the /boot folder on my USB to the / of my USB:

```
cp - R /media/disk/boot/* /media/disk/
```

because I wasn't sure if the bootloader could see the files if they weren't placed in root (which they actually were from the beginning before I moved them for some debugging purpose). Can they?

And then when I rebooted I made absolutely sure that the computer would boot from the USB.

First boot device: USB-HDD
Second boot device: USB-ZIP
Third boot device: Hard drive (Boot order of hard drives: USB stick put in first place).

These changes I of course made in the BIOS menu. When I tried booting the first time (when it didn't work) I pressed F12 to select what device to boot from, USB-HDD. As I stated, no boot there.

But now it works and I'm absolutely joyful! \\:D/

Only thing left now is to search for the thank you button. 

Thanks caljohnsmith!

---

### Post by caljohnsmith on 2008-12-29
I'm glad to hear you have it working now; cheers and have fun with your new Ubuntu install. :)

---

