---
title: "Using the Windows Boot manager to boot Ubuntu off another HDD"
date: 2009-06-07
forum: General Help
---

### Post by nuclearpidgeon on 2009-06-07
Hi,

I've recently been using a special setup to install ubuntu - since I am always shuffling around partitions and operating systems, I find it is easier to not install GRUB over the Windows boot manager.

My previous setup was like this - bear with me, this is a little complicated:
**HDD Table key: {} is HD, [] is a partition, () is an extended partition**


Windows XP was already installed

{ [WINDOWS XP] }

Installed Ubuntu, putting both the ext3 partition and the swap partition inside an extended partition. Then installed GRUB to the extended partition, not the MBR

Grub installed here \/
{ [  WINDOWSXP  ] ( [ UBUNTU FILES ] [SWAP] ) }

Then I used this command:
```
dd if=/dev/sda5/ of=/media/WINDOWSXP/Linux.bin count=1 bs=512
```to make a file that the windows bootloader could chainload, giving me access to ubuntu. (sda5 was the extended partition, where I installed GRUB).


Now my setup has changed. To conserve space, I've decided to move Ubuntu onto another older hard drive.

HD1
{ [ WINDOWSXP ] }
HD2
{ [ UBUNTU ] ( [SWAP] ) }     //This is the standard way of installing ubuntu - the installer did it automatically

However, I can't do the original Windows bootloader link - I get a GRUB error 22. I think this is because the data inside the bin file (from the dd command) is drive-relative. Because the Windows boot manager (and thus the bin file) is on HD1, it is trying to reference the MBR of **that** HDD, not the 2nd one.

How can I make the bin file point to the other hard drive?

P.S.
Sorry if this is complicated  it's a bit tricky to explain. if you post back, make sure you give a detailed description of your interpretation of my description. If need be, I can try to re-explain it.

Thanks!

---

### Post by Bearly Able on 2009-06-07
OK, so as I understand it, you have Windows on one drive, Ubuntu on the other and want to load Ubuntu from Windows, not Windows from GRUB, yes?

When I first tried to dual-boot (XP on one drive and Ubuntu on the other), I couldn't get GRUB to load Windows.  I had excellent advice to set things up with Windows loading GRUB, and you should be able to follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1060203").  Read through the thread, because at the start we were trying to get GRUB to load Windows.

Good luck!

---

### Post by nuclearpidgeon on 2009-06-21
Hmm, I tried a few things mentioned there, but had no luck.

Here are my results from that boot script thing though...

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub0.97 in the file /linux.bin looks at sector 1 of 
                       the same hard drive for the stage2 file. A stage2 file 
                       is at this location on /dev/sdb. Stage2 looks on the 
                       same partition for /boot/grub/stage2.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```

---

### Post by nuclearpidgeon on 2009-06-21
Hmm. (again)
Just tried booting directly off the 2nd HDD by changing the BIOS disk boot order.
Ubuntu boots fine, I'm using it now, but If I try to load Windows it says:

Unsupported executable format

or something like that. I can quote it exactly if required

---

### Post by Bearly Able on 2009-06-26
Sorry to take so long getting back to you.  I'm not sure if this is any help to you, but I've run the boot info script again, and the results are below.  This should give you the details from my system, where Windows does boot Ubuntu, to compare with yours.  Hopefully you, or someone else on the forums, can work out what needs to change on yours to get it working the way you want.

(Don't get confused by the two entries for Ubuntu on the Windows boot menu.  I had to do a fresh install after problems with Jaunty, and had to reset the boot order.  I somehow managed to add the extra line by mistake at that stage.  Also, the Windows entry in GRUB doesn't work; I keep meaning to comment it out.) 

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /grub.bin is trying to chain load 
                       sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 24231999 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbc4fbc4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,576,704   240,894,675   f W95 Ext d (LBA)
/dev/sda5          71,682,093   133,259,174    61,577,082   7 HPFS/NTFS
/dev/sda6         133,259,238   199,463,039    66,203,802   7 HPFS/NTFS
/dev/sda7         199,463,103   266,678,999    67,215,897   7 HPFS/NTFS
/dev/sda8         266,679,063   312,576,704    45,897,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ec031

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   300,447,629   300,447,567  83 Linux
/dev/sdb2         300,447,630   312,576,704    12,129,075   5 Extended
/dev/sdb5         300,447,693   312,576,704    12,129,012  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="127C3D347C3D13C7" TYPE="ntfs" 
/dev/sda5: UUID="4CBE3566D7F2CDE4" TYPE="ntfs" 
/dev/sda6: UUID="ACABF83B1BD256E9" TYPE="ntfs" 
/dev/sda7: UUID="024FF147EFA0A210" TYPE="ntfs" 
/dev/sda8: UUID="132F8D1E942CCBC1" TYPE="ntfs" 
/dev/sdb1: UUID="6385736e-fa00-46bb-aeb9-e38234f91980" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="4d8ef928-c53e-47e2-8cab-67f20ec03462" 

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
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lesley/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lesley)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\grub.bin=" Ubuntu Grub Menu"

C:\grub.bin=" Ubuntu Grub Menu"


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
# kopt=root=UUID=6385736e-fa00-46bb-aeb9-e38234f91980 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6385736e-fa00-46bb-aeb9-e38234f91980

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		6385736e-fa00-46bb-aeb9-e38234f91980
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6385736e-fa00-46bb-aeb9-e38234f91980 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		6385736e-fa00-46bb-aeb9-e38234f91980
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6385736e-fa00-46bb-aeb9-e38234f91980 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6385736e-fa00-46bb-aeb9-e38234f91980
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6385736e-fa00-46bb-aeb9-e38234f91980 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6385736e-fa00-46bb-aeb9-e38234f91980
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6385736e-fa00-46bb-aeb9-e38234f91980 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6385736e-fa00-46bb-aeb9-e38234f91980
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6385736e-fa00-46bb-aeb9-e38234f91980 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=4d8ef928-c53e-47e2-8cab-67f20ec03462 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  12.4GB: boot/grub/menu.lst
  12.4GB: boot/grub/stage2
  12.4GB: boot/initrd.img-2.6.27-14-generic
  12.4GB: boot/initrd.img-2.6.27-7-generic
  12.3GB: boot/vmlinuz-2.6.27-14-generic
  12.3GB: boot/vmlinuz-2.6.27-7-generic
  12.4GB: initrd.img
  12.4GB: initrd.img.old
  12.3GB: vmlinuz
  12.3GB: vmlinuz.old
```

---

