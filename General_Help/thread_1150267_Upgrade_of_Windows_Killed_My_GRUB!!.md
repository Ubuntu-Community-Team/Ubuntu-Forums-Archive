---
title: "Upgrade of Windows Killed My GRUB!!"
date: 2009-05-05
forum: General Help
---

### Post by DougieFresh4U on 2009-05-05
I had 3 partitions, 2 Ubuntu and Windows. After upgrade of the widows today, I no longer have GRUB menu at the begining of booting machine. I have searched the forums some and I have the following info, so if some one can guide mew please. Using live Jaunty cd at the moment
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d06a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   291,860,866   291,449,219   7 HPFS/NTFS
/dev/sda3         291,868,920   625,137,344   333,268,425   5 Extended
/dev/sda5         611,530,353   625,137,344    13,606,992  82 Linux swap / Solaris
/dev/sda6         291,869,046   431,698,679   139,829,634  83 Linux
/dev/sda7         431,698,743   611,530,289   179,831,547  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0882C33A82C32AD0" TYPE="ntfs" 
/dev/sda2: UUID="8488C08988C07AE6" LABEL="Windows 7 ??" TYPE="ntfs" 
/dev/sda5: UUID="5ee29484-6e54-4799-a6c4-81daab1d8ddc" TYPE="swap" 
/dev/sda6: UUID="b3d866ba-af4a-4234-9a91-03d360a738f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="785fc95b-8e13-4e69-b347-5c7e831952b5" TYPE="ext4" 

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
# kopt=root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b3d866ba-af4a-4234-9a91-03d360a738f0

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
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5ee29484-6e54-4799-a6c4-81daab1d8ddc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 214.0GB: boot/grub/menu.lst
 214.0GB: boot/grub/stage2
 214.0GB: boot/initrd.img-2.6.28-11-generic
 214.0GB: boot/vmlinuz-2.6.28-11-generic

=========================== sda7/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

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
# kopt=root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=785fc95b-8e13-4e69-b347-5c7e831952b5

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
# defoptions=quiet splash vga=794

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
# howmany=7

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

title		Ubuntu karmic (development branch), kernel 2.6.30-2-generic
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.30-2-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.30-2-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-2-generic (recovery mode)
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.30-2-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro  single
initrd		/boot/initrd.img-2.6.30-2-generic

title		Ubuntu karmic (development branch), kernel 2.6.30-1-generic
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.30-1-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-1-generic (recovery mode)
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.30-1-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro  single
initrd		/boot/initrd.img-2.6.30-1-generic

title		Ubuntu karmic (development branch), kernel 2.6.28-11-generic
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		785fc95b-8e13-4e69-b347-5c7e831952b5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.30-020630rc3-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.30-020630rc3-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.30-020630rc3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.30-020630rc3-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.30-020630rc3-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.30-020630rc3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.30-020630rc2-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.30-020630rc2-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.30-020630rc2-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.30-020630rc2-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.30-020630rc2-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.30-020630rc2-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=785fc95b-8e13-4e69-b347-5c7e831952b5 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5ee29484-6e54-4799-a6c4-81daab1d8ddc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 225.7GB: boot/grub/menu.lst
 223.0GB: boot/grub/stage2
 226.2GB: boot/initrd.img-2.6.28-11-generic
 226.2GB: boot/initrd.img-2.6.30-1-generic
 226.4GB: boot/initrd.img-2.6.30-2-generic
 221.6GB: boot/vmlinuz-2.6.28-11-generic
 236.2GB: boot/vmlinuz-2.6.30-1-generic
 226.1GB: boot/vmlinuz-2.6.30-2-generic
 226.4GB: initrd.img
 226.2GB: initrd.img.old
 226.1GB: vmlinuz
 236.2GB: vmlinuz.old
```

---

### Post by gamblor01 on 2009-05-05
Yeah you probably had grub in the MBR and Windows decided to trash it.  Figures.  Fortunately there is a simple fix.  Put in the live CD into your computer, boot up, and open a terminal.  Then run these commands:

```

$ grub
$ find /boot/grub/stage1

```

This should return something like (hd0,5)...if I'm correct you have Ubuntu installed on /dev/sda6 and that is where grub resides, so it should be hd(0,5).  Just use whatever it tells you though.  You will need this output for the next step.


```

$ root (hd0,5)    [swap out (hd0,5) with whatever was returned in step 2]
$ setup (hd0)

```

This will now install grub in your MBR.  Yippee!

---

### Post by DougieFresh4U on 2009-05-06
Thank you.
One problem, it got back one of my partitions, I did,
**grub> root (hd0,5)**
I believe step 2 returned (hd0,5,6), so how can I recover my other partition?
I am now back into my Jaunty install, (no live cd)
From previous post(mine) looks like Karmic is on sda7?
Again thanks :P
```
grub> find /boot/grub/stage1
 (hd0,5)
 (hd0,6)
```

---

### Post by DougieFresh4U on 2009-05-06
Please help :)

---

### Post by gamblor01 on 2009-05-06
Calm down...some of us do have to sleep you know.  ;)

It looks like you have 2 different grub installations -- one on sda6 and another on sda7.  When I first replied I just looked at the output until I saw your menu.lst which was on /dev/sda6.  I didn't continue scrolling down to your /dev/sda7/boot/grub/menu.lst file.  *THIS* file is obviously the one that contains entries to boot all of the partitions, so you would need to use (hd0,6) in the grub commands.

As a side note: you have full entries (meaning it tells it where the kernel is, where initrd is, and uses the UUID) in your /dev/sda7/boot/grub/menu.lst file for your Ubuntu partition on sda6.  You could just chainload if you want though, since the sda6 partition already has a bootloader on it.  Doesn't really matter though.

So either run your live CD or boot into Jaunty and run these commands:

```

$ grub
$ root hd(0,6)
$ setup (hd0)

```Just a note -- you could have just tried this yourself to see if it worked.  The above commands are really just:

(1) getting you into a grub command shell
(2) telling grub that it should use the menu.lst file on hd(0,6) a.k.a /dev/sda7
(3) installing grub into the MBR

So running that does no harm -- especially if you have a live CD around.  You can trash your MBR over and over again and always be able to recover and reinstall grub.  So in the future, don't fret too much over trashing the MBR.

Right now it is using the menu.lst file from /dev/sda6, which is why you only see the Jaunty options (Ubuntu 9.04, Ubuntu 9.04 recovery mode, and Ubuntu 9.04 memtest).  You can either copy the rest of the entries from your /dev/sda7/boot/grub/menu.lst file or just use the above 3 commands and tell your system that you wish to use the menu.lst on sda7 instead.  Depending on your level of skill, it might just be easier to run the above 3 commands and be done with it.

---

