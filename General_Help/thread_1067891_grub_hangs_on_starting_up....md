---
title: "grub hangs on starting up..."
date: 2009-02-12
forum: General Help
---

### Post by chaotzu on 2009-02-12
So I dual boot linux and xp. Ubuntu boots fine, but since my first time trying to boot xp since I installed Ubuntu it hangs at "Starting up..."

Anyone has any suggestions? please!

---

### Post by caljohnsmith on 2009-02-12
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by darco on 2009-02-12
> **chaotzu said:**
> So I dual boot linux and xp. Ubuntu boots fine, but since my first time trying to boot xp since I installed Ubuntu it hangs at "Starting up..."

Anyone has any suggestions? please!

You may have to run the xp recovery disk and run the /fixboot or fixmbr command. Search the forums for more info
good luck
darco

---

### Post by chaotzu on 2009-02-12
Here is the results. I hope i can get some help from this. Thanks in advanced.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c0c0c0c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,752,579   207,752,517   7 HPFS/NTFS
/dev/sda2         207,752,580   312,576,704   104,824,125   5 Extended
/dev/sda5         207,752,643   308,190,959   100,438,317  83 Linux
/dev/sda6         308,191,023   312,576,704     4,385,682  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 2062 MB, 2062548992 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     4,028,408     4,028,346   b W95 FAT32

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   102,832,064   102,832,002   c W95 FAT32 (LBA)
/dev/sdc2         102,832,065   312,576,704   209,744,640   f W95 Ext d (LBA)
Empty Partition


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0010D50610D50396" TYPE="ntfs" 
/dev/sda5: UUID="6ba6e15f-c843-474a-9637-5c7a8fba2a00" TYPE="ext3" 
/dev/sda6: UUID="ad48925b-aa1f-4f9d-a180-d9dc74410774" TYPE="swap" 
/dev/sdb1: UUID="908C-48D7" TYPE="vfat" 
/dev/sdc1: LABEL="WD Passport" UUID="0B9A-ED2E" TYPE="vfat" 

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
gvfs-fuse-daemon on /home/nix/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nix)
/dev/sdc1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer


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
# kopt=root=UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6ba6e15f-c843-474a-9637-5c7a8fba2a00

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
uuid		6ba6e15f-c843-474a-9637-5c7a8fba2a00
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6ba6e15f-c843-474a-9637-5c7a8fba2a00
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6ba6e15f-c843-474a-9637-5c7a8fba2a00
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6ba6e15f-c843-474a-9637-5c7a8fba2a00
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6ba6e15f-c843-474a-9637-5c7a8fba2a00
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6ba6e15f-c843-474a-9637-5c7a8fba2a00 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ad48925b-aa1f-4f9d-a180-d9dc74410774 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 124.8GB: boot/grub/menu.lst
 124.7GB: boot/grub/stage2
 124.7GB: boot/initrd.img-2.6.27-11-generic
 124.8GB: boot/initrd.img-2.6.27-7-generic
 124.8GB: boot/vmlinuz-2.6.27-11-generic
 124.8GB: boot/vmlinuz-2.6.27-7-generic
 124.7GB: initrd.img
 124.8GB: initrd.img.old
 124.8GB: vmlinuz
 124.8GB: vmlinuz.old

```

---

### Post by chaotzu on 2009-02-12
I think fixboot or fixmbr might get rid of grub right? I still wanna use linux though.

Also reading around it seems like the pointer to my partition or whatever might be wrong. Like I might need to fix that code I posted above to swap (hd0,0) (hd0,1). or something like that. I'm not too sure how it works though so I'll take any suggestions.

---

### Post by caljohnsmith on 2009-02-12
Actually your entry for Windows in your Grub's menu.lst is OK. So just to confirm, were you able to boot Windows OK before installing Ubuntu I assume? How about first booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Windows again from Grub and let me know if you get any further. If that doesn't help, how about booting back into Ubuntu, make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD (sda) and "Proceed", choose "Intel", choose "Advanced", select the sda1 Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical (this is probably what testdisk will report) and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

---

### Post by chaotzu on 2009-02-12
Yes i was able to boot into xp with no problem before installing Ubuntu. I'm runing chkdsk in windows recovery now, and I will post results. If they are normal I'll try the ubuntu check too. Thank you for your help.

---

### Post by chaotzu on 2009-02-12
chkdsk said it found and fixed some problems so doing another chkdsk

---

### Post by chaotzu on 2009-02-12
So i installed and ran testdisk like you said and it did say "Extrapolated boot sector and current boot sector are different" so i selected write, and that fixed it. I can now dual boot again.

IOU and thanks again :D

---

### Post by caljohnsmith on 2009-02-12
That's great news, I'm glad testdisk did the trick; cheers and enjoy Ubuntu and Windows. :)

---

