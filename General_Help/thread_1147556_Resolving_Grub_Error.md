---
title: "Resolving Grub Error"
date: 2009-05-03
forum: General Help
---

### Post by KillerSiafu on 2009-05-03
After doing a clean install of 9.04 on my desktop I ran into Grub Error 17.

```
Verifying DMI Pool Data..........
GRUB Loadng stage1.5.

GRUB loading, please wait...
Error 17
```

I believe I know the cause of the problem I just need some help resolving it. The last time this happened, GRUB was just confused which disk to boot from.

The system has 4, 500gb hard drives in software-RAID5 (sda-sdd) and a 160gb hard drive (sde) acting as the main operating system disk. This disk is partitioned into its main partition (sde6) which has the majority of the space and sde5, which acts as swap.

I've run into this problem before, where GRUB is confused which disk to boot from but I haven't been able to resolve it like I was before.

Essentially what I've tried is:

1) Booted the Live CD
2) Created a temp directory
3) Mounted sde6 to the temp directory
4) gksudo gedit temp/boot/grub/menu.lst
5) Played around with the various options in the file, such as groot, etc
6) rebooted the machine

However, I don't think any of the changes I've been making to the menu.lst file have been taking effect. For example, I tried changing the timeout variable from 3 to 15 to see GRUB Loading would wait longer before hitting the error, but it didn't.

So i'm not sure what to try from here. I seem to remember being able to access the GRUB terminal directly during during the GRUB loading stages but I can't seem to be able to do that anymore. I've also pulled the following info:

fdisk -l:

> Disk /dev/sde: 160.0 GB
Disk identifier: 0x00033fe3

Device Boot   Start     End     Blocks    Id   System
/dev/sde1     1         19457   156288321 5    Extended
/dev/sde5     18790     19457     5365710 82   Linux swap / Solaris
/dev/sde6     1         18788   150914515 83   Linux

grub> geometry (hd4)

> drive 0x84: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sde
Partition num: 4, Filesystem type unknown, partition type 0x82
Partition num: 5, Filesystem type ext2fs, partition type 0x83

menu.lst

> kopt=root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro
groot=(hd0,0)

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel        /boot/memtest86+.bin
quiet

---

### Post by caljohnsmith on 2009-05-03
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by KillerSiafu on 2009-05-03
Here ya go:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #5 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Grub0.97 is installed in the MBR of /dev/sde and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdb1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdc1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdd1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sde1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004b0d1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00033fe3

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   312,576,704   312,576,642   5 Extended
/dev/sde5         301,845,285   312,576,704    10,731,420  82 Linux swap / Solaris
/dev/sde6                 189   301,829,219   301,829,031  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="bc192f3c-d9d7-6a37-1364-2eee8b80e522" TYPE="mdraid" 
/dev/sdb1: UUID="bc192f3c-d9d7-6a37-1364-2eee8b80e522" TYPE="mdraid" 
/dev/sdc1: UUID="bc192f3c-d9d7-6a37-1364-2eee8b80e522" TYPE="mdraid" 
/dev/sdd1: UUID="bc192f3c-d9d7-6a37-1364-2eee8b80e522" TYPE="mdraid" 
/dev/sde5: UUID="0dbca8d8-2fac-4793-a8bb-1e4b0a46a6d9" TYPE="swap" 
/dev/sde6: UUID="6e5287ea-7b65-49bf-850b-05b7e00fa39c" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sde6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,5)

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
uuid		6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		6e5287ea-7b65-49bf-850b-05b7e00fa39c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sde6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde6 during installation
UUID=6e5287ea-7b65-49bf-850b-05b7e00fa39c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=0dbca8d8-2fac-4793-a8bb-1e4b0a46a6d9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde6: Location of files loaded by Grub: ===================


  60.9GB: boot/grub/menu.lst
  61.0GB: boot/grub/stage2
  61.0GB: boot/initrd.img-2.6.28-11-generic
  60.9GB: boot/vmlinuz-2.6.28-11-generic
  61.0GB: initrd.img
  60.9GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-05-03
OK, I believe I see the issue, how about doing the following:
```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the sde Ubuntu drive first on start up, and let me know exactly what happens. We can work from there.

John

---

### Post by KillerSiafu on 2009-05-03
Ok here's the output of running those commands... rebooting now

```

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
1+0 records in
1+0 records out
440 bytes (440 B) copied, 0.0074029 s, 59.4 kB/s

```

```

ubuntu@ubuntu:~$ sudo grub

grub> device (hd0) /dev/sde 

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit

```

---

### Post by KillerSiafu on 2009-05-03
Nice I think that got it!

It got past stage 1.5 and went into GRUB loading, I was able to select 9.04 to boot and it appears to be booting from the right partition.

Thanks for the help!

---

### Post by caljohnsmith on 2009-05-03
Glad to hear that did the trick. Cheers and have fun with Ubuntu. :)

John

---

