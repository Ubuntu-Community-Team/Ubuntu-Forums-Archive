---
title: "Grub error 17"
date: 2009-03-08
forum: General Help
---

### Post by yezdi on 2009-03-08
I have installed ubuntu on an external hard drive with the following details

(hd1,2) is my primary ubuntu partition with ubuntu installed in it.
(hd1,2) I also installed grub in the same partition.
(hd1,4) is my /home mount
(hd1,5) is my swap.

When I try to boot from my external drive the following comes up on screen

"GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17"

I have looked at a lot of threads on this forum and tried to reinstall grub, checked the menu.lst file and tried some other remedies but nothing seems to have worked. 
I would appreciate any help I can get.

---

### Post by DeMus on 2009-03-08
> **yezdi said:**
> I have installed ubuntu on an external hard drive with the following details

(hd1,2) is my primary ubuntu partition with ubuntu installed in it.
(hd1,2) I also installed grub in the same partition.
(hd1,4) is my /home mount
(hd1,5) is my swap.

When I try to boot from my external drive the following comes up on screen

"GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17"

I have looked at a lot of threads on this forum and tried to reinstall grub, checked the menu.lst file and tried some other remedies but nothing seems to have worked. 
I would appreciate any help I can get.

Please post the /boot/grub/menu.lst file here so others can have a look.
Also type in the terminal ```
sudo fdisk -l
``` and post the outcome here as well. Do this with your external drive connected to the computer.

---

### Post by yezdi on 2009-03-08
> **DeMus said:**
> Please post the /boot/grub/menu.lst file here so others can have a look.
Also type in the terminal ```
sudo fdisk -l
``` and post the outcome here as well. Do this with your external drive connected to the computer.
The following is the /boot/grub/menu.lst file

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
# kopt=root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05eadc67-de11-4b47-94d4-c24292509a91

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
uuid		05eadc67-de11-4b47-94d4-c24292509a91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		05eadc67-de11-4b47-94d4-c24292509a91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		05eadc67-de11-4b47-94d4-c24292509a91
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
chainloader	+1


----------------------------------------------------------------
I have attached the partition table for my external hard drive as an image file.

---

### Post by DeMus on 2009-03-08
Hi, sorry for the late reply (had to visit my mother who is ill).
Could you also post the contents of the /etc/fstab file?
I have a feeling the entry to your OS in the menu.lst file is pointing to the wrong disk and therefore it can not find the OS.

---

### Post by yezdi on 2009-03-08
> **DeMus said:**
> Hi, sorry for the late reply (had to visit my mother who is ill).
Could you also post the contents of the /etc/fstab file?
I have a feeling the entry to your OS in the menu.lst file is pointing to the wrong disk and therefore it can not find the OS.
Hi,
Thanks for getting back to me. I have attached an image of the /etc/fstab file because I couldn't get the right formatting in the text.

---

### Post by DeMus on 2009-03-11
> **yezdi said:**
> Hi,
Thanks for getting back to me. I have attached an image of the /etc/fstab file because I couldn't get the right formatting in the text.

Hi, I received your P.M. Sorry for not getting back to you.

In the menu.lst file you boot an OS from the partition with UUID=05eadc67-de11-4b47-94d4-c24292509a91
This is your sdc3 partition, according to your fstab file.
You mention in your original post you have installed Ubuntu on hd1, partitions 2, 4 and 5 with grub on 2.
Where does the name hd1 come from? "hd1" can never be "sdc" since "c" is the third disk.
I would say you are pointing to the wrong disk but grub does start and grub is on the same disk and partition as the OS. So you must be pointing to the right disk and partition.

I don't see anything wrong here, fstab and the outcome of fdisk -l do match. Very sorry but I can't help you any further, I am also still new to Linux myself. I hope somebody with experience else will read this post and helps you.
Good luck.

---

### Post by meierfra. on 2009-03-11
Grub error 17 can also be caused be the setting in the bios.
So in order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by yezdi on 2009-03-13
Hi mierfra,
Thank you for trying to help me. The following are the contents of the Results.txt file that the script generated.

```
============================= Boot Info Summary:==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 934215097 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x480a480a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   464,246,369   464,246,307   7 HPFS/NTFS
/dev/sda2         464,246,370   488,392,064    24,145,695   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002e457

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   918,677,024   918,676,962   7 HPFS/NTFS
/dev/sdb2    *    918,677,025   924,974,504     6,297,480   7 HPFS/NTFS
/dev/sdb3         924,974,505   944,509,544    19,535,040  83 Linux
/dev/sdb4         944,509,545   976,768,064    32,258,520   5 Extended
/dev/sdb5         944,509,608   972,832,139    28,322,532  83 Linux
/dev/sdb6         972,832,203   976,768,064     3,935,862  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="766DDF95331553FE" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="BCE8BA19E8B9D1BE" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdb2: UUID="498998305CC19AAB" TYPE="ntfs" 
/dev/sdb3: UUID="05eadc67-de11-4b47-94d4-c24292509a91" TYPE="ext3" 
/dev/sdb5: UUID="7beca02e-6302-4ef0-b605-3e0a5b369420" TYPE="ext3" 
/dev/sdb6: UUID="b3acbd24-e6d4-4a56-ac70-82189c787419" TYPE="swap" 

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
/dev/sdb3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05eadc67-de11-4b47-94d4-c24292509a91

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
uuid		05eadc67-de11-4b47-94d4-c24292509a91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		05eadc67-de11-4b47-94d4-c24292509a91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05eadc67-de11-4b47-94d4-c24292509a91 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		05eadc67-de11-4b47-94d4-c24292509a91
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
chainloader	+1



=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=05eadc67-de11-4b47-94d4-c24292509a91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=7beca02e-6302-4ef0-b605-3e0a5b369420 /home           ext3    relatime        0       2
# /dev/sdc6
UUID=b3acbd24-e6d4-4a56-ac70-82189c787419 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 478.4GB: boot/grub/menu.lst
 478.3GB: boot/grub/stage2
 478.2GB: boot/initrd.img-2.6.27-7-generic
 478.3GB: boot/vmlinuz-2.6.27-7-generic
 478.2GB: initrd.img
 478.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 21 e6 c1 36  |........?...!..6|
00000020  00 00 00 00 80 00 80 00  87 17 60 00 00 00 00 00  |..........`.....|
00000030  04 00 00 00 00 00 00 00  78 01 06 00 00 00 00 00  |........x.......|
00000040  f6 00 00 00 01 00 00 00  ab 9a c1 5c 30 98 89 49  |...........\0..I|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 fa 33 c0  |..............3.|
00000060  8e d0 bc 00 7c fb b8 c0  07 8e d8 c7 06 54 00 00  |....|........T..|
00000070  00 c7 06 56 00 00 00 c7  06 5b 00 10 00 b8 00 0d  |...V.....[......|
00000080  8e c0 2b db e8 07 00 68  00 0d 68 66 02 cb 50 53  |..+....h..hf..PS|
00000090  51 52 06 66 a1 54 00 66  03 06 1c 00 66 33 d2 66  |QR.f.T.f....f3.f|
000000a0  0f b7 0e 18 00 66 f7 f1  fe c2 88 16 5a 00 66 8b  |.....f......Z.f.|
000000b0  d0 66 c1 ea 10 f7 36 1a  00 88 16 25 00 a3 58 00  |.f....6....%..X.|
000000c0  a1 18 00 2a 06 5a 00 40  3b 06 5b 00 76 03 a1 5b  |...*.Z.@;.[.v..[|
000000d0  00 50 b4 02 8b 16 58 00  b1 06 d2 e6 0a 36 5a 00  |.P....X......6Z.|
000000e0  8b ca 86 e9 8a 36 25 00  b2 80 cd 13 58 72 2a 01  |.....6%.....Xr*.|
000000f0  06 54 00 83 16 56 00 00  29 06 5b 00 76 0b c1 e0  |.T...V..).[.v...|
00000100  05 8c c2 03 d0 8e c2 eb  8a 07 5a 59 5b 58 c3 be  |..........ZY[X..|
00000110  59 01 eb 08 be e3 01 eb  03 be 39 01 e8 09 00 be  |Y.........9.....|
00000120  ad 01 e8 03 00 fb eb fe  ac 3c 00 74 09 b4 0e bb  |.........<.t....|
00000130  07 00 cd 10 eb f2 c3 1d  00 41 20 64 69 73 6b 20  |.........A disk |
00000140  72 65 61 64 20 65 72 72  6f 72 20 6f 63 63 75 72  |read error occur|
00000150  72 65 64 2e 0d 0a 00 29  00 41 20 6b 65 72 6e 65  |red....).A kerne|
00000160  6c 20 66 69 6c 65 20 69  73 20 6d 69 73 73 69 6e  |l file is missin|
00000170  67 20 66 72 6f 6d 20 74  68 65 20 64 69 73 6b 2e  |g from the disk.|
00000180  0d 0a 00 25 00 41 20 6b  65 72 6e 65 6c 20 66 69  |...%.A kernel fi|
00000190  6c 65 20 69 73 20 74 6f  6f 20 64 69 73 63 6f 6e  |le is too discon|
000001a0  74 69 67 75 6f 75 73 2e  0d 0a 00 33 00 49 6e 73  |tiguous....3.Ins|
000001b0  65 72 74 20 61 20 73 79  73 74 65 6d 20 64 69 73  |ert a system dis|
000001c0  6b 65 74 74 65 20 61 6e  64 20 72 65 73 74 61 72  |kette and restar|
000001d0  74 0d 0a 74 68 65 20 73  79 73 74 65 6d 2e 0d 0a  |t..the system...|
000001e0  00 17 00 5c 4e 54 4c 44  52 20 69 73 20 63 6f 6d  |...\NTLDR is com|
000001f0  70 72 65 73 73 65 64 2e  0d 0a 00 00 00 00 55 aa  |pressed.......U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by meierfra. on 2009-03-13
> Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst

Grub is looking at partition #2 but Ubuntu is on partition #3 (/dev/sdb3). So you need to reinstall grub.

Boot from the LiveCD, open a terminal and  type

```
sudo grub
root (hd1,2)
setup (hd1)
quit
```

Reboot and hope for the best.

---

### Post by mandeepsmagh on 2009-03-13
Here is detailed guide for u to reinstall GRUB - [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by yezdi on 2009-03-16
> **meierfra. said:**
> Grub is looking at partition #2 but Ubuntu is on partition #3 (/dev/sdb3). So you need to reinstall grub.

Boot from the LiveCD, open a terminal and  type

```
sudo grub
root (hd1,2)
setup (hd1)
quit
```

Reboot and hope for the best.

Thanks a lot for all your help. I seem to have got it to work. I just had to reinstall grub in the Boot Record of the external drive.
```

sudo grub
find /boot/grub/stage1
(hd1,2)
root (hd1,2)
setup (hd1)
quit 
```

That seemed to do the trick

---

### Post by meierfra. on 2009-03-16
> I seem to have got it to work.
Great. Have fun with  Vista and Ubuntu.

---

