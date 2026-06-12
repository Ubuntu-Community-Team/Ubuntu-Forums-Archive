---
title: "Installed BURG. Having Boot problems."
date: 2010-11-27
forum: Desktop Environments
---

### Post by Aryamaan on 2010-11-27
I installed BURG on my computer through Ubuntu 10.10 following the instructions at google code. After restarting my computer in the boot screen it says

```
Boot from CD/DVD:
GRUB loading.
error: no such device <a lot of alpha-numerical symbols>
Entering rescue mode...
grub rescue>
```Could someone please help me restore GRUB ?

---

### Post by Aryamaan on 2010-11-27
Also, I am using the Ubuntu 10.10 CD to use ubuntu. That's how I posted this thread.

---

### Post by sikander3786 on 2010-11-27
We need some more info.

Please boot into a Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Don't forget to wrap your output with proper code tags # from the post menu. [/code] at the end and [code] at the beginning.

---

### Post by Aryamaan on 2010-11-27
Here it is:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda8/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   976,768,064   874,369,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   307,194,929   204,796,557   7 HPFS/NTFS
/dev/sda6         307,194,993   511,991,549   204,796,557   7 HPFS/NTFS
/dev/sda7         511,991,613   716,788,169   204,796,557   7 HPFS/NTFS
/dev/sda8         716,788,233   778,220,729    61,432,497   7 HPFS/NTFS
/dev/sda9         921,584,853   974,390,444    52,805,592  83 Linux
/dev/sda10        974,390,508   976,768,064     2,377,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       256ae9f2-7303-472a-b670-993e2dca797b   ext4                                     
/dev/sda10       5e393b70-10b6-4bb4-8087-278c385ae028   swap                                     
/dev/sda1        FAA85462A8542005                       ntfs       Local Disk                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7AD85F92D85F4C0F                       ntfs       Local Disk                    
/dev/sda6        2010648F10646DAA                       ntfs       Games                         
/dev/sda7        D0D86A32D86A174E                       ntfs       Movies                        
/dev/sda8        DE8471D78471B31F                       ntfs       Ubuntu                        
/dev/sda9        75049b18-88c6-4c42-b5c8-7052f9fe6762   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda9        /media/75049b18-88c6-4c42-b5c8-7052f9fe6762 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Games             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/Local Disk_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda8/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   ipv6.disable=1 quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   ipv6.disable=1 quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set faa85462a8542005
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda8/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda8/Wubi: Location of files loaded by Grub: =================


   2.4GB: boot/grub/grub.cfg
   9.9GB: boot/initrd.img-2.6.35-22-generic
  10.9GB: boot/initrd.img-2.6.35-23-generic
   8.5GB: boot/vmlinuz-2.6.35-22-generic
   7.9GB: boot/vmlinuz-2.6.35-23-generic
  10.9GB: initrd.img
   9.9GB: initrd.img.old
   7.9GB: vmlinuz
   8.5GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=75049b18-88c6-4c42-b5c8-7052f9fe6762

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
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=5e393b70-10b6-4bb4-8087-278c385ae028 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 496.8GB: boot/grub/menu.lst
 496.9GB: boot/grub/stage2
 496.9GB: boot/initrd.img-2.6.28-11-generic
 496.9GB: boot/vmlinuz-2.6.28-11-generic
 496.9GB: initrd.img
 496.9GB: vmlinuz
```

---

### Post by sikander3786 on 2010-11-27
This is a complex setup for me at least. Win XP, Wubi install of 10.10 and a proper install of 9.04. And you tried to install Burg for your Wubi install and that messed up the system as I see Grub2 installed in the MBR now.

What I can advise is to restore the boot for Ubuntu 9.04 and Windows. I don't know if that would also repair the boot for your Wubi install or not. But I think it should.

Follow the steps here to reinstall Grub Legacy.

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

**Remember,** you need an Ubuntu disc of 9.04 or older. The newer releases come with Grub2. You can choose GUI or CLI method, whichever you prefer.

Please let us know about your progress.

---

### Post by Aryamaan on 2010-11-27
Didn't work :/  It asked me to go super user.. which I did. And then asked to type grub. When i did that the terminal said grub is not installed, type apt-get install grub to install it. Which I did. And then followed all the instructions mentioned in the link you sent me. 

```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
root@ubuntu:~# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libschroedinger-1.0-0 libvpx0 libgsm1 libva1 libfaac0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  grub-legacy-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 162 not upgraded.
Need to get 406kB of archives.
After this operation, 1,425kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main grub i386 0.97-29ubuntu60 [406kB]
Fetched 406kB in 7s (53.8kB/s)                                                 
Preconfiguring packages ...
(Reading database ... 125357 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package grub.
(Reading database ... 125133 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu60_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu60) ...
root@ubuntu:~# 
```

---

### Post by sikander3786 on 2010-11-27
I think you need to chroot and remove grub2 before installing Grub legacy. (I apologize, that should have been mentioned in my above post)

See here for details.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You need to only purge Grub2 following that and reinstall using the same instructions as posted above.

---

### Post by Aryamaan on 2010-11-27
Alright.. So i only have to remove grub2 right. I don't have to do step 4 from the link u just mentioned. I should just remove grub 2 and go back to the previous link right ?

---

### Post by Aryamaan on 2010-11-27
Ok. It didn't work.

---

### Post by sikander3786 on 2010-11-27
Please run post the output of bootinfoscript once again as there have been some changes.

Thanks.

---

### Post by bcbc on 2010-11-27
If you install burg from wubi, which you did, then it will not boot. Wubi installs cannot be booted directly from the MBR.

I don't know whether you previously had grub-legacy from your 9.04 install or the windows bootloader in the MBR. But if you had windows, then just reinstall the windows bootloader to fix, then boot wubi and remove burg.

---

### Post by Aryamaan on 2010-11-28
Here's the output of bootinfoscript:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda8/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda9 and 
                       looks at sector 970523861 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   976,768,064   874,369,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   307,194,929   204,796,557   7 HPFS/NTFS
/dev/sda6         307,194,993   511,991,549   204,796,557   7 HPFS/NTFS
/dev/sda7         511,991,613   716,788,169   204,796,557   7 HPFS/NTFS
/dev/sda8         716,788,233   778,220,729    61,432,497   7 HPFS/NTFS
/dev/sda9         921,584,853   974,390,444    52,805,592  83 Linux
/dev/sda10        974,390,508   976,768,064     2,377,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       256ae9f2-7303-472a-b670-993e2dca797b   ext4                                     
/dev/sda10       5e393b70-10b6-4bb4-8087-278c385ae028   swap                                     
/dev/sda1        FAA85462A8542005                       ntfs       Local Disk                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7AD85F92D85F4C0F                       ntfs       Local Disk                    
/dev/sda6        2010648F10646DAA                       ntfs       Games                         
/dev/sda7        D0D86A32D86A174E                       ntfs       Movies                        
/dev/sda8        DE8471D78471B31F                       ntfs       Ubuntu                        
/dev/sda9        75049b18-88c6-4c42-b5c8-7052f9fe6762   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/Local Disk_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Games             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda9        /media/75049b18-88c6-4c42-b5c8-7052f9fe6762 ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda8/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   ipv6.disable=1 quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro   ipv6.disable=1 quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set de8471d78471b31f
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda8 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set faa85462a8542005
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 75049b18-88c6-4c42-b5c8-7052f9fe6762
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda8/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda8/Wubi: Location of files loaded by Grub: =================


   2.4GB: boot/grub/grub.cfg
   9.9GB: boot/initrd.img-2.6.35-22-generic
  10.9GB: boot/initrd.img-2.6.35-23-generic
   8.5GB: boot/vmlinuz-2.6.35-22-generic
   7.9GB: boot/vmlinuz-2.6.35-23-generic
  10.9GB: initrd.img
   9.9GB: initrd.img.old
   7.9GB: vmlinuz
   8.5GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=75049b18-88c6-4c42-b5c8-7052f9fe6762

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
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        75049b18-88c6-4c42-b5c8-7052f9fe6762
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=75049b18-88c6-4c42-b5c8-7052f9fe6762 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=5e393b70-10b6-4bb4-8087-278c385ae028 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 496.8GB: boot/grub/menu.lst
 496.9GB: boot/grub/stage2
 496.9GB: boot/initrd.img-2.6.28-11-generic
 496.9GB: boot/vmlinuz-2.6.28-11-generic
 496.9GB: initrd.img
 496.9GB: vmlinuz
```

---

### Post by Aryamaan on 2010-11-28
I had GRUB as the default bootloader when ubuntu 9.04 and windows was there. I installed 10.04 later inside windows and upgraded from 10.04 to 10.10. So do I still have to try installing the windows bootloader?

---

### Post by bcbc on 2010-11-28
> **Aryamaan said:**
> I had GRUB as the default bootloader when ubuntu 9.04 and windows was there. I installed 10.04 later inside windows and upgraded from 10.04 to 10.10. So do I still have to try installing the windows bootloader?

To reinstall the grub bootloader see this Howto: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Look for the part titled "How to restore the Ubuntu grub bootloader (9.04 and older)"

---

### Post by Aryamaan on 2010-11-28
Is my ubuntu drive sda9 ?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72a672a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60801   437184877+   f  W95 Ext'd (LBA)
/dev/sda5            6375       19122   102398278+   7  HPFS/NTFS
/dev/sda6           19123       31870   102398278+   7  HPFS/NTFS
/dev/sda7           31871       44618   102398278+   7  HPFS/NTFS
/dev/sda8           44619       48442    30716248+   7  HPFS/NTFS
/dev/sda9           57367       60653    26402796   83  Linux
/dev/sda10          60654       60801     1188778+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by Aryamaan on 2010-11-28
Alright. I tried reinstalling GRUB with sda9 as my ubuntu drive. When I restarted i got this:

```
[CENTER]GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions[/CENTER]

grub>
```

So I decided to just restore XP Bootloader. I booted from the XP installation CD. Entered recovery console by pressing r when prompted. Entered windows choice, and typed "bootcfg /rebuild". Then did "fixboot" and finally "fixmbr". So I have my XP Bootloader back. But my wubi install seems to have disappeared from the boot screen.

---

### Post by bcbc on 2010-11-28
> **Aryamaan said:**
> Alright. I tried reinstalling GRUB with sda9 as my ubuntu drive. When I restarted i got this:

```
[CENTER]GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions[/CENTER]

grub>
```

So I decided to just restore XP Bootloader. I booted from the XP installation CD. Entered recovery console by pressing r when prompted. Entered windows choice, and typed "bootcfg /rebuild". Then did "fixboot" and finally "fixmbr". So I have my XP Bootloader back. But my wubi install seems to have disappeared from the boot screen.
You should have just installed the bootloader (fixmbr). I'm not sure what the rebuild command did. Probably you just need to fix the boot.ini - add this line: C:\wubildr.mbr = "Ubuntu"
Look up how to do this - do not do it from a live CD unless you know what you are doing. Search on  support.microsoft.com instead.

---

### Post by Aryamaan on 2010-11-29
Thanks for all the help. It's working now :)

---

