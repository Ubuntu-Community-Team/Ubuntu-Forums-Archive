---
title: "Grub and Windows XP"
date: 2009-05-03
forum: General Help
---

### Post by pepper454 on 2009-05-03
Please help me with the proper commands to boot windows from grub. Below is my Hard drive setup.  I have tried various things, the closest I get puts me back at the grub menu.  The other system response which made me think I was close was something about needing to loat the kernel first.  Windows is sdc1.  The default after grub install just makes the computer keep beeping at me..

title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

Thanks for any help

```
p31@p31-desktop:~$ sudo fdisk -l /dev/sdc
[sudo] password for p31: 

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad66ad66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20398   163846903+   7  HPFS/NTFS
/dev/sdc2           20399       25498    40965750   1c  Hidden W95 FAT32 (LBA)
/dev/sdc3           25499       29323    30724312+  83  Linux
/dev/sdc4           29324       30401     8659035   82  Linux swap / Solaris
p31@p31-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0 1465138584 sda
   8        1 1465136001 sda1
   8       16 1465138584 sdb
   8       17 1465136001 sdb1
   8       32  244198584 sdc
   8       33  163846903 sdc1
   8       34   40965750 sdc2
   8       35   30724312 sdc3
   8       36    8659035 sdc4
   8       80     500472 sdf
   8       81     500440 sdf1
p31@p31-desktop:~$
```

---

### Post by Legace on 2009-05-03
Try this (I think you missed **makeactive**):

```
title		Microsoft Windows XP
rootnoverify	(hd2,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by zeex on 2009-05-03
> **pepper454 said:**
> Please help me with the proper commands to boot windows from grub. Below is my Hard drive setup.  I have tried various things, the closest I get puts me back at the grub menu.  The other system response which made me think I was close was something about needing to loat the kernel first.  Windows is sdc1.  The default after grub install just makes the computer keep beeping at me..

title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

Thanks for any help

p31@p31-desktop:~$ sudo fdisk -l /dev/sdc
[sudo] password for p31: 

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad66ad66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20398   163846903+   7  HPFS/NTFS
/dev/sdc2           20399       25498    40965750   1c  Hidden W95 FAT32 (LBA)
/dev/sdc3           25499       29323    30724312+  83  Linux
/dev/sdc4           29324       30401     8659035   82  Linux swap / Solaris
p31@p31-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0 1465138584 sda
   8        1 1465136001 sda1
   8       16 1465138584 sdb
   8       17 1465136001 sdb1
   8       32  244198584 sdc
   8       33  163846903 sdc1
   8       34   40965750 sdc2
   8       35   30724312 sdc3
   8       36    8659035 sdc4
   8       80     500472 sdf
   8       81     500440 sdf1
p31@p31-desktop:~$

Hi, 

can you describe your setup like how many drives you have and what kind (SATA/IDE)?

and output of 
```

$ sudo fdisk -l
```

---

### Post by pepper454 on 2009-05-03
> **Legace said:**
> Try this (I think you missed **makeactive**):

```
title        Microsoft Windows XP
rootnoverify    (hd2,0)
savedefault
makeactive
chainloader    +1
```

This just stalls on Starting Up......
Windows is on the same disk as ubuntu
ubuntu boots from (hd0,2)

---

### Post by pepper454 on 2009-05-03
> **zeex said:**
> Hi, 

can you describe your setup like how many drives you have and what kind (SATA/IDE)?

and output of 
```

$ sudo fdisk -l
```

1.5TB on sata 1 of motherboard
1.5TB on sata 2 of motherboard
250gb on only motherboard IDE master (multiple partitions)
Optical on only motherboard IDE slave
Optical on IDE pci card

Output of ```

$ sudo fdisk -l
```

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1973754c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x914c79b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad66ad66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20398   163846903+   7  HPFS/NTFS
/dev/sdc2           20399       25498    40965750   1c  Hidden W95 FAT32 (LBA)
/dev/sdc3           25499       29323    30724312+  83  Linux
/dev/sdc4           29324       30401     8659035   82  Linux swap / Solaris

Disk /dev/sdf: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0049e089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          63      500440+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(61, 254, 63) logical=(62, 77, 63)
```

---

### Post by pepper454 on 2009-05-03
title        Microsoft Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1 

The above gives me...

Starting Up.....
Loading Grub Stage 2

Then puts me back at the grub menu.

---

### Post by caljohnsmith on 2009-05-03
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

Regards,
John

---

### Post by pepper454 on 2009-05-03
Below is the output from [bootinfoscript]("https://sourceforge.net/projects/bootinfoscript/")


```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub4Dos is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 413042458 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /grldr /GRLDR

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1973754c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x914c79b7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad66ad66

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   327,693,869   327,693,807   7 HPFS/NTFS
/dev/sdc2         327,693,870   409,625,369    81,931,500  1c Hidden W95 FAT32 (LBA)
/dev/sdc3         409,625,370   471,073,994    61,448,625  83 Linux
/dev/sdc4         471,073,995   488,392,064    17,318,070  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0049e089

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63     1,000,943     1,000,881   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="152C6DAC7D18A7A9" TYPE="ntfs" 
/dev/sdb1: UUID="7E3898CB389883B5" TYPE="ntfs" 
/dev/sdc3: UUID="445b419e-e9ee-47bf-84fd-963aae46159d" TYPE="ext4" 
/dev/sdc4: UUID="d3ee1afe-51d5-4a7a-a05d-af71c749b73d" TYPE="swap" 
/dev/sdf1: SEC_TYPE="msdos" LABEL="512MB CF" UUID="2C4B-738E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc3 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/p31/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=p31)
/dev/sdf1 on /media/512MB CF type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sdc3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=445b419e-e9ee-47bf-84fd-963aae46159d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=445b419e-e9ee-47bf-84fd-963aae46159d

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        445b419e-e9ee-47bf-84fd-963aae46159d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=445b419e-e9ee-47bf-84fd-963aae46159d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        445b419e-e9ee-47bf-84fd-963aae46159d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=445b419e-e9ee-47bf-84fd-963aae46159d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        445b419e-e9ee-47bf-84fd-963aae46159d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
##title        Microsoft Windows XP Professional
##rootnoverify    (hd2,0)
##savedefault
##map        (hd0) (hd2)
##map        (hd2) (hd0)
##chainloader    +1
title        Microsoft Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1



=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=445b419e-e9ee-47bf-84fd-963aae46159d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc4 during installation
UUID=d3ee1afe-51d5-4a7a-a05d-af71c749b73d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


 211.5GB: boot/grub/menu.lst
 211.4GB: boot/grub/stage2
 211.4GB: boot/initrd.img-2.6.28-11-generic
 211.6GB: boot/vmlinuz-2.6.28-11-generic
 211.4GB: initrd.img
 211.6GB: vmlinuz

================================ sdf1/menu.lst: ================================

timeout 60 
default 0 
 
title Boot from Hard Drive 
rootnoverify (hd0,0) 
chainloader (hd0,0)+1 
 
title -------------------- 
root 
 
title Start Hiren's BootCD 
find --set-root /HBCD/boot.gz 
map --mem /HBCD/boot.gz (fd0) 
map --hook 
chainloader (fd0)+1 
rootnoverify (fd0) 
map --floppies=1 
boot 
 
title Mini Windows Xp 
find --set-root /HBCD/XPLOADER.BIN 
chainloader /HBCD/XPLOADER.BIN 

=================== sdf1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdg sdh 
```

---

### Post by caljohnsmith on 2009-05-03
> **pepper454 said:**
> 
```

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  [COLOR="Red"]Grub0.97 is installed in the boot sector of sdc1[/COLOR] and 
                       looks at sector 413042458 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

```
As shown highlighted in red, it looks like the main issue is that you accidentally installed Grub at some point to the boot sector of your Windows sdc1 partition. To fix it, you can boot your Windows XP Install CD, go to the "recovery console", and first run:
```
map
```
That will show a list of your partitions and corresponding drive letters, so find the one that is sdc1 and then run:
```
fixboot C:
```
But replace "C" if the drive letter for your Windows sdc1 partition is different. Also, you will need to reinstall Grub to the MBR (Master Boot Record) of that drive, so how about doing:
```
sudo grub
grub> root (hd2,2)
grub> setup (hd2)
grub> quit
```
Then reboot, and you should be able to boot Ubuntu and Windows from your Grub menu. Let me know how it goes or if you run into problems.

John

---

### Post by pepper454 on 2009-05-03
> **caljohnsmith said:**
> Then reboot, and you should be able to boot Ubuntu and Windows from your Grub menu. Let me know how it goes or if you run into problems.

John


Followed your direction and everything is up and running properly.
Thank you.

---

### Post by caljohnsmith on 2009-05-03
> **pepper454 said:**
> Followed your direction and everything is up and running properly.
Thank you.
Glad to hear your dual-boot is working OK now. Cheers and enjoy your OSes. :)

John

---

