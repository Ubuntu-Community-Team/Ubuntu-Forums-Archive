---
title: "Error17"
date: 2009-05-14
forum: General Help
---

### Post by tanusgreystar on 2009-05-14
Hi. I have Win XP and Ubuntu dual boot. When I installed Ubuntu I split the 750gb hdd among both os, thinking that I could easily create new partitions within the unused space. I tried different partitioning programs to no avail. I could not get them to lock the hdd (in Windows) and I was going to repartition the Linux side of the hdd later since I couldn't use any program at all to change that. So finally I used Acronis and was able to shrink the WinXp partition and create a 300gb partition for data. Problem is I can't boot into Win or Ubuntu. I get Error17 and no choose OS screen. I can boot into Ubuntu with live cd and supergrub cd, but I have to use the Supergrub cd to boot into Ubuntu. Supergrub lets me see the choose OS screen but when I select Win XP I get a message that NTLDR is missing. I tried to fix the grub with the Supergrub cd unsuccessfully, and I'm really confused on a fix I found in an older post (below):

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition) (I had to use sda6 here)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0) /dev/sda
(hd1) /dev/sdc
(hd2) /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that. This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

I was able to get through steps 1-7, but I am pretty confused about the rest. In device.map I typed everything in quotes but nothing happened. And I couldn't figure out how to exit the device.map. I ended up typing some stuff in the device.map that I can't figure out how to erase. I'm really confused. All my data seems to be intact. I can mount all the HDD, including my WinXP drive and the new partition. I'm still a Linux noob. Sorry such a long post!

---

### Post by spiderbatdad on 2009-05-14
A lot of folks are using this boot info script now to provides a better picture of their systems. [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal: Applications > Accessories > Terminal. Enter:

```
sudo bash ~/Desktop/boot_info_script*.sh
```This assumes you saved the downloaded progam to your desktop. The command will create a "RESULTS.txt" file. Please copy/paste the RESULTS.txt file to your next post. Use code tags around the text by highlighting the text and clicking the # symbol above.

---

### Post by tanusgreystar on 2009-05-14
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ba01ba0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   101,948,489   101,948,427   7 HPFS/NTFS
/dev/sda2         101,948,490 1,465,144,064 1,363,195,575   5 Extended
/dev/sda5         101,948,553   731,102,084   629,153,532   7 HPFS/NTFS
/dev/sda6         731,102,148 1,445,400,179   714,298,032  83 Linux
/dev/sda7       1,445,400,243 1,465,144,064    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x078bcbb0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AADC870BDC86D0CD" TYPE="ntfs" 
/dev/sda5: UUID="E94773F9F2858161" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="97fcdc42-4b09-40f6-b4b1-905118e5657a" TYPE="ext3" 
/dev/sda7: UUID="f7ecab01-843b-48be-be35-2370a9b0eb3f" TYPE="swap" 
/dev/sdb1: UUID="6E1CC2B61CC2789B" LABEL="Music Files" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb1 on /media/Musicfiles type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Music Files type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tanusgreystar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tanusgreystar)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97fcdc42-4b09-40f6-b4b1-905118e5657a

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		97fcdc42-4b09-40f6-b4b1-905118e5657a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1


=============================== sda6/etc/fstab: ===============================


proc /proc proc defaults 0 0
UUID=97fcdc42-4b09-40f6-b4b1-905118e5657a / ext3 relatime,errors=remount-ro 0 1
UUID=f7ecab01-843b-48be-be35-2370a9b0eb3f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Musicfiles ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Music\040Files ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda6: Location of files loaded by Grub: ===================


 450.3GB: boot/grub/menu.lst
 450.3GB: boot/grub/stage2
 450.3GB: boot/initrd.img-2.6.27-11-generic
 450.4GB: boot/initrd.img-2.6.28-11-generic
 450.3GB: boot/vmlinuz-2.6.27-11-generic
 450.3GB: boot/vmlinuz-2.6.28-11-generic
 450.4GB: initrd.img
 450.3GB: initrd.img.old
 450.3GB: vmlinuz
 450.3GB: vmlinuz.old

---

### Post by spiderbatdad on 2009-05-14
I think you should reinstall grub via the live cd. Get a terminal and run:
```
sudo mount /dev/sda6 /mnt
cd /mnt/boot
sudo grub-install --root-directory=/mnt/boot /dev/sda

```This method will overwrite the windows boot loader...which appears to be broken...the NTLDR error.
There is another method used for preserving the windows boot loader. Typically on a Linux system Grub is the boot loader used.
See here for more information on each method: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) You will notice the commands above are slightly different, regarding directories.

---

### Post by tanusgreystar on 2009-05-17
You know what? I used the fix you gave me and not only can I boot into Ubuntu, but I can also boot into Windows! Go figure. I guess the bootloader was fine. Now I have to figure out how to resize my Linux partition.

---

