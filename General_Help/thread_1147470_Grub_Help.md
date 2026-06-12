---
title: "Grub Help"
date: 2009-05-03
forum: General Help
---

### Post by ajhunte on 2009-05-03
Here is as much as I know. I originally began with a different OS installed on my machine. I added another hard drive and installed Ubuntu 8.10 on it. After this, I was unable to get to my other OS. When perusing around the terminal in linux, I can see the 'boot' file for the other OS listed in:

/media/HarDrive/boot

I am pretty sure that Grub recognizes the Ubuntu harddrive as hd0,5. I have also tried to edit the grub 'menu.lst' file by adding

title OTHER
root (hd1,1) >>>> I have tried (hd1, a lot of different numbers)
makeactive
chainloader +1
**************************************************  ****************************************************************************
Here is the output for fdisk -l:
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT
/dev/sda2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a91fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1220     9799618+  83  Linux
/dev/sdb2            1221       60801   478584382+   5  Extended
/dev/sdb5           59323       60801    11880036   82  Linux swap / Solaris
/dev/sdb6            1221       57843   454824184+  83  Linux
/dev/sdb7           57844       59322    11880036   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 2114 MB, 2114977792 bytes
2 heads, 63 sectors/track, 32784 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x001c6317

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       32785     2065392    6  FAT16
**************************************************  ****************************************************************************
Here is the output when I type 'Mount" in the director /media/HarDrive:

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ajhunte/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ajhunte)
/dev/sdc1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1  000,utf8,umask=077,flush)
/dev/sda2 on /media/HardDrive type hfsplus (rw,nosuid,nodev,uhelper=hal)

---

### Post by zvacet on 2009-05-03
I think [this]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Installing_Ubuntu_after_Mac_OS_X") is what are you looking for.Why are you afraid to say that you have Hachintosh installed.It is obvious from 

> /dev/sda2 on /media/HardDrive type hfsplus (rw,nosuid,nodev,uhelper=hal)

---

### Post by ajhunte on 2009-05-03
I appreciate the help, but I mentioned in my post that I had already tried that.

---

### Post by caljohnsmith on 2009-05-03
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by ajhunte on 2009-05-03
Thank you for the help, here is the results. I am pretty new to the boot loader game, so I dont get a lot of the syntax. 

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks at sector 722485311 on 
    boot drive #2 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640 1,953,000,879 1,952,591,240 HFS+

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a91fb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,599,299    19,599,237  83 Linux
/dev/sdb2          19,599,300   976,768,064   957,168,765   5 Extended
/dev/sdb5         953,007,993   976,768,064    23,760,072  82 Linux swap / Solaris
/dev/sdb6          19,599,426   929,247,794   909,648,369  83 Linux
/dev/sdb7         929,247,858   953,007,929    23,760,072  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2114 MB, 2114977792 bytes
2 heads, 63 sectors/track, 32784 cylinders, total 4130816 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x001c6317

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,130,815     4,130,784   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sda2: UUID="8A10C4F73504BCBD" LABEL="HardDrive" TYPE="hfsplus" 
/dev/sdb1: UUID="20170c0f-e5e3-49fa-8ae3-3e63138036e0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="8a81d82c-6d5a-437b-ab1b-de259371a7b7" TYPE="swap" 
/dev/sdb6: UUID="6dde861f-f65c-44e5-a898-03ebad7c33e0" TYPE="ext3" 
/dev/sdb7: UUID="da45b591-76b0-4a87-96b5-2283cb8e037e" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" UUID="1410-BF1F" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ajhunte/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ajhunte)
/dev/sdc1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=20170c0f-e5e3-49fa-8ae3-3e63138036e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=20170c0f-e5e3-49fa-8ae3-3e63138036e0

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        20170c0f-e5e3-49fa-8ae3-3e63138036e0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=20170c0f-e5e3-49fa-8ae3-3e63138036e0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        20170c0f-e5e3-49fa-8ae3-3e63138036e0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=20170c0f-e5e3-49fa-8ae3-3e63138036e0 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        20170c0f-e5e3-49fa-8ae3-3e63138036e0
kernel        /boot/memtest86+.bin
quiet

title        Hackintosh
root        (hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=20170c0f-e5e3-49fa-8ae3-3e63138036e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=8a81d82c-6d5a-437b-ab1b-de259371a7b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
   2.3GB: boot/grub/stage2
   2.3GB: boot/initrd.img-2.6.27-7-generic
   2.3GB: boot/vmlinuz-2.6.27-7-generic
   2.3GB: initrd.img
   2.3GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6dde861f-f65c-44e5-a898-03ebad7c33e0

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        6dde861f-f65c-44e5-a898-03ebad7c33e0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        6dde861f-f65c-44e5-a898-03ebad7c33e0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        6dde861f-f65c-44e5-a898-03ebad7c33e0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        6dde861f-f65c-44e5-a898-03ebad7c33e0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        6dde861f-f65c-44e5-a898-03ebad7c33e0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

#This is your sad attempt to get Hackintosh working. Such is life.
title Hackintosh
root (hd1,1)
makeactive
chainloader +1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=6dde861f-f65c-44e5-a898-03ebad7c33e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=da45b591-76b0-4a87-96b5-2283cb8e037e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 113.6GB: boot/grub/menu.lst
 113.6GB: boot/grub/stage2
 113.7GB: boot/initrd.img-2.6.27-11-generic
 113.6GB: boot/initrd.img-2.6.27-7-generic
 113.6GB: boot/vmlinuz-2.6.27-11-generic
 113.7GB: boot/vmlinuz-2.6.27-7-generic
 113.7GB: initrd.img
 113.6GB: initrd.img.old
 113.6GB: vmlinuz
 113.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 b9 01 00 00 00 b0  02 66 ba 00 e2 00 00 e8  |.f.......f......|
00000040  8f 00 81 3e 00 e4 48 2b  0f 85 7c 00 66 a1 28 e4  |...>..H+..|.f.(.|
00000050  66 0f c8 66 c1 e8 09 66  a3 06 e6 b0 04 8d 36 e3  |f..f...f......6.|
00000060  e3 8d 3e 20 e5 e8 98 01  75 3c 8d b6 1d 01 8b 34  |..> ....u<.....4|
00000070  81 3c 00 02 75 30 8b 5c  5e 86 fb 81 c3 ff 01 c1  |.<..u0.\^.......|
00000080  eb 09 80 fb 7e 77 1f 66  8b 44 08 66 0f c8 66 31  |....~w.f.D.f..f1|
00000090  c9 66 ba 00 02 02 00 8d  7c 68 e8 57 02 bf dd e3  |.f......|h.W....|
000000a0  e8 60 00 e9 19 00 66 8b  16 c0 e5 e8 1d 03 b0 7e  |.`....f........~|
000000b0  66 ba 00 02 02 00 e8 18  00 bf e3 e1 e8 44 00 8a  |f............D..|
000000c0  16 04 e6 ea 00 02 00 20  bf dd e1 e8 35 00 f4 eb  |....... ....5...|
000000d0  fd 66 60 06 89 e5 52 31  d2 66 c1 ea 04 8e c2 5b  |.f`...R1.f.....[|
000000e0  1e 1e 66 03 0e 00 e6 66  51 06 53 30 e4 50 68 10  |..f....fQ.S0.Ph.|
000000f0  00 8a 16 04 e6 89 e6 b4  42 cd 13 72 cb 89 ec 07  |........B..r....|
00000100  66 61 c3 66 60 57 be d3  e1 e8 07 00 5e e8 03 00  |fa.f`W......^...|
00000110  66 61 c3 bb 01 00 ac 3c  00 74 06 b4 0e cd 10 eb  |fa.....<.t......|
00000120  f5 c3 66 60 ad 86 e0 ab  3c 00 74 1c 89 c1 ad 09  |..f`....<.t.....|
00000130  c0 75 01 48 86 e0 80 fc  00 77 0a 3c 61 72 06 3c  |.u.H.....w.<ar.<|
00000140  7a 77 02 24 df ab e2 e6  66 61 c3 66 60 b2 00 66  |zw.$....fa.f`..f|
00000150  8b 44 02 66 3b 45 02 75  0f 80 3c 00 75 0a 66 8b  |.D.f;E.u..<.u.f.|
00000160  44 06 66 3b 45 06 74 48  77 44 72 3d 66 60 31 d2  |D.f;E.tHwDr=f`1.|
00000170  87 f7 66 ad 66 89 c1 87  f7 66 ad 66 39 c8 77 2e  |..f.f....f.f9.w.|
00000180  72 27 87 f7 ad 89 c1 87  f7 ad 80 f9 00 74 1f 39  |r'...........t.9|
00000190  c8 74 0b 77 07 fe ce 89  c1 e9 02 00 fe c6 f3 a7  |.t.w............|
000001a0  77 0c 72 05 88 f2 e9 07  00 fe ca e9 02 00 fe c2  |w.r.............|
000001b0  88 96 14 00 80 fa 00 66  61 c3 50 57 8b 3e 0a e6  |.......fa.PW.>..|
000001c0  57 47 47 49 49 b0 00 f3  aa 89 3e 0a e6 5d 89 2d  |WGGII.....>..].-|
000001d0  5f 58 c3 0d 0a 62 6f 6f  74 31 3a 20 00 65 72 72  |_X...boot1: .err|
000001e0  6f 72 00 73 74 61 72 74  75 70 66 69 6c 65 00 00  |or.startupfile..|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

sed: can't read sda2/etc/issue: No such file or directory

```

---

### Post by caljohnsmith on 2009-05-03
Unfortunately I'm not going to be able to help you; as zvacet all ready pointed out, you are indeed trying to boot an Apple OS on a PC, and that goes against forum rules since you are using pirated software on hardware that is not supported by Apple. We will be more than happy to help you with other booting problems, but we can't support piracy in these forums. So with that in mind, please do not ask for any further help with this issue in these forums. Thanks for your understanding and cooperation. :)

Regards,
John

---

