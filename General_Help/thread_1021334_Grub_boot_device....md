---
title: "Grub boot device..."
date: 2008-12-25
forum: General Help
---

### Post by Linuxas on 2008-12-25
Merry Christmas everyone:)
Here is my story. I have an asus eee 1000h with windows xp home installed. I installed eeeubuntu in my new supertalent pico-d 8gb. I aslso have a 2gb usb drive. I extracted eeeubuntu in my 2gb drive with unetbuttin in order to emulate a live cd and install eeeubuntu in my 8gb drive. So at the boot sequence i selected as first drive my 2gb kingston drive (then my sata drive and then my 8gb drive). My pc booted from the 2gb drive and i selected to install eeeubuntu in my 8gb drive. The installation was succesful and i removed my 2gb before restart. When i boot up my system with only the 8gb drive and my main sata drive on, i got an "grub error 21". I made every change possible at the boot sequence between those two, but the error was the same. When i inserted the 2gb drive and boot up my system(the boot sequence was 1st sata,2nd 2gb, 3d 8gb) grub menu appeared and i was able to enter eeeubuntu as well as windows.
Now my question is, how can i fix this issue? I want to boot my pc with only the 8gb drive attached, and not both usb drives. If it is possible i would prefer to boot my pc and run windows amd when i insert my 8gb drive to have the option of getting into eeeubuntu.
Thank you for your help!

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Linuxas on 2008-12-25
Here are the results:
Grub is installed in the MBR of /dev/sda and looks on boot drive #3 in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on boot drive #3 in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdc and looks on the same drive in partition #1 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sda2:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda3:
    File system:  
    Boot sector  type:  No Boot Loader
    Mounting failed:  
mount: you must specify the filesystem type

sdb1:
    File system:  vfat
    Boot sector  type:  Fat32
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 32.
    Operating System: 
    Boot files/directories present: 

sdc1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04.1 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2:
    File system:  Extended Partition

sdc5:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e24ae19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   167750729    83875333+   7  HPFS/NTFS
/dev/sda2       167750730   312496379    72372825    7  HPFS/NTFS
/dev/sda3       312496380   312576704       40162+  ef  EFI (FAT-12/16/32)

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK


Disk /dev/sdb: 2009 MB, 2009071616 bytes
13 heads, 45 sectors/track, 6707 cylinders, total 3923968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3923967     1961968    6  FAT16

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK
Warning: partition 1 extends past end of disk


Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    14892254     7446096   83  Linux
/dev/sdc2        14892255    15647309      377527+   5  Extended
/dev/sdc5        14892318    15647309      377496   82  Linux swap / Solaris

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK
Warning: partition 1 extends past end of disk
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

/dev/sda1: UUID="DAE41A35E41A13FB" TYPE="ntfs" 
/dev/sda2: UUID="76D84C35D84BF243" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="E0FD-1813" TYPE="vfat" 
/dev/sdc1: UUID="8a7ed973-acc9-4b03-8076-cc0ffe1243c5" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="afb266d0-ff22-40f9-be45-1e306b615c25" 

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


sdc1/boot/grub/menu.lst

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
# kopt=root=UUID=8a7ed973-acc9-4b03-8076-cc0ffe1243c5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=8a7ed973-acc9-4b03-8076-cc0ffe1243c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=8a7ed973-acc9-4b03-8076-cc0ffe1243c5 ro single
initrd		/boot/initrd.img-2.6.24-21-eeepc

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
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


sdc1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=8a7ed973-acc9-4b03-8076-cc0ffe1243c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=afb266d0-ff22-40f9-be45-1e306b615c25 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdc1/boot

total 12872
drwxr-xr-x  3 root root    4096 2008-12-25 21:59 .
drwxr-xr-x 21 root root    4096 2008-12-25 21:59 ..
-rw-r--r--  1 root root   67648 2008-08-22 23:03 config-2.6.24-21-eeepc
drwxr-xr-x  2 root  999    4096 2008-12-25 21:59 grub
-rw-r--r--  1 root  999 5106003 2008-12-25 21:59 initrd.img-2.6.24-21-eeepc
-rw-r--r--  1 root root 5111267 2008-08-24 19:35 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r--  1 root root  103204 2008-08-22 23:03 memtest86+.bin
-rw-r--r--  1 root root  879903 2008-08-22 23:03 System.map-2.6.24-21-eeepc
-rw-r--r--  1 root root 1850200 2008-08-22 23:03 vmlinuz-2.6.24-21-eeepc

sdc1/boot/grub

total 204
drwxr-xr-x 2 root  999   4096 2008-12-25 21:59 .
drwxr-xr-x 3 root root   4096 2008-12-25 21:59 ..
-rw-r--r-- 1 root  999    197 2008-12-25 21:59 default
-rw-r--r-- 1 root  999     45 2008-12-25 21:59 device.map
-rw-r--r-- 1 root  999   8056 2008-12-25 21:59 e2fs_stage1_5
-rw-r--r-- 1 root  999   7904 2008-12-25 21:59 fat_stage1_5
-rw-r--r-- 1 root  999     16 2008-12-25 21:59 installed-version
-rw-r--r-- 1 root  999   8608 2008-12-25 21:59 jfs_stage1_5
-rw-r--r-- 1 root root   4559 2008-12-25 21:59 menu.lst
-rw-r--r-- 1 root  999   7324 2008-12-25 21:59 minix_stage1_5
-rw-r--r-- 1 root  999   9632 2008-12-25 21:59 reiserfs_stage1_5
-rw-r--r-- 1 root  999    512 2008-12-25 21:59 stage1
-rw-r--r-- 1 root  999 108356 2008-12-25 21:59 stage2
-rw-r--r-- 1 root  999   9276 2008-12-25 21:59 xfs_stage1_5

StdErr Messages 

boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 8cd: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 8cd: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 00: command not found
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: [: missing `]'
boot_info_script.txt: line 326: 00: command not found

---

### Post by caljohnsmith on 2008-12-25
I think the most ideal solution for your situation is if you can go into your BIOS and set the 8 GB USB drive to boot first. If you can do that, you should at least get a Grub menu on start up, but you'll need to tweak whichever Ubuntu entry you choose slightly in order to boot into Ubuntu: when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd2,0)", change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hd2,0)" to use the (hd0,0) that worked to boot Ubuntu:
```
# groot=(hd0,0)
```
And also replace your existing Windows entry near the bottom of the file with:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
Try rebooting and see if either of the two Windows entries in your Grub menu work; if neither does, be sure to let me know exactly what happens when you select each one, but one of them should work. If everything above works OK and you are then able to boot Ubuntu and Windows from your Grub menu, the last thing to do would be to restore a Windows MBR to your Windows drive, but first let me know how far you get or if you run into problems; we can work from there.

---

### Post by Linuxas on 2008-12-25
> So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hd2,0)" to use the (hd0,0) that worked to boot Ubuntu:
```
# groot=(hd0,0)
```
And also replace your existing Windows entry near the bottom of the file with:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1


Save, quit gedit, then run:
sudo update-grub
``` 
Amazing! It worked just perfectly! Thank you very much!
I still though haven't understand what was the real problem shown in the RESULTS.txt and how you realized which was the problem exactly(in order to know next time) but anyway.
> 
If everything above works OK and you are then able to boot Ubuntu and Windows from your Grub menu, the last thing to do would be to restore a Windows MBR to your Windows drive, but first let me know how far you get or if you run into problems; we can work from there.

So now that Windows and Ubuntu boot without any problems, do i have to do anything else?

---

### Post by caljohnsmith on 2008-12-25
That's great, I'm glad to hear it worked OK. It would be best to go ahead and restore a Windows MBR to your Windows sda drive, because currently the sda drive has Grub in the MBR. If you restore a Windows MBR to sda, then you should be able to boot into Windows even if something happens to your Ubuntu drive (including simply disconnecting the Ubuntu drive). So if that sounds good to you, just do:
```
sudo lilo -M  /dev/sda mbr
```
And you should be all set. :)

---

### Post by Linuxas on 2008-12-25
> **caljohnsmith said:**
> That's great, I'm glad to hear it worked OK. It would be best to go ahead and restore a Windows MBR to your Windows sda drive, because currently the sda drive has Grub in the MBR. If you restore a Windows MBR to sda, then you should be able to boot into Windows even if something happens to your Ubuntu drive (including simply disconnecting the Ubuntu drive). So if that sounds good to you, just do:
```
sudo lilo -M  /dev/sda mbr
```
And you should be all set. :)

I give: sudo lilo -M  /dev/sda mbr but it returns: sudo: lilo: command not found

---

### Post by caljohnsmith on 2008-12-25
> **Linuxas said:**
> I give: sudo lilo -M  /dev/sda mbr but it returns: sudo: lilo: command not found
OK, try then:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And let me know if that works or not.

---

### Post by Linuxas on 2008-12-25
> **caljohnsmith said:**
> OK, try then:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And let me know if that works or not.

I enabled some repositories and installed lilo.
I successfully gave sudo lilo -M  /dev/sda mbr. Now i can boot directly to windows without the usb attached! When i use my usb drive there is a grub menu waiting for me, so i can choose Ubuntu! It's such things that make me admire Linux and its users! you can adjust everything in your system! Thank you very very much for your help!:)

---

### Post by caljohnsmith on 2008-12-25
> **Linuxas said:**
> I enabled some repositories and installed lilo.
I successfully gave sudo lilo -M  /dev/sda mbr. Now i can boot directly to windows without the usb attached! When i use my usb drive there is a grub menu waiting for me, so i can choose Ubuntu! It's such things that make me admire Linux and its users! you can adjust everything in your system! Thank you very very much for your help!:)
Glad to hear it's working the way it should now. Cheers, have fun with Windows and Ubuntu, and have a Merry Christmas. :)

---

