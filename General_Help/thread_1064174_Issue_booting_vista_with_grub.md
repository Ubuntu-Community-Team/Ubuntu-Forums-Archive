---
title: "Issue booting vista with grub"
date: 2009-02-08
forum: General Help
---

### Post by Leif on 2009-02-08
Hi,

I recently went thru a cycle of installing vista then ubuntu on an old laptop. Ubuntu is working fine but I can't get vista booting again. I've attached the output from the boot info script :

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1427. But according to the info from fdisk, 
                       sda6 starts at sector 11005952.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x66733871

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,044,594     9,044,532  83 Linux
/dev/sda2           9,044,595   156,296,384   147,251,790   5 Extended
/dev/sda5           9,044,658    11,004,524     1,959,867  82 Linux swap / Solaris
/dev/sda6          11,005,952    51,965,951    40,960,000   7 HPFS/NTFS
/dev/sda7          51,968,000    72,447,999    20,480,000  83 Linux
/dev/sda8          72,450,048   156,295,167    83,845,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="141a0892-1e26-4113-b8da-a340d7498282" TYPE="ext3" 
/dev/sda5: UUID="3def0f2e-4e59-4237-9dbb-023b76a17a9c" TYPE="swap" 
/dev/sda6: UUID="F2F816ABF8166E5B" TYPE="ntfs" 
/dev/sda7: UUID="8b055bb7-157b-4b5e-8e7b-7ee1afc5d077" TYPE="ext3" 
/dev/sda8: UUID="0C16AF1816AF01B6" LABEL="Space" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/leif/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=leif)

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
# root		(hd0,5)
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
# kopt=root=UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077

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
uuid		8b055bb7-157b-4b5e-8e7b-7ee1afc5d077
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8b055bb7-157b-4b5e-8e7b-7ee1afc5d077
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8b055bb7-157b-4b5e-8e7b-7ee1afc5d077
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8b055bb7-157b-4b5e-8e7b-7ee1afc5d077
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8b055bb7-157b-4b5e-8e7b-7ee1afc5d077
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


title		Windows Vista 5map
map (hd0,5) (hd0,0)
map (hd0,0) (hd0,5)
root (hd0,5)
chainloader +1

title		Windows Vista
rootnoverify (hd0,5)
makeactive
chainloader +1

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=8b055bb7-157b-4b5e-8e7b-7ee1afc5d077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=141a0892-1e26-4113-b8da-a340d7498282 /home           ext3    relatime        0       2
# /dev/sda5
UUID=3def0f2e-4e59-4237-9dbb-023b76a17a9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/menu.lst
  36.7GB: boot/grub/stage2
  36.6GB: boot/initrd.img-2.6.27-11-generic
  36.6GB: boot/initrd.img-2.6.27-7-generic
  36.6GB: boot/vmlinuz-2.6.27-11-generic
  36.6GB: boot/vmlinuz-2.6.27-7-generic
  36.6GB: initrd.img
  36.6GB: initrd.img.old
  36.6GB: vmlinuz
  36.6GB: vmlinuz.old

```

I suspect it's because of the "According to the info in the boot sector, sda6 starts at sector 1427. But according to the info from fdisk, sda6 starts at sector 11005952." bit, but not sure what that's supposed to mean. Can anyone help?

Cheers,

Leif

---

### Post by dougalkerr on 2009-02-08
Google 'dual boot windows with linux' and you will find a great tutorial about how to do it properly. I can't remember who it is by but, it all works. I have done it and I remember having to use the Vista install disc and get to the 'repair Vista or something such like' because Linux damages Vistas' bootloader. Once you get Vista to repair itself and reboot you will have grub giving you your options and Vista should work normally once more...

---

### Post by Leif on 2009-02-08
Thanks! I thought about going through the 'repair windows boot/reinstall grub' routine, but I was really hoping to avoid it. Anyone have any other options?

---

### Post by caljohnsmith on 2009-02-08
It looks like the problem is you installed Vista to sda6, which is a logical partition; whenever you install Windows to a logical partition, it will always put its boot files in a primary FAT/NTFS partition, or it won't let you install. Since you don't have a primary FAT/NTFS partition, you probably deleted your Vista's boot files when you installed Ubuntu. If you don't want to redo everything, here is a really [good tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") of how restore Vista's boot files and also boot it from a logical partition. Let me know how that goes or if you run into problems.

---

