---
title: "Ubuntu GRUB query"
date: 2009-01-23
forum: General Help
---

### Post by markeee on 2009-01-23
Hi,

Just need a bit of help with grub.

Currently have Ubuntu 8.10 installed on my external USB drive, with XP installed on the internal sata drive


GRUB is installed on the external usb, obviusly this creates a problem booting up when the usb drive is not connected

How would I go about changing it so grub uses a partition on the sata driv??



Created a partition on sda, /dev/sda5 - to be a dedicated grub partition

Copied /boot/ to /dev/sda5 - but Im not sure what to do from here

I know I need to edit the menu.lst
#
Should i delete the copy of grub that's on the external drive (rename it incase I need to call it back) and work on the grub on new partition?


Thanks


Mark

---

### Post by caljohnsmith on 2009-01-23
Does your BIOS support USB booting? If so, you wouldn't need to install Grub to your sda drive if you don't want to, you could just install Grub to your USB drive. Or I can help you set up a dedicated Grub partition if that's what you really want. How about posting the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by dagnabit dang doohickey on 2009-01-23
A dedicated grub partition doesn't need the whole /boot dir on it, just /boot/grub. To be more clear, the /boot dir on the grub partition should only contain the grub directory.

The menu.lst on the dedicated grub partition will need some changes. The whole AUTOMAGIC KERNELS LIST section should be deleted and replaced with an entry that points to the menu.lst on the ubuntu partition. The grub configfile command is used for this.

As an example, the following is what replaced the the AUTOMAGIC KERNELS LIST section in the menu.lst on my dedicated grub partition.
```
# Boot Ubuntu Dapper Drake on /dev/hda6
title       Ubuntu Dapper Drake
configfile  (hd0,5)/boot/grub/menu.lst

```

Handy link: [How to make a dedicated GRUB Partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by markeee on 2009-01-24
> **caljohnsmith said:**
> Does your BIOS support USB booting? If so, you wouldn't need to install Grub to your sda drive if you don't want to, you could just install Grub to your USB drive. Or I can help you set up a dedicated Grub partition if that's what you really want. How about posting the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

thanks for your reply mate

the BIOS does support USB booting

at present GRUb is installed on the USB drive (/dev/sdb5) and it  is also installed on the internal SATA drive (/dev/sda)

If the USB drive is connected - i can select boot off USB, which will then load GRUB off the USB drive

If the USB drive is not connected and I leave it to boot up as normal, then the grub off sda will be loaded, which will allow us to boot into Windows vista.


What I would like is to have:

a) grub installed on /dv/sda - so only one copy of grub installed

b) be able to select Windows / Ubuntu from the grub on sda (can select windows atm) just need to edit menu.lst to be able to select boot ubuntu 

my final question is..how do i remove grub from the external drive? 


Thanks


Mark

---

### Post by caljohnsmith on 2009-01-24
It would help if I could first get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup related to booting.

---

### Post by markeee on 2009-01-24
```
=========================== Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 687297032 on boot drive #2 for the stage2 
                       file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block. BootPart 
                       in the file /NST/nst_grub.mbr is trying to chain load 
                       sector #585938808 on boot drive #3
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 687338968 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 687142792 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 687224704 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70000000

Partition  Boot        Start          End         Size  Id System

/dev/sda1                 63      449,819      449,757  de Dell Utility
/dev/sda2            450,560   21,422,063   20,971,504   7 HPFS/NTFS
/dev/sda3    *    21,422,080  229,195,767  207,773,688   7 HPFS/NTFS
/dev/sda4        229,199,355  234,436,544    5,237,190   5 Extended
/dev/sda5        229,199,418  234,436,544    5,237,127  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a832b

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63  585,938,744  585,938,682   b W95 FAT32
/dev/sdb2        585,938,745  781,417,664  195,478,920   5 Extended
/dev/sdb5        585,938,808  773,385,164  187,446,357  83 Linux
/dev/sdb6        773,385,228  781,417,664    8,032,437  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0710" TYPE="vfat" 
/dev/sda2: UUID="D27881027880E697" TYPE="ntfs" 
/dev/sda3: UUID="1AF0340FF033EF9D" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="6bda9dfc-e7ca-44d3-bca2-e5dfa4dd9edf" TYPE="ext2" 
/dev/sdb1: LABEL="FREECOM HDD" UUID="F4F7-8880" TYPE="vfat" 
/dev/sdb5: UUID="66233def-d918-4c2d-8810-64c28935ae1a" TYPE="ext3" 
/dev/sdb6: UUID="6d0f055b-34ea-4303-b10d-23eb604db9e9" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="08E5-5129" TYPE="vfat" 

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
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
/dev/sdb1 on /media/FREECOM HDD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3

title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

# title		Ubuntu 8.10, kernel 2.6.24-23-generic
# root		(hd1,4)
# kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
# initrd		/boot/initrd.img-2.6.24-23-generic
# quiet

# title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
# root		(hd1,4)
# kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro  single
# initrd		/boot/initrd.img-2.6.24-23-generic

# title		Ubuntu 8.10, memtest86+
# root		(hd1,4)
# kernel		/boot/memtest86+.bin
# quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



=================== sda5: Location  of files loaded by Grub: ===================


 119.3GB: boot/grub/menu.lst
 119.3GB: boot/grub/stage2
 119.3GB: boot/initrd.img-2.6.24-23-generic
 119.4GB: boot/initrd.img-2.6.27-9-generic
 119.3GB: boot/vmlinuz-2.6.24-23-generic
 119.4GB: boot/vmlinuz-2.6.27-9-generic

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
# kopt=root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=66233def-d918-4c2d-8810-64c28935ae1a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=6d0f055b-34ea-4303-b10d-23eb604db9e9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5 /media/extfs

=================== sdb5: Location  of files loaded by Grub: ===================


 351.8GB: boot/grub/menu.lst
 351.9GB: boot/grub/stage2
 351.8GB: boot/initrd.img-2.6.24-23-generic
 351.9GB: boot/initrd.img-2.6.27-9-generic
 351.8GB: boot/vmlinuz-2.6.24-23-generic
 351.8GB: boot/vmlinuz-2.6.27-9-generic
 351.9GB: initrd.img
 351.8GB: initrd.img.old
 351.8GB: vmlinuz
 351.8GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.

```

thanks for your help mate - above are the contents of the RESULTS.txt created from running the script

i know the post is long-but you said to paste here, hope it's ok:)



What I am trying to get is ;

grub on sda - and to be able to chose windows vista / ubuntu - with ubuntu being on the usb sdb5 (so i need to edit menu.lst on sda to reflect this i think)

but - how do i remove grub off the usb drive

cheers

---

### Post by caljohnsmith on 2009-01-24
OK, so when you boot Grub on your sda drive and get the Grub menu, what happens when you choose the first Ubuntu entry? The one I mean is:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```
It looks like that should work to boot Ubuntu on your USB drive, assuming your USB drive shows up as second in your BIOS boot order.

---

### Post by markeee on 2009-01-27
> **caljohnsmith said:**
> OK, so when you boot Grub on your sda drive and get the Grub menu, what happens when you choose the first Ubuntu entry? The one I mean is:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66233def-d918-4c2d-8810-64c28935ae1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```
It looks like that should work to boot Ubuntu on your USB drive, assuming your USB drive shows up as second in your BIOS boot order.


it doesn't load if I try to boot Ubuntu off the GRUB menu from the sda drive

I have to chose boot from USB so the grub located on the usb drive /dev/sdb5 loads and then I can boot into Ubuntu

caljohnsmith-not sure if this is a stupid question-you mention USB drive being second in the BIOS boot order

would that matter? How I thought it could be done was to have the GRUB load up off sda, select Ubuntu off the menu which would load the Ubuntu off the USB drive - or is this just not possible?

Thanks for your help!

Mark

---

### Post by caljohnsmith on 2009-01-27
> **markeee said:**
> 

caljohnsmith-not sure if this is a stupid question-you mention USB drive being second in the BIOS boot order

would that matter? How I thought it could be done was to have the GRUB load up off sda, select Ubuntu off the menu which would load the Ubuntu off the USB drive - or is this just not possible?

Thanks for your help!

Mark
It turns out that Grub on start up sees the order of drives as the BIOS boot order so that:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So if you boot from the sda drive, that drive should be (hd0), and if your USB drive is the only other drive, it should be (hd1). When you boot the USB drive, it will then be (hd0), and your sda drive will be (hd1) if it is the only other drive. But it sounds like something else may be going on, because you said you couldn't boot Ubuntu from the sda Grub menu even though the Ubuntu entries use (hd1,4). How about booting the sda drive again, and when you get the Grub menu, press "c" to get the Grub CLI, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Based on the size of the drive and the partitions those commands list, let me know if (hd0) is your sda drive and if (hd1) is your USB drive.

---

