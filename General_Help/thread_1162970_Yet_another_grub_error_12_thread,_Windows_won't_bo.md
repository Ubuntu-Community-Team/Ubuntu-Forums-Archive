---
title: "Yet another grub error 12 thread, Windows won't boot"
date: 2009-05-18
forum: General Help
---

### Post by fung on 2009-05-18
I've spent the last 6 hours (there were lots of search hits) trying to get windows to start working and so far all efforts have failed and frankly I want to sleep.

I am receiving error 12 when I try to boot into XP. I think this started occuring after I combined a couple pointless partitions and all the labels changed. I'm all out of ideas. Here's the output from boot_info_script032.sh.

PS I don't know why there's a random reference to Vista. I had it installed a LONG time ago but since removed it in favor of XP so there are only 2 OS on here, not 3.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc7 and 
                       looks at sector 105184128 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b4b782e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,522,143 1,953,522,081   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x174af2a2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf701103e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   209,760,704   209,744,640   5 Extended
/dev/sdc5              16,128   104,888,384   104,872,257   7 HPFS/NTFS
/dev/sdc6         205,567,803   209,760,704     4,192,902  82 Linux swap / Solaris
/dev/sdc7         104,888,448   143,958,464    39,070,017  83 Linux
/dev/sdc8         143,958,528   205,567,739    61,609,212  83 Linux
/dev/sdc2    *    209,760,705   419,489,279   209,728,575   7 HPFS/NTFS
/dev/sdc3         419,489,280   976,768,064   557,278,785   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ECB4C6B1B4C67D98" TYPE="ntfs" 
/dev/sdb1: UUID="79B6434811116EE3" LABEL="data" TYPE="ntfs" 
/dev/sdc2: UUID="9EE06255E0623425" LABEL="SeaDat1" TYPE="ntfs" 
/dev/sdc3: UUID="7164B92464B53758" TYPE="ntfs" 
/dev/sdc5: UUID="7880DCEF80DCB4BA" TYPE="ntfs" 
/dev/sdc6: UUID="a9663301-606b-4f19-8254-a7287bbc9b30" TYPE="swap" 
/dev/sdc7: UUID="fec272ce-b819-465c-8463-296a7cc8c2a7" TYPE="ext4" 
/dev/sdc8: UUID="81d17a7e-89fe-487e-a246-263b7312e925" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdc7 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-12-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc8 on /home type ext4 (rw,relatime)
/dev/sdb1 on /media/sdb1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc2 on /media/sdc2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc3 on /media/sdc3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /media/sdc5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


=========================== sdc7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fec272ce-b819-465c-8463-296a7cc8c2a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fec272ce-b819-465c-8463-296a7cc8c2a7

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		fec272ce-b819-465c-8463-296a7cc8c2a7
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=fec272ce-b819-465c-8463-296a7cc8c2a7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		fec272ce-b819-465c-8463-296a7cc8c2a7
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=fec272ce-b819-465c-8463-296a7cc8c2a7 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		fec272ce-b819-465c-8463-296a7cc8c2a7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fec272ce-b819-465c-8463-296a7cc8c2a7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fec272ce-b819-465c-8463-296a7cc8c2a7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fec272ce-b819-465c-8463-296a7cc8c2a7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fec272ce-b819-465c-8463-296a7cc8c2a7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc5
title		Windows XP Professional x64 Edition
rootnoverify	(hd2,4)
savedefault
makeactive
map		(hd0,0) (hd2,4)
map		(hd2,4) (hd0,0)
chainloader	+1


=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdc7 during installation
UUID=fec272ce-b819-465c-8463-296a7cc8c2a7  /               ext4         relatime,errors=remount-ro  0  1  
# /home was on /dev/sdc8 during installation
UUID=81d17a7e-89fe-487e-a246-263b7312e925  /home           ext4         relatime                    0  2  
# swap was on /dev/sdc6 during installation
UUID=a9663301-606b-4f19-8254-a7287bbc9b30  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb2                                  /media/sdb2     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb3                                  /media/sdb3     ntfs         defaults                    0  0  
/dev/sdb4                                  /media/sdb4     ntfs         defaults                    0  0  
/dev/sdc2                                  /media/sdc2     ntfs         defaults                    0  0  
/dev/sdc3                                  /media/sdc3     ntfs         defaults                    0  0  
/dev/sdc4                                  /media/sdc4     ntfs         defaults                    0  0  
/dev/sdc5                                  /media/sdc5     ntfs         defaults                    0  0  

=================== sdc7: Location of files loaded by Grub: ===================


  55.7GB: boot/grub/menu.lst
  53.8GB: boot/grub/stage2
  56.6GB: boot/initrd.img-2.6.28-11-generic
  58.0GB: boot/initrd.img-2.6.28-12-generic
  55.5GB: boot/vmlinuz-2.6.28-11-generic
  54.4GB: boot/vmlinuz-2.6.28-12-generic
  58.0GB: initrd.img
  56.6GB: initrd.img.old
  54.4GB: vmlinuz
  55.5GB: vmlinuz.old

================================ sdc2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer

```

Thanks. I'm going to go take a nap. ):P

---

### Post by fung on 2009-05-18
shameless bump

---

### Post by fung on 2009-05-18
come on guys =( my games are just sitting there lonely and unplayed! just waiting for me to go back to them.

---

