---
title: "Grub issue"
date: 2009-03-22
forum: General Help
---

### Post by Jameshardy88 on 2009-03-22
Hi i have been dual booting windows xp and ubuntu 8.10 on my main disk for some time and have had everything running smoothly, however i recently decided to have a look at ultimate edition and so installed it onto my external hard drive. Now however i can't access any of my partitions unless the hard drive is plugged in (which is not always possible for me). I assume this is because my GRUB menu has been changed with the installation of the new OS and that by default it now looks for the list stored on my external hard drive? Basically when i turn on my pc it gets to the GRUB boot stage and returns with error 22. I was wondering how it would be possible to make it so that i could boot with or without the external hard drive plugged in?

thanks for any help,

james

---

### Post by Jameshardy88 on 2009-03-22
the error i get is this (looked it up) hope it helps...

21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.

---

### Post by Jameshardy88 on 2009-03-22
-

---

### Post by meierfra. on 2009-03-22
Please don't bump your thread more than once  a day.

To solve your problem  you need to install the Ultimate Grub to the external drive and the Ubuntu Grub to the internal drive:

Open a terminal in ubuntu and type

```
sudo grub 
```

and at the "grub>" prompt.

```
 find /boot/grub/stage2 
```

This will return (hd0,X) and (hd1,Y) where X and Y are some numbers, like (hd0,1) and (hd1,3)

Still at the "grub>" prompt:


```
root (hd0,X))
setup (hd0)
root (hd1,Y)
setup (hd1)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")
Also set you bios to boot from the external drive.

---

### Post by Jameshardy88 on 2009-03-24
Sorry i have a small problem still, Both stage 1 and 2 return the same directory...

grub> find /boot/grub/stage1
 (hd0,4)

grub> find /boot/grub/stage2
 (hd0,4)

Should i still just assign them both as previously suggested?

---

### Post by Jameshardy88 on 2009-03-25
bump

---

### Post by meierfra. on 2009-03-25
```
bump 
```

Sorry, I looked at your thread yesterday, thought about it and then forgot to answer.

Did you use "sudo grub"?
Do you have a separate boot or grub partition?

Anyway, try

```
sudo grub
find /boot/grub/stage2
find /grub/stage2
find /stage2
```


If this gives  you  two different "root (hd?,?}" use those two.
If not:

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Jameshardy88 on 2009-03-26
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 40887172 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o remove_hiberfile

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o remove_hiberfile


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,150,404    39,150,342   7 HPFS/NTFS
/dev/sda2          39,150,405   173,646,584   134,496,180   5 Extended
/dev/sda5          39,150,468   169,309,034   130,158,567  83 Linux
/dev/sda6         169,309,098   173,646,584     4,337,487  82 Linux swap / Solaris
/dev/sda3         173,646,585   193,261,949    19,615,365   c W95 FAT32 (LBA)
/dev/sda4         193,261,950   195,366,464     2,104,515  d7 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000215724032 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953546336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03c1c68d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,536,129 1,953,536,067   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="618AE8C503F87567" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda4: UUID="26184B24184AF27B" TYPE="ntfs" 
/dev/sda5: UUID="ca2f8262-7cce-473c-a5ec-be6647e1ed0d" TYPE="ext3" 
/dev/sda6: UUID="8dc21cc5-589d-4ffb-b340-6ced93a5b359" TYPE="swap" 
/dev/sdb1: LABEL="IOMEGA 1T" UUID="2FCD-7801" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb1 on /media/IOMEGA 1T type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
gvfs-fuse-daemon on /home/hardy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hardy)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=c:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca2f8262-7cce-473c-a5ec-be6647e1ed0d

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
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Embedded
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8dc21cc5-589d-4ffb-b340-6ced93a5b359 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  21.7GB: boot/grub/menu.lst
  20.9GB: boot/grub/stage2
  22.3GB: boot/initrd.img-2.6.27-11-generic
  20.6GB: boot/initrd.img-2.6.27-7-generic
  20.6GB: boot/initrd.img-2.6.27-9-generic
  21.1GB: boot/vmlinuz-2.6.27-11-generic
  20.6GB: boot/vmlinuz-2.6.27-7-generic
  20.6GB: boot/vmlinuz-2.6.27-9-generic
  22.3GB: initrd.img
  20.6GB: initrd.img.old
  21.1GB: vmlinuz
  20.6GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda3/BOOT.INI: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

I don't know if this is relevent but i ran this script when my external hard drive was not plugged in

---

### Post by meierfra. on 2009-03-26
> I don't know if this is relevent but i ran this script when my external hard drive was not plugged in 

Could you run the script again with the external drive plugged in?

>  Now however i can't access any of my partitions unless the hard drive is plugged in

Is this still the case?  Or did you run

sudo grub
root (hd0,4)
setup (hd0)

and now you are  able  boot without the external drive plugged in, but are no longer able to boot the Ultimate Edition?

Or did the above quote refer to your "1000GB" storage drive?

Was the external drive plugged in when you run "find /boot/grub/stage2"? (it needs to be)

---

### Post by Jameshardy88 on 2009-03-26
> **meierfra. said:**
> Could you run the script again with the external drive plugged in?


Will do as soon as i have access to it (its shared)

> **meierfra. said:**
> 
Is this still the case?  Or did you run

sudo grub
root (hd0,4)
setup (hd0)

and now you are  able  boot without the external drive plugged in, but are no longer able to boot the Ultimate Edition?


I am now able to access my Ubuntu (and windows) partitions again which for me is the main thing and im very relieved about so thank you very much for that =)  

> **meierfra. said:**
> 

Or did the above quote refer to your "1000GB" storage drive?



no it didn't refer to that drive, thats another hard drive of mine but is irrelevent in this case, it just has back-up data on it

> **meierfra. said:**
> 
Was the external drive plugged in when you run "find /boot/grub/stage2"? 



yes

---

### Post by meierfra. on 2009-03-26
> I am now able to access my Ubuntu
Good.  Now the RESULTS.txt makes sense. I was just confused since you hadn't mentioned this.

> 
[QUOTE]View Post
Was the external drive plugged in when you run "find /boot/grub/stage2"?
yes[/QUOTE]

O.K. Then we need to figure out why the stage2 file on your external drive was not detected. Could you run the boot  info script with the external drive attached and post the new RESULTS.txt (If you don't delete  the old RESULTS.txt beforehand, the new one will be called "RESULTS1.txt")

---

### Post by Jameshardy88 on 2009-03-27
> **meierfra. said:**
> O.K. Then we need to figure out why the stage2 file on your external drive was not detected. Could you run the boot  info script with the external drive attached and post the new RESULTS.txt (If you don't delete  the old RESULTS.txt beforehand, the new one will be called "RESULTS1.txt")


here it is...
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 40887172 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o remove_hiberfile

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o remove_hiberfile


sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,150,404    39,150,342   7 HPFS/NTFS
/dev/sda2          39,150,405   173,646,584   134,496,180   5 Extended
/dev/sda5          39,150,468   169,309,034   130,158,567  83 Linux
/dev/sda6         169,309,098   173,646,584     4,337,487  82 Linux swap / Solaris
/dev/sda3         173,646,585   193,261,949    19,615,365   c W95 FAT32 (LBA)
/dev/sda4         193,261,950   195,366,464     2,104,515  d7 Unknown


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd13e72ae

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   540,282,014   540,281,952   b W95 FAT32
/dev/sdc2         540,282,015   625,137,344    84,855,330   5 Extended
/dev/sdc5         540,282,078   621,570,914    81,288,837  83 Linux
/dev/sdc6         621,570,978   625,137,344     3,566,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="618AE8C503F87567" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda4: UUID="26184B24184AF27B" TYPE="ntfs" 
/dev/sda5: UUID="ca2f8262-7cce-473c-a5ec-be6647e1ed0d" TYPE="ext3" 
/dev/sda6: UUID="8dc21cc5-589d-4ffb-b340-6ced93a5b359" TYPE="swap" 
/dev/sdc1: LABEL="IOMEGA 300G" UUID="1031-10F5" TYPE="vfat" 
/dev/sdc5: UUID="6a480a4e-af89-4a7b-bea6-79c19fb5ace8" TYPE="ext3" 
/dev/sdc6: UUID="556a7c73-5bf7-44e6-8e99-cfa761b1d267" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/hardy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hardy)
/dev/sdc5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/IOMEGA 300G type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=c:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca2f8262-7cce-473c-a5ec-be6647e1ed0d

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
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ca2f8262-7cce-473c-a5ec-be6647e1ed0d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Embedded
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8dc21cc5-589d-4ffb-b340-6ced93a5b359 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  21.7GB: boot/grub/menu.lst
  20.9GB: boot/grub/stage2
  22.3GB: boot/initrd.img-2.6.27-11-generic
  20.6GB: boot/initrd.img-2.6.27-7-generic
  20.6GB: boot/initrd.img-2.6.27-9-generic
  21.1GB: boot/vmlinuz-2.6.27-11-generic
  20.6GB: boot/vmlinuz-2.6.27-7-generic
  20.6GB: boot/vmlinuz-2.6.27-9-generic
  22.3GB: initrd.img
  20.6GB: initrd.img.old
  21.1GB: vmlinuz
  20.6GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda3/BOOT.INI: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6a480a4e-af89-4a7b-bea6-79c19fb5ace8

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

title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro  single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Embedded
root		(hd0,3)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca2f8262-7cce-473c-a5ec-be6647e1ed0d ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=556a7c73-5bf7-44e6-8e99-cfa761b1d267 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 280.4GB: boot/grub/menu.lst
 280.5GB: boot/grub/stage2
 280.4GB: boot/initrd.img-2.6.27-12-generic
 280.4GB: boot/initrd.img-2.6.27-7-generic
 280.4GB: boot/vmlinuz-2.6.27-12-generic
 280.4GB: boot/vmlinuz-2.6.27-7-generic
 280.4GB: initrd.img
 280.4GB: initrd.img.old
 280.4GB: vmlinuz
```

---

### Post by meierfra. on 2009-03-27
Your 1000GB BackUp drive did not show up on RESULTS.txt. Was it plugged in?

Anyway, try this:
Boot into Ubuntu, open a terminal and open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Add this to the very end of the file:

title           Ultimate Edition
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/vmlinuz root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro quiet splash 
initrd		/initrd.img
quiet

title		Ultimate Edition (recovery mode)
uuid		6a480a4e-af89-4a7b-bea6-79c19fb5ace8
kernel		/vmlinuz root=UUID=6a480a4e-af89-4a7b-bea6-79c19fb5ace8 ro  single
initrd		/initrd.img



Save the file, reboot and see whether the new "Ulimate Edition" item on the Grub menu works.

---

### Post by Jameshardy88 on 2009-03-27
Thanks ill try that, and no i unplugged it whilst running that script

---

