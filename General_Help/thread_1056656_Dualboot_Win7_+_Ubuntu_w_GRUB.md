---
title: "Dualboot Win7 + Ubuntu w/ GRUB"
date: 2009-02-01
forum: General Help
---

### Post by imnotbncre8ive on 2009-02-01
Hello everyone. I'm sure you guys get people with this problem constantly, so my apologies. I've read several similar threads and looked across websites, but I have not been able to resolve my issue.

I had Win7 installed on an 80GB harddrive. Later, I installed Ubuntu onto a second 40GB harddrive. I would like to be able to boot Win7 from GRUB now. I have tried modifying the 'menu.lst' file, but to no avail.

Here is the information returned by fdisk -lu
--------------------------------------------
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x156f156e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7f81c39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   156297215    78147584    7  HPFS/NTFS
-------------------------------------

Here is what I have entered into 'menu.lst'
--------------------------------------
title		Windows 7 Beta 1
rootnoverify	(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
--------------------------------------

When I choose the option in GRUB, I receive the error
'Invalid or unsupported executable format'

Any and all help is greatly appreciated.

---

### Post by caljohnsmith on 2009-02-01
It looks like the issue might be that you are booting the sdb drive on start up instead of the sda drive. How about trying this entry for Windows:
```
title Windows 7
root (hd0,0)
chainloader +1
```
If that doesn't work, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to booting Win 7 from Grub might be.

---

### Post by imnotbncre8ive on 2009-02-01
(This is an extra post by mistake. Sry bout that.)

---

### Post by imnotbncre8ive on 2009-02-01
I appreciate your help and suggestions.

I first tried changing the Win7's GRUB entry to what you suggested, but it did not work. I think I have tried using (hd0,0) before but Win7 is installed on the 80GB drive, and that one is designated hdb now I believe. In any case, I ran the script you direct me to and here are the results:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x156f156e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,862,899    74,862,837  83 Linux
/dev/sda2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7f81c39

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   156,297,215   156,295,168   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b55ace9c-8d57-4b91-98a0-a0a9736ee6a4" TYPE="ext3" 
/dev/sda5: UUID="2eb9a806-1d7d-4299-b045-f83a191c1267" TYPE="swap" 
/dev/sdb1: UUID="4CF0CD3BF0CD2C50" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tonka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tonka)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows 7 Beta 1
root		(hd0,0)
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b55ace9c-8d57-4b91-98a0-a0a9736ee6a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=2eb9a806-1d7d-4299-b045-f83a191c1267 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  16.1GB: boot/grub/menu.lst
  16.1GB: boot/grub/stage2
  16.2GB: boot/initrd.img-2.6.24-19-generic
  16.1GB: boot/initrd.img-2.6.27-11-generic
  16.1GB: boot/vmlinuz-2.6.24-19-generic
  16.1GB: boot/vmlinuz-2.6.27-11-generic
  16.1GB: initrd.img
  16.2GB: initrd.img.old
  16.1GB: vmlinuz
  16.1GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-01
Of the two Windows entries you have tried so far, did one of them return a "BOOTMGR missing" error? If so, that's the entry you should use. It looks like the issue right now is that your Win 7 partition is missing its boot files, so probably when you installed Win 7, Win 7 put its boot files on the sda drive. Then when you installed Ubuntu to sda, you would have unintentionally deleted Win 7's boot files. But the bottom line is you'll need to restore Windows 7 boot files in order to boot Windows 7 again. I would recommend following step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore your Win 7 boot files. You can skip step 1 and 3 of that tutorial, and also you can skip the "bootsect" command in step 2 since your Windows boot sector appears to be fine according to the script results. Also, I would recommend reading through this recent thread:

[http://ubuntuforums.org/showthread.php?p=6657699](http://ubuntuforums.org/showthread.php?p=6657699)

Good luck and let me know how it goes or if you run into problems.

---

### Post by meierfra. on 2009-02-01
> I would recommend following step 2 of this tutorial for how to restore your Win 7 boot files. You can skip step 1 and 3 of that tutorial, and also you can skip the "bootsect" command in step 2 since your Windows boot sector appears to be fine according to the script results. Also, I would recommend reading through this recent thread:

[http://ubuntuforums.org/showthread.php?p=6657699](http://ubuntuforums.org/showthread.php?p=6657699)

I just updated that  tutorial.  It should now work  without having to read  through  the recent thread.

---

