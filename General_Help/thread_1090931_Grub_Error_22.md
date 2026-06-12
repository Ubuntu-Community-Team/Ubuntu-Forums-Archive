---
title: "Grub Error 22"
date: 2009-03-08
forum: General Help
---

### Post by Kimos on 2009-03-08
I've been running a stable version of 8.04 since about 08/04. Desktop setup. It's the only OS on the box. I've had no hardware changes lately and no software changes other than regular updates.

Today I rebooted and received "GRUB Error 22". Jiggling cables and unplugging devices did nothing. I could not figure out how to get any more info out of grub other than just that one error code.

I've booted from a live CD and all my partitions and disks are intact. I've tried this suggestion:

```

$ sudo grub

grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)

grub> setup (hd0)

grub> quit

```

Upon reboot, this did nothing.

I'm at a loss for what to even try next. Nothing changed that I know of and the hardware all seems to be working with zero problems off the live CD. I did a fsck of the ext3 partitions for /home and / and they all returned with no problems.

What should I do next?

Attached are things I think may be of interest.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3036       38913   288190035   83  Linux
/dev/sda2            2849        3035     1502077+  82  Linux swap / Solaris
/dev/sda3   *           1        2848    22876528+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x223fcbe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            5111       30401   203149957+  83  Linux
ubuntu@ubuntu:~$ =

```

```
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=769

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ 

```

---

### Post by meierfra. on 2009-03-08
Maybe your computer is  set to boot from your 250GB drive. So I suggest to  change the boot order in bios.

**If this did not solve your problem:** 

In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Kimos on 2009-03-09
It's not set to boot from the 250GB. The root partition is on the larger SATA drive. Perhaps I should have attached this as well:

```
ubuntu@ubuntu:~$ cat /media/disk/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=364fb6a1-cf38-468e-ade4-b034d87990d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/home	ext3	defaults	0	0	
/dev/sdb2	/media/common	ext3	defaults	0	0
ubuntu@ubuntu:~$ 

```

Here's the output from the bootinfoscript:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d8fa9

Partition  Boot         Start           End          Size  Id System

/dev/sda1          48,757,275   625,137,344   576,380,070  83 Linux
/dev/sda2          45,753,120    48,757,274     3,004,155  82 Linux swap / Solaris
/dev/sda3    *             63    45,753,119    45,753,057  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x223fcbe3

Partition  Boot         Start           End          Size  Id System

/dev/sdb2          82,092,150   488,392,064   406,299,915  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3857aa00-b9b1-467b-8e96-f78118ef4e63" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="364fb6a1-cf38-468e-ade4-b034d87990d5" TYPE="swap" 
/dev/sda3: UUID="fd54f936-7e83-4ec3-8fd4-8e55e39c921e" TYPE="ext3" 
/dev/sdb2: LABEL="common" UUID="02c39468-4015-4c98-8b5d-6f48859b9f80" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=769

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fd54f936-7e83-4ec3-8fd4-8e55e39c921e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=364fb6a1-cf38-468e-ade4-b034d87990d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/home	ext3	defaults	0	0	
/dev/sdb2	/media/common	ext3	defaults	0	0

=================== sda3: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/menu.lst
   4.5GB: boot/grub/stage2
   8.2GB: boot/initrd.img-2.6.24-16-generic
   8.0GB: boot/initrd.img-2.6.24-16-generic.bak
   4.4GB: boot/initrd.img-2.6.24-17-generic
   4.4GB: boot/initrd.img-2.6.24-17-generic.bak
   4.4GB: boot/initrd.img-2.6.24-18-generic
   4.4GB: boot/initrd.img-2.6.24-18-generic.bak
   4.2GB: boot/initrd.img-2.6.24-19-generic
   4.2GB: boot/initrd.img-2.6.24-19-generic.bak
   4.3GB: boot/initrd.img-2.6.24-21-generic
   4.2GB: boot/initrd.img-2.6.24-21-generic.bak
   4.3GB: boot/initrd.img-2.6.24-22-generic
   4.3GB: boot/initrd.img-2.6.24-22-generic.bak
   4.2GB: boot/initrd.img-2.6.24-23-generic
   4.5GB: boot/initrd.img-2.6.24-23-generic.bak
   4.2GB: boot/vmlinuz-2.6.24-16-generic
   4.2GB: boot/vmlinuz-2.6.24-17-generic
   4.4GB: boot/vmlinuz-2.6.24-18-generic
   4.2GB: boot/vmlinuz-2.6.24-19-generic
   4.2GB: boot/vmlinuz-2.6.24-21-generic
   4.2GB: boot/vmlinuz-2.6.24-22-generic
   4.5GB: boot/vmlinuz-2.6.24-23-generic
   4.2GB: initrd.img
   4.3GB: initrd.img.old
   4.5GB: vmlinuz
   4.2GB: vmlinuz.old

```

---

### Post by Kimos on 2009-03-09
I've resolved my issue. Thank you for your help meierfra.

The first bit of the output of that script showed that grub was loaded on the MBR of both drives:

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

I had assumed that since I was getting a grub error, the problem was not in the BIOS but was a software issue. Turns out that my 250GB IDE drive which now only contains media/data used to be a primary drive of mine. It still had an old version of grub on the MBR. My BIOS decided to change the boot order of my devices and it first found the old IDE drive rather than booting off my 320GB SCSI. Grub on the old drive pointed to an OS that does not exist anymore and clearly errored.

I have no clue why that setting changed, but I switched it back and everything is as it should be again.

---

### Post by meierfra. on 2009-03-09
> I've resolved my issue. Thank you for your help meierfra.

Glad to be of help.

> I have no clue why that setting changed, 
Maybe a power outage?  Or the CMOS battery might be low.

---

### Post by Kimos on 2009-03-09
> **meierfra. said:**
> 
Maybe a power outage?  Or the CMOS battery might be low.

I restarted the system normally so I doubt it was a power outage, but I'll check the battery. Thanks.

---

