---
title: "Grub issue"
date: 2009-03-10
forum: General Help
---

### Post by ekaqu on 2009-03-10
So, I have on my computer the following OSes: Ubuntu, OpenSolaris, Win2k, Vista  (and will be adding debian after i fix this issue).

My set up is a bit weird. My primary drive is my 250g drive which is what I used to store data (no OS), my slave drive is my 200g drive which is what I use for every OS.  (so grub is on primary drive and not with OSes).

The other day I removed the partitions (2 ext2 and 1 ntfs) from my data drive and made one big ext2 partition.

After that when I boot up, the only OS that I can get to is my ubuntu install (when I try windows it says its not valid, when I try OpenSolaris I get to its grub and try to load it but it gets to the screeen "loading" then reboots).

Any help to fix this issue would be most welcome.  Thanks for your time in reading this!

Here is my menu.list file:
```
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
# kopt=root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1037e3d1-0428-4d5b-865d-9d85ea02226a

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
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is for the windows vista install
title		Microsoft Windows Vista
root		(hd0,0)
chainloader	+1

# This is the solaris information
title OpenSolaris
rootnoverify		(hd1,2)
chainloader +1
```



Here is the output of fdisk -l:
```
sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b900b90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa4182e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5109    41038011    7  HPFS/NTFS
/dev/sdb2            5110       10595    44066295    5  Extended
/dev/sdb3           10596       15700    40998912   bf  Solaris
/dev/sdb4           15701       20806    41013945    7  HPFS/NTFS
/dev/sdb5            5110       10218    41038011   83  Linux
/dev/sdb6           10219       10595     3028221   82  Linux swap / Solaris
```


Edit: I just remembered one thing.  One of the ntfs partitions I deleted used to be a windows install now just data partition.  It might have been an active partition when I installed both the windows drives (explains why I had to use partition 0,0 for windows...).

---

### Post by LegendofTom on 2009-03-10
You might have altered the boot manager for windows by deleting partitions, maybe even a vital one.  Nevertheless, try this here:

 [http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/) 

to reset grub.

---

### Post by ekaqu on 2009-03-10
I tried what the site said and had the same issues.

When loading vista or win2k I see this "Error 13: Invalid or unsupported executable format"

I tried (at the grub screen) to boot into the partitions the windows installs are at (win2k(1,0), vista(1,3)) and for 2k it says its starting up but doesn't get past that (even with time) and vista says "bootmgr is missing".

OpenSolaris has the same issue, it gets to the loading then reboots.

I know that since I removed partition (0,0) that it prob messed up my windows drives, but I don't understand why OpenSolaris is still not working.  I have not set that OS up to read ntfs or ext systems, so changing that drive shouldn't cause this, but it seems to have a correlation.

---

### Post by LegendofTom on 2009-03-11
menu.lst shows:

title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is for the windows vista install
title		Microsoft Windows Vista
root		(hd0,0)
chainloader	+1

But you say win2k(1,0) and vista(1,3).  Try changing those and see what happens.

---

### Post by ekaqu on 2009-03-11
(0,0) was an old ntfs partition that used to have a windows install on it, it came before the 2k and vista installs so the boot info was on (0,0).

When I try to boot vista it says "bootmgr is missing".

for 2k it says "loading" and will say that for a few mins (10 is farthest I have tried) before I get bored and reboot.

So I dont think that the windows partitions can be saved without some trick from microsoft to get the boot information into those partitions.

My biggest wonder at the moment is why deleting the partitions screwed up my opensolaris install.

Thanks for your constant help LegendofTom.

---

### Post by lindsay7 on 2009-03-12
I do not know if this will help you but you might see something here that will help....


 In order to get a clearer picture of your setup, boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

Code:
sudo bash ~/Desktop/boot_info_script*.sh
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop;  copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.


Hopfully someone can help form there.

---

### Post by ekaqu on 2009-03-12
Here is the result file's input.

Also note that where it says I am trying to use the configfile for opensolaris, that was me testing that command out the other day, chainloader +1 has the issue I posted about (configfile just says "cant mount").
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.95 is installed in the boot sector of sdb3 and 
                       looks at sector 170208725 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b900b90

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002  93 Amoeba/Accidently Hidden Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa4182e1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    82,076,084    82,076,022  17 Hidden HPFS/NTFS
/dev/sdb2          82,076,085   170,208,674    88,132,590   5 Extended
/dev/sdb5          82,076,148   164,152,169    82,076,022  83 Linux
/dev/sdb6         164,152,233   170,208,674     6,056,442  82 Linux swap / Solaris
/dev/sdb3         170,208,675   252,206,498    81,997,824  bf Solaris
/dev/sdb4         252,220,500   334,248,389    82,027,890  17 Hidden HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="681a7892-7ffe-465d-aad7-209cc86e430a" TYPE="ext2" 
/dev/sdb1: UUID="D808BCF108BCD02C" TYPE="ntfs" 
/dev/sdb4: UUID="223406A66D157C59" TYPE="ntfs" 
/dev/sdb5: UUID="1037e3d1-0428-4d5b-865d-9d85ea02226a" TYPE="ext3" 
/dev/sdb6: UUID="7e91c584-f7fb-40bf-996c-01c5c769c49f" TYPE="swap" 
/dev/sdb7: TYPE="zfs" 
/dev/sdc1: UUID="002C0DDC2C0DCE1A" LABEL="FreeAgent Drive" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /mnt/windrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /mnt/linfiles type ext2 (rw)
/dev/sdb4 on /mnt/vistaDrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdc1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1037e3d1-0428-4d5b-865d-9d85ea02226a

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
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1037e3d1-0428-4d5b-865d-9d85ea02226a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows 2000 Professional
hide (hd1,3)
unhide(hd1,0)
root		(hd1,0)
chainloader	+1
makeactive
boot

# This is for the windows vista install
title		Microsoft Windows Vista
unhide (hd1,3)
hide (hd1,0)
rootnoverify	(hd1,3)
chainloader	+1
makeactive
boot

# This is the solaris information
title OpenSolaris
rootnoverify		(hd1,2)
configfile (hd1,2)/boot/grub/menu.lst
#chainloader +1

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=1037e3d1-0428-4d5b-865d-9d85ea02226a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=b6c5e721-737f-4d84-be14-09ca35270ed8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /mnt/windrive/ ntfs-3g defaults,locale=en_US.UTF-8 0 0
#/dev/sda1 /mnt/ntfShare/ ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /mnt/linfiles/ ext2 defaults 0 0
#/dev/sda3 /mnt/sharentfs/ ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb4 /mnt/vistaDrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


  76.1GB: boot/grub/menu.lst
  76.1GB: boot/grub/stage2
  76.1GB: boot/initrd.img-2.6.27-11-generic
  76.2GB: boot/initrd.img-2.6.27-7-generic
  76.2GB: boot/initrd.img-2.6.27-9-generic
  76.1GB: boot/vmlinuz-2.6.27-11-generic
  76.1GB: boot/vmlinuz-2.6.27-7-generic
  76.1GB: boot/vmlinuz-2.6.27-9-generic
  76.1GB: initrd.img
  76.2GB: initrd.img.old
  76.1GB: vmlinuz
  76.1GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-03-12
The Windows partition you deleted contained the boot files for  Windows 2000 and Windows Vista.  You might try the  tutorials in  this [thread]("http://ubuntuforums.org/showthread.php?t=813628") to restore the boot files (I think the tutorial for XP should also work for Win 2000, but I'm not sure)


> but I don't understand why OpenSolaris is still not working. 
Me neither. It might be a strange coincidence.  Does the "loading" screen  looks like a  grub screen or did opensolaris actually start to boot?
When was the last time you succesfully booted into opensolaris?

Try this:

Use 

title OpenSolaris
rootnoverify  (hd0,2)
chainloader +1

in menu.lst and set your bios to boot from the Ubuntu drive.

---

### Post by ekaqu on 2009-03-12
> **meierfra. said:**
> The Windows partition you deleted contained the boot files for  Windows 2000 and Windows Vista.  You might try the  tutorials in  this [thread]("http://ubuntuforums.org/showthread.php?t=813628") to restore the boot files (I think the tutorial for XP should also work for Win 2000, but I'm not sure)


 
Me neither. It might be a strange coincidence.  Does the "loading" screen  looks like a  grub screen or did opensolaris actually start to boot?
When was the last time you succesfully booted into opensolaris?


It looks like the screen OpenSolaris uses right when it starts to load the files.

Last time I logged into OS was the day before I deleted the partitions (I have a unix admin class that uses it, so  I use it to test scripts).  Worked like normal then.

Ill edit my grub with your settings later tonight, have an exam so can't really play around with things at the moment.

---

### Post by ekaqu on 2009-03-12
> **meierfra. said:**
> The Windows partition you deleted contained the boot files for  Windows 2000 and Windows Vista.  You might try the  tutorials in  this [thread]("http://ubuntuforums.org/showthread.php?t=813628") to restore the boot files (I think the tutorial for XP should also work for Win 2000, but I'm not sure)

I tried what the site said and the 2k install got farther, it stopped and said that <window root>\system32\hal.dll was corrupt or not there (its there alright).  I tried replacing it with the vista one and got the same issue.  


>  
Me neither. It might be a strange coincidence.  Does the "loading" screen  looks like a  grub screen or did opensolaris actually start to boot?
When was the last time you succesfully booted into opensolaris?

Try this:

Use 

title OpenSolaris
rootnoverify  (hd0,2)
chainloader +1

in menu.lst and set your bios to boot from the Ubuntu drive.

I did that and I didnt get any further.  I get to OpenSolari's grub window then try to load OpenSolaris and get to the 3 line load screen that says "sun" and other things (didnt stay up long enough to read it all).  Then it rebooted.

---

### Post by meierfra. on 2009-03-12
> <window root>\system32\hal.dll was corrupt or not there

This usually means that "boot.ini" is not configured correctly.

In your case it should be:

timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)[COLOR="Black"]\[/COLOR]Windows
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="<Some Title>" /fastdetect

(Well, that's what it should be for XP, i"m not sure that it's the same for Win 2000)

> OpenSolaris and get to the 3 line load screen that says "sun" and other things (didnt stay up long enough to read it all).

I'm not familar enough with OpenSolaris, to tell you what the problem might be. But I'll do some research.

---

### Post by meierfra. on 2009-03-12
Correction:

It seems for Win 2000 boot.ini should look like this:

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows 2000" /fastdetect

---

### Post by ekaqu on 2009-03-13
Thanks for the correction.  I can now boot 2000 =D.

---

