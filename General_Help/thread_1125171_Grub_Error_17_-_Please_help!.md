---
title: "Grub Error 17 - Please help!"
date: 2009-04-14
forum: General Help
---

### Post by Pipps on 2009-04-14
**[B]My Ubuntu system will not boot - I receive an Error 17 at startup and it hangs. Please help!**[/B]

This morning I reformatted my local hard-drive and resized the partitions.

Prior to the reformat, I took partition images of the '/boot' and '/' partitions from the previous Ubuntu installation.

I then reinstalled Ubuntu. Grub boot-loader started normally and everything was fine.

I then restarted my system and launched PartImage from the Sysresccd. I reinstated just the '/' partition image. [_I was presented with a Grub Error 15 on reboot_]("http://ubuntuforums.org/showthread.php?t=1124610"), and the system hung.

I launched PartImage again from the Sysresccd, and reinstated both the '/boot' and the '/' partition images.

On reboot, I was presented with Grub Error 17, as follows: 

> 
Error 17: Cannot mount selected partition

Press any key to continue.


I took a photograph of the screen. I can report that the error appeared in the following context during the startup procedure:

> * Checking root file systems...
960
fsck 1.41.3 (12-Oct-2008 )
fsck.ext3: Unable to resolve 'UUID-d33304f1-a492-42e1-9753-1ab1436a9409'
fsck.ext3: Unable to resolve 'UUID-490ba839-9466-43d6912a-dc1bfaa18ae5'
fsck died with exit status 8

* File system check failed.                                      [Fail]
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started
CONTROL-D will terminate this shell and resume system boot.(Type CONTROL-D to continue)

I now receive both of these error screens every time I try to start the system. I am currently only able to boot from my Ubuntu 8.10 Live USB pendrive.

**What can be done to allow Grub to work properly and to allow me to reinstate my backed-up '/' partition image with the Sysresccd?**

Thank you.

---

### Post by Zack McCool on 2009-04-14
Looks like your UUID's have changed during your procedures...

Boot to a LiveCD, then run the following to get the current UUID's:

```
 tune2fs -i /dev/sda1 
```

Will give you, for example, the info for /dev/sda1.  Get the UUID strings for the 2 partitions you need, then correct the /etc/fstab to include the new UUID's.  Do the same for /boot/grub/menu.lst.

It looks like that should fix you up, but if not, let me know...

---

### Post by Pipps on 2009-04-14
Hello! Thank you for your help!

1. Typing 'tune2fs -i /dev/sda1' in a terminal in Live CD produces the following output:

> 
mint mint # tune2fs /dev/sda4
tune2fs 1.41.3 (12-Oct-2008 )
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
	[-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
	[-M last_mounted_dir] [-O [^]feature[,...]]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID]
	[ -I new_inode_size ] device

So I tried typing sudo blkid. It produced the following output:

> 
/dev/sda1: UUID="9CFC0E9DFC0E7236" TYPE="ntfs" 
/dev/sda2: UUID="d33304f1-a492-42e1-9753-1ab1436a9409" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="5ca3cbe9-8f3c-41a7-916d-ed3073e18e15" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4e4b1957-664e-40ec-bd2a-dcaed0df47b9" TYPE="swap" 
/dev/sdb1: LABEL="USB DRIVE" UUID="4A75-FD75" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 


2. However, I immediately recognise the stated sda2 and sda4 UUIDs in this output, because they are the UUIDs which relate to the partition images which I have just reinstated.

But why is it that Grub does not appear to like these UUIDs and refuse to boot from these partitions?

3. When I open the 'menu.lst' file in the '/boot' local directory, I cannot see where the UUIDs would be inserted. The output of the local 'menu.lst' file is as follows:

> 
# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,0)
kernel		/last-good-boot/vmlinuz root=/dev/sda2 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


> 
# sample /boot/grub/menu.lst entry for memtest86
#
# This example 	assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin


4. I cannot find a directory called '/etc/fstab' in Live CD mode, even with 'hidden files and folders' ticked.

5. What should I do to make Grub boot my reinstated partitions?

---

### Post by Pipps on 2009-04-15
Please help me! :cry:

---

### Post by meierfra. on 2009-04-15
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Pipps on 2009-04-16
Deear Sir. Thank you so much for your incredibly kind and explicit instructions. Please find the output of my results.txt file below:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9d9d9d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   131,138,594   131,138,532   7 HPFS/NTFS
/dev/sda2         131,138,595   131,331,374       192,780  83 Linux
/dev/sda3         131,331,375   135,235,169     3,903,795   5 Extended
/dev/sda5         131,331,438   135,235,169     3,903,732  82 Linux swap / Solaris
/dev/sda4         135,235,170   156,296,384    21,061,215  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1002 MB, 1002438656 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x006beaa5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,957,887     1,957,825   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x202e58c4

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9CFC0E9DFC0E7236" TYPE="ntfs" 
/dev/sda2: UUID="2ff5a7b5-4099-456d-bb7a-3d360cf5caa3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="4edd04e2-953b-451b-b5eb-8287c66a8e59" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4e4b1957-664e-40ec-bd2a-dcaed0df47b9" 
/dev/sdb1: LABEL="USB DRIVE" UUID="4A75-FD75" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: UUID="4E10E48610E475FD" LABEL="IOMEGA_HDD" TYPE="ntfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)
/dev/sdd1 on /media/IOMEGA_HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,1)
kernel		/last-good-boot/vmlinuz root=/dev/sda4 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


============================= sda2/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,1)
kernel		/last-good-boot/vmlinuz root=/dev/sda4 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


=================== sda2: Location of files loaded by Grub: ===================


  67.2GB: boot/grub/menu.lst
  67.2GB: boot/grub/stage2
  67.1GB: boot/initrd.img-2.6.27-7-generic
  67.1GB: boot/vmlinuz-2.6.27-7-generic
  67.2GB: grub/menu.lst
  67.2GB: grub/stage2
  67.1GB: initrd.img-2.6.27-7-generic
  67.1GB: vmlinuz-2.6.27-7-generic

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=4edd04e2-953b-451b-b5eb-8287c66a8e59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=2ff5a7b5-4099-456d-bb7a-3d360cf5caa3 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=4e4b1957-664e-40ec-bd2a-dcaed0df47b9 none            swap    sw              0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

I look forward to receiving your further instruction on the route forward.

---

### Post by GnuGuy on 2009-04-16
I'd like to mention that I recently resolved a problem with Grub using a boot disk called "supergrub". You can repair your grub with this disk. 

[http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems](http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems)

Hope this helps.

---

### Post by leonardo_neo on 2009-04-16
> **GnuGuy said:**
> I'd like to mention that I recently resolved a problem with Grub using a boot disk called "supergrub". You can repair your grub with this disk. 

[http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems](http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems)

Hope this helps.


+1

I too recommend SGD for problems like this.

---

### Post by meierfra. on 2009-04-16
RESULTS.txt  did not reveal any problems. But RESUTLS.txt also does not  seem to match the previously provided information. 
Did you have all your hard drives plugged in, when you run the boot info script?

Could you describe the current situation? You said that you get Grub Error 17  and the "unresolved uuid error". But I don't understand  how you can get both of those errors.

Could you describe exactly what happens during boot up? 
Does the Grub menu appear?  
Do you get Grub error 17  after you pick  Linux Mint at  the Grub Menu?  When exactly do you get the "unresolved uuid error" ?

---

### Post by Pipps on 2009-04-17
Dear Sir

Thank you for your kind interest in my humble problem and your expert assistance in the matter.

Currently, my setup is booting fine. That is because I am using the new Ubuntu installation which I recently applied to my new 10GB ext3 partition.

However, the entire problem, and the Grub Error 17, indeed appear when I use Partimage (from the Sysresccd) to reinstate the drive image for my Ubuntu installation which mounts at '/' (but does not include '/boot').

Partimage will reinstate the old drive image without any problems, but when I then subsequently attempt to boot it, I have the problems which I have previously described. I can go into them in more detail if that would help. But please let me know if this information is enough to clarify the situation, first.

Thank you again for all your time and help.

Best wishes

Pipps

---

### Post by meierfra. on 2009-04-17
> Currently, my setup is booting fine. That is because I am using the new Ubuntu installation which I recently applied to my new 10GB ext3 partition.

Trying  to figure out a solution to a problem, which no longer exists, is usually impossible.

If you want to figure out a solution to your problem, you will have to use Partimage again to reinstate you old drive image.  Then  run the boot info script and post the RESULTS.txt. Also describe exactly what happens during boot up. The more details you provide, the easier it will be to figure out the cause of your problems.

---

