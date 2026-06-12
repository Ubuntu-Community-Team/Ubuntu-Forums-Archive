---
title: "grub error 17. help!"
date: 2009-04-12
forum: General Help
---

### Post by haruX on 2009-04-12
Hi,

I am new to xubuntu since I don't want to use windows anymore and I want to migrate to xubuntu.

2 days ago I installed xubuntu but I do not know where i screwed up. Now i got grub error 17. Now i cannot use my hard disk... I have tried from F1 to F12.. Del.. but i cannot go to bios, boot from cd or anything.. please help me :(

P.S. the error comes after I boot to another "OS" under grub which said something like "Microsoft Vista/Longhorn (Launcher)". I decided to take a look at what is that but it was my acer-emanagement. Given only options to restore factory settings, i decided to exit. After that i got error 17.

-haru

---

### Post by Thura on 2009-04-12
Seems there is a lot of answers already ... Try those first if not yet ...
[http://www.google.com.my/search?hl=en&q=grub+error+17&btnG=Search&meta=](http://www.google.com.my/search?hl=en&q=grub+error+17&btnG=Search&meta=)

---

### Post by haruX on 2009-04-12
> **Thura said:**
> Seems there is a lot of answers already ... Try those first if not yet ...
[http://www.google.com.my/search?hl=en&q=grub+error+17&btnG=Search&meta=](http://www.google.com.my/search?hl=en&q=grub+error+17&btnG=Search&meta=)

i have already tried googling.. its my best friend :(

> **Gambitt said:**
> It looks like your filesystem is not recognized. It means xubuntu can't mount selected partition because the filesystem type cannot be recognized by GRUB.

If you can boot from a live cd, go to a terminal and enter:
sudo fdisk -l    (l is a lowercase L)
This will give you the partitions and formats.

Dont forget to set your BIOS to boot from CD first!

I can't really access the bios.. I tried all those keys to enter but i was greeted with an error no matter what i try to press. If i use it as an external hard disk would it still be workable? Because i am getting a new hard disk this coming wednesday.

But i'll try again later after i reach home.

---

### Post by Jammanuser on 2009-04-12
In my experience with Grub, error 17 means your menu.lst is pointing at the wrong location. Check your /boot/grub/menu.lst, and compare the "root (hdx,y)" device (unless you're using UUID lines instead of 'root') with the location the command **sudo fdisk -l** gives as the location of your root partition from the Terminal, and verify that they are the same. If not, then ajust accordingly.

Cheers.

---

### Post by haruX on 2009-04-13
Hi thanks everyone for the reply.. But i cannot get into bios or anything. It just goes to error 17 every single time (I have tried more then 10 times, thats for sure).

So does it means its a goner with no hope anymore?

---

### Post by meierfra. on 2009-04-13
grub error 17 can have many different causes.  In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and download the Boot Info Script to your desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by haruX on 2009-04-18
Hi. I managed to get it to work. Here it is.

I have one question though. Why do I have 2 ubuntu with different kernel version? Everytime I try running the top one(2.6.24-23-generic). It hangs.

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hda
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hda: 593 MB, 593889280 bytes
255 heads, 63 sectors/track, 18 cylinders, total 289985 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x53b32377

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2          20,466,810   156,858,659   136,391,850   f W95 Ext d (LBA)
/dev/sda5          20,466,873   156,296,384   135,829,512   7 HPFS/NTFS
/dev/sda6         156,296,448   156,858,659       562,212  82 Linux swap / Solaris
/dev/sda3         156,858,660   166,786,829     9,928,170  83 Linux
/dev/sda4    *    166,793,216   312,578,047   145,784,832   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F6524D6AE49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda3: UUID="787c4eb3-ae0e-4a87-b6f6-783e9b7c691b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="56B04411B043F5D1" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="DC949C23949C0266" TYPE="ntfs" 
/dev/sda6: UUID="eae51d30-f4b9-4afd-b14b-5b3a617e4f7e" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev)
/dev/sda1 on /media/PQSERVICE type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,3)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=787c4eb3-ae0e-4a87-b6f6-783e9b7c691b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=eae51d30-f4b9-4afd-b14b-5b3a617e4f7e none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/sda3 /media/DATA ntfs-3g defaults,locale=en_SG.UTF-8 0 0
/dev/sda5 /media/maindrive ntfs-3g defaults,locale=en_SG.UTF-8 0 0

=================== sda3: Location of files loaded by Grub: ===================


  81.6GB: boot/grub/menu.lst
  85.1GB: boot/grub/stage2
  85.1GB: boot/initrd.img-2.6.22-14-generic
  85.1GB: boot/initrd.img-2.6.22-14-generic.bak
  80.5GB: boot/initrd.img-2.6.24-23-generic
  85.3GB: boot/initrd.img-2.6.24-23-generic.bak
  85.1GB: boot/vmlinuz-2.6.22-14-generic
  80.4GB: boot/vmlinuz-2.6.24-23-generic
  80.5GB: initrd.img
  85.1GB: initrd.img.old
  80.4GB: vmlinuz
  85.1GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Jammanuser on 2009-04-18
It is more probable that you have just one Ubuntu, but two kernels, one of them an update that doesn't work. ;) If I were you, I would get rid of the non-working kernel, and update your menu.lst, so you only have entries that actually work in your menu.lst.

---

