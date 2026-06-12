---
title: "broken dual boot"
date: 2009-02-24
forum: General Help
---

### Post by Kamien on 2009-02-24
I recently setup a dual booted system with Ibex and Vista. Everything was working fine until I formatted one of my storage hard drives to ext3. Now the vista install won't boot with grub error 13.

This is the output of `fdisk -l`.
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c35b2e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77825   625129281   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4289827

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77826   625129472    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       42178   338793472    7  HPFS/NTFS
/dev/sdc2           42179       48641    51914047+   5  Extended
/dev/sdc5           42179       48371    49745241   83  Linux
/dev/sdc6           48372       48641     2168743+  82  Linux swap / Solari
```

/dev/sda and /dev/sdb are storage drives while /dev/sdc is a split drive with an Ibex partition and a Vista partition.

This is my grub entry for Vista.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

The hard drive I formatted was /dev/sda and I figured I completely erased the vista boot sector since the grub entry states that its on /dev/sda1.

Did I completely break Vista by formatting /dev/sda? If not is there a way to fix it?

---

### Post by unutbu on 2009-02-24
Try adding 

```

title		Windows Vista/Longhorn (hd1,0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1



title		Windows Vista/Longhorn (hd2,0)
root		(hd2,0)
savedefault
makeactive
chainloader	+1
```

to /boot/grub/menu.lst

Then try booting each of these new entries. If one of them works, great. You can edit /boot/grub/menu.lst and remove the other two. If not one of these three entries work,
then please follow these instructions so we may have a better picture of your boot setup:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)

---

### Post by Kamien on 2009-02-24
The hd(1,0) entry gave a `BootMngr Missing` Error.

The hd(2,0) entry loops back to grub.

Here is the RESULTS.txt from the bootinfoscript.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub is installed in the MBR of /dev/sdc and looks at sector 355393 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 689128097 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c35b2e6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,250,258,624 1,250,258,562  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4289827

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b5da3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   677,588,991   677,586,944   7 HPFS/NTFS
/dev/sdc2         677,589,570   781,417,664   103,828,095   5 Extended
/dev/sdc5         677,589,633   777,080,114    99,490,482  83 Linux
/dev/sdc6         777,080,178   781,417,664     4,337,487  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="disksda" UUID="bd5fe773-2be9-4ba3-8bea-9b2f40ac8280" TYPE="ext3" 
/dev/sdb1: UUID="86E2616CE2616183" LABEL="one" TYPE="ntfs" 
/dev/sdc5: UUID="6c027be6-58fa-4add-a552-c028735da2c2" TYPE="ext3" 
/dev/sdc6: UUID="675dfee1-abef-433b-9309-2a5c89ccd42c" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/disksda type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marcin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcin)


=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6c027be6-58fa-4add-a552-c028735da2c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6c027be6-58fa-4add-a552-c028735da2c2

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6c027be6-58fa-4add-a552-c028735da2c2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c027be6-58fa-4add-a552-c028735da2c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6c027be6-58fa-4add-a552-c028735da2c2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c027be6-58fa-4add-a552-c028735da2c2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6c027be6-58fa-4add-a552-c028735da2c2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows Vista/Longhorn (hd1,0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1



title		Windows Vista/Longhorn (hd2,0)
root		(hd2,0)
savedefault
makeactive
chainloader	+1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=6c027be6-58fa-4add-a552-c028735da2c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=675dfee1-abef-433b-9309-2a5c89ccd42c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 352.8GB: boot/grub/menu.lst
 352.8GB: boot/grub/stage2
 352.9GB: boot/initrd.img-2.6.27-7-generic
 352.8GB: boot/vmlinuz-2.6.27-7-generic
 352.9GB: initrd.img
 352.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd
```

---

### Post by unutbu on 2009-02-24
This GRUB entry is the right one for you:
```

title		Windows Vista/Longhorn (hd1,0)
root		[COLOR="Red"](hd1,0)[/COLOR]
savedefault
makeactive
chainloader	+1
```

You can delete the other two.

To fix the `BootMngr Missing` Error, try this:

[http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php](http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php)

---

### Post by caljohnsmith on 2009-02-25
> **Kamien said:**
> 
```

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  [COLOR="Red"]Grub[/COLOR]
    Boot sector info:  [COLOR="Red"]Grub0.97 is installed in the boot sector of sdc1[/COLOR] and 
                       looks at sector 689128097 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

```
It looks like at some point you accidentally installed Grub to the boot sector of your sdc1 NTFS partition, and it appears that partition is the Vista partition since your only other NTFS partition sdb1 does not have your Vista install. So in order to boot Vista again, you will first need to repair the sdc1 boot sector. To do that, I would recommend first trying "testdisk" to see if it can find a valid backup boot sector for that partition, because if it can, that should repair your Vista partition's boot sector assuming the backup boot sector is not a Windows XP boot sector. So to use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk /dev/sdc1
```
After starting testdisk, choose "Proceed", "None", "Advanced", "Boot", then choose "Backup BS"; if testdisk gives you a warning that the sectors are not identical, then choose "Write". After you are done doing the "Backup BS" in testdisk, please post the output of the following command:
```

sudo xxd -s128 -l2 -p /dev/sdc1
sudo mount /dev/sdc1 /mnt && ls -l /mnt
```
Also, since you were previously using (hd0,0) to boot Vista from your Grub menu, that means you were booting Vista from what was the sda1 partition since it is clear you are booting the sda drive on start up. So that means when you deleted the sda1 NTFS partition and made it ext3 instead, you unintentionally deleted Vista's boot files. So in order to boot Vista again, you will need to restore Vista's boot files to its original partition (sdc1) and boot Vista from that partition instead. But how about posting the output of the above mount command first and we can work from there if you want.

---

### Post by unutbu on 2009-02-25
Kamien, after having a conversation with caljohnsmith, I realize my suggestions in post #4 are in error. sdb1 is not your Vista partition since if it was, the RESULTS.txt script would have reported "Operating System: Vista" for sdb1.

---

