---
title: "Dual Boot Confusion."
date: 2009-01-20
forum: General Help
---

### Post by rroze002 on 2009-01-20
Hi all,

I've got Ubuntu and XP installed on two separate HDs.  Is Grub only able to handle multiple os installation on a single disk?  For the past week or so, the only way I've been able to switch between the two OSs is to define the boot order from within the BIOS.  Is there some option in Grub to make it all work or should I be looking for other ways?  

Any help and advice will be appreciated.

Thanks

---

### Post by goinglinux on 2009-01-20
Here is a link to a post on this forum that discusses how to configure GRUB for two hard drives. 

[http://ubuntuforums.org/showthread.php?t=474734]("http://ubuntuforums.org/showthread.php?t=474734")

---

### Post by deadlockedgamer on 2009-01-20
You could make windows the main hard drive and then install Ubuntu on the secondary. It should automatically put the boot loader on the windows hard disk and have a menu with a ten second count down to select an OS. I have done it with 8.04 and 8.1 with two hard drives and it works fine.

---

### Post by rroze002 on 2009-01-20
So I followed the guide to reconfigure Grub, and here is what I got.

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)        
root (hd0,0)
grub> setup (hd1)
setup (hd1)

Error 17: Cannot mount selected partition

Also Im not very sure that the drives are labeled correctly, which could explain the error message.  I believe XP is installed on HD1 and Linux on HD0  Is there an easy way to determine the drive assignments?

---

### Post by Dieseler on 2009-01-20
Hey rr
grub can boot 2 disks.
I can try to help.
I dual boot off two disks also.
Can you post the output of

fdisk -lu

and possibly also your
menu.lst, from inside /  /boot/grub  folder.

And which disk drive do you have set in bios to boot first?
Needs to be your drive with grub.
We can go from there.

---

### Post by caljohnsmith on 2009-01-21
Rroze002, I think it would help to get a clearer picture of your setup in order to figure out what might be the best solution for your situation, so if that sounds OK with you, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what might be the best solution for your booting situation.

---

### Post by rroze002 on 2009-01-21
First of all, thank you all for helping.
Here are the results for fdisk-lu and the boot info script.
*****************
fdisk - lu
*****************
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc55cc55c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000040e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   476359379   238179658+  83  Linux
/dev/sdb2       476359380   488392064     6016342+   5  Extended
/dev/sdb5       476359443   488392064     6016311   82  Linux swap / Solaris

*******************
boot info script
*******************

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 464633919 on boot drive #2 for the 
                       stage2 file and on partition #1 for 
                       /boot/grub/menu.lst .
    Mounting failed:
mount: you must specify the filesystem type

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc55cc55c

/dev/sda1     *           63  488,375,999  488,375,937   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000040e5

/dev/sdb1     *           63  476,359,379  476,359,317  83 Linux
/dev/sdb2        476,359,380  488,392,064   12,032,685   5 Extended
/dev/sdb5        476,359,443  488,392,064   12,032,622  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="533737cc-83ac-4537-8c6f-f60c2b34bac1" TYPE="ext3" 
/dev/sdb5: UUID="b1a418b5-acec-4d0e-8d5f-5dcdca54c86f" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rroze002/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rroze002)

=========================== sdb1/boot/grub/menu.lst: ===========================

hiddenmenu
default 0
timeout 10

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
# kopt=root=UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=533737cc-83ac-4537-8c6f-f60c2b34bac1

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

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=533737cc-83ac-4537-8c6f-f60c2b34bac1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b1a418b5-acec-4d0e-8d5f-5dcdca54c86f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 25484
drwxr-xr-x  3 root root    4096 2009-01-17 19:03 .
drwxr-xr-x 21 root root    4096 2009-01-18 11:53 ..
-rw-r--r--  1 root root  503560 2008-11-04 15:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 18:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 15:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 18:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-18 15:43 grub
-rw-r--r--  1 root root 8648256 2009-01-17 19:02 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8647911 2009-01-17 19:03 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 15:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 18:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 15:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 18:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 15:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 18:30 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2009-01-18 15:43 .
drwxr-xr-x 3 root root   4096 2009-01-17 19:03 ..
-rw-r--r-- 1 root root    197 2009-01-17 18:33 default
-rw-r--r-- 1 root root     15 2009-01-17 18:33 device.map
-rw-r--r-- 1 root root   8108 2009-01-17 18:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-17 18:33 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-17 18:33 installed-version
-rw-r--r-- 1 root root   8712 2009-01-17 18:33 jfs_stage1_5
-rw-r--r-- 1 root root   3142 2009-01-21 18:20 menu.lst
-rw-r--r-- 1 root root   4708 2009-01-17 19:02 menu.lst~
-rw-r--r-- 1 root root   4792 2009-01-18 15:43 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-17 18:33 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-17 18:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-17 18:33 stage1
-rw-r--r-- 1 root root 121460 2009-01-17 18:33 stage2
-rw-r--r-- 1 root root   9556 2009-01-17 18:33 xfs_stage1_5

=================== sdb1: Location  of files loaded by Grub: ===================


 237.9GB: boot/grub/menu.lst
 237.8GB: boot/grub/stage2
 237.8GB: boot/initrd.img-2.6.27-7-generic
 237.9GB: boot/initrd.img-2.6.27-9-generic
 237.8GB: boot/vmlinuz-2.6.27-7-generic
 237.8GB: boot/vmlinuz-2.6.27-9-generic
 237.9GB: initrd.img
 237.8GB: initrd.img.old
 237.8GB: vmlinuz
 237.8GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

---

### Post by caljohnsmith on 2009-01-21
So if you switch your BIOS to boot your Ubuntu drive, can you still boot into Ubuntu OK? I'm wondering because your Ubuntu entries in the Grub menu.lst file don't have a "uuid" or "root" line, and I don't think that will work. Also, it looks like you accidentally did "setup (hd0,0)" in the Grub CLI at some point, because Grub is installed to the boot sector of your Windows sda1 partition. Unfortunately that means you won't be able to mount, read, or boot your Windows partition until you fix that first, so how about booting your Windows XP Install CD, go to the "recovery console" and do:
```
fixboot
```
That should fix Windows, and if you can set your BIOS and boot into Ubuntu OK. If you can boot into Ubuntu OK, how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry for Windows:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If you can't boot into Ubuntu though, let me know and we can work from there. Otherwise let me know how it goes.

---

### Post by rroze002 on 2009-01-24
Thank you caljohnsmith.  Everything works as planned, although I seem to have lost some drivers from my Windows install, probably from having written a new boot section.

---

### Post by NBBTANK on 2009-01-24
Hi Everyone,

I recently installed Ubuntu on one of my hard drives and I have Vista on another. Now I can only boot Ubuntu. I've been reading through this forum, but none of it has helped. I was wondering if anyone might be able to give me some insight on how I fix my computer so that it dual boots Vista and Ubuntu.

Thanks.

---

