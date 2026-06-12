---
title: "Boot Help"
date: 2009-03-01
forum: General Help
---

### Post by hothail on 2009-03-01
I have 2 hard drives, my main 320 GB and secondary 640 GB.

I have installed Ubuntu on the 320 GB hard drive. After reboot it stopped at Verifying DMI Pool Data.

I rebooted the computer and went into the boot menu.  From here I can select any drive to boot from, so by complete accident I selected my secondary  640 GB.

Ubuntu was able to boot, once it booted I verified that I did in fact install it on my 320 GB.  

Now and every time I boot I have to select my secondary hard drive when it’s not even formatted yet. 

What is the problem and how can I fix this?

---

### Post by hothail on 2009-03-01
bump

---

### Post by caljohnsmith on 2009-03-01
It sounds like you may have Grub installed to the MBR (Master Boot Record) of your 640 GB drive, but to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by hothail on 2009-03-01
Ok here is what is in the text file.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000320aa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   606,919,634   606,919,572  83 Linux
/dev/sdb2         606,919,635   625,137,344    18,217,710   5 Extended
/dev/sdb5         606,919,698   625,137,344    18,217,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="717aad43-9160-47bb-ac65-aaabb8b2d88d" TYPE="ext3" 
/dev/sdb5: UUID="5982f33c-9174-421f-abe2-d40375a18863" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gamer11114/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gamer11114)


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=717aad43-9160-47bb-ac65-aaabb8b2d88d

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
uuid		717aad43-9160-47bb-ac65-aaabb8b2d88d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		717aad43-9160-47bb-ac65-aaabb8b2d88d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		717aad43-9160-47bb-ac65-aaabb8b2d88d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		717aad43-9160-47bb-ac65-aaabb8b2d88d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		717aad43-9160-47bb-ac65-aaabb8b2d88d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=717aad43-9160-47bb-ac65-aaabb8b2d88d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5982f33c-9174-421f-abe2-d40375a18863 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 136.9GB: boot/grub/menu.lst
 136.9GB: boot/grub/stage2
 136.9GB: boot/initrd.img-2.6.27-11-generic
 136.9GB: boot/initrd.img-2.6.27-7-generic
 136.9GB: boot/vmlinuz-2.6.27-11-generic
 136.9GB: boot/vmlinuz-2.6.27-7-generic
 136.9GB: initrd.img
 136.9GB: initrd.img.old
 136.9GB: vmlinuz
 136.9GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-03-01
OK, how about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot your Ubuntu drive, and you should be able to boot into Ubuntu. Let me know how that goes or if you run into problems.

---

### Post by hothail on 2009-03-01
I will try this in a half hour or so then post to tell you how it goes.

---

### Post by hothail on 2009-03-01
thanks alot caljohnsmith, it worked perfectly!

---

### Post by caljohnsmith on 2009-03-01
Glad to hear that worked OK; cheers and enjoy your Ubuntu install. :)

---

