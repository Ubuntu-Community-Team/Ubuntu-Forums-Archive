---
title: "grub chainloader question"
date: 2009-05-16
forum: General Help
---

### Post by wendallsan on 2009-05-16
Hi all,

I'm experimenting with chainloading in grub.

I have 3 OS's, and am currently running grub from the one on hda6.  I have Ubuntu 8.04 on hda1 and Ubuntu 9.04 on hda3.  I'd like to get over to the Ubuntu 9.04 grub to boot from there.  I've added this entry into my grub menu.lst:

```

title CHAINLOAD TO UBU9
# root (hd0,2) # THIS SHOULD TRANSLATE TO HDA3 . . .
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f # THIS IS HDA3'S UUID . . .
chainloader +1

```

I've tried both uuid and root to identify the partition, but both ways result in an error 13: invalid or unsupported executable format.  My 9.04 install is ext3 (not ext4) formatted.

Shouldn't this work?  Where can I begin to troubleshoot this?  Any help is greatly appreciated.

---

### Post by Brandon Williams on 2009-05-16
In order for chainloading another copy of grub to work, you must first install the grub stage1 bootloader to the partition that you will chainload.

In your example, you would do this:
```
$ grub
grub> root (hd0,2)
grub> setup (hd0,2)
```

After this, you will have the stage1 bootloader installed in the boot sector of the partition, and the stage2 on that partition will know where to look for its stage2 and menu.lst.

---

### Post by wendallsan on 2009-05-17
Hi and thanks for your help!

On executing the commands you gave me, I get the following error on the setup command:

```

Checking if "/boot/grub/stage1" exists ... no
Checking if "/grub/stage1" exists ... no

Error 2: Bad file or directory type

```

Any idea what this means?  Any further help is greatly appreciated!

---

### Post by unutbu on 2009-05-17
Perhaps run boot_info_script [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)
and post the RESULTS.txt file. This should give us plenty of information to understand your boot setup and what commands are needed to chainload.

---

### Post by wendallsan on 2009-05-17
Hi and thanks,

Here are the results of that script:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 4.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63   185,839,919   185,839,857  83 Linux
/dev/hda2    *    390,636,540   488,392,064    97,755,525   5 Extended
/dev/hda5         483,106,743   488,392,064     5,285,322  82 Linux swap / Solaris
/dev/hda6         390,636,666   483,106,679    92,470,014  83 Linux
/dev/hda3         185,839,920   288,238,229   102,398,310  83 Linux
/dev/hda4         288,238,230   390,636,539   102,398,310   7 HPFS/NTFS


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dea26dd4-d38d-4fa9-9f7a-b21cfbfac36c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda1: UUID="d6a09043-40e9-4faa-a16f-eaadd3e3790c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="04bdb9ab-fd31-472f-a19c-092d0bfca72f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda4: TYPE="ntfs" 
/dev/hda5: TYPE="swap" 
/dev/hda6: UUID="3b188cc9-42c9-4ae8-ae39-f36260a52c09" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/hda6 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /media/Nyo type ext3 (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


=========================== hda1/boot/grub/menu.lst: ===========================

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
default		4

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
# kopt=root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25-custom
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25-custom root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24.7-rt25-custom
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25-custom (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25-custom root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24.7-rt25-custom

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25 root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24.7-rt25
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24.7-rt25 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24.7-rt25 root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24.7-rt25

#title		Ubuntu 8.04.1, kernel 2.6.24-23-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-23-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-23-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-23-rt


####################################
# THIS IS GENERIC UBUNTU KERNEL
####################################

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

##################################
# THIS IS THE UBUNTU STUDIO KERNEL??
##################################

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
initrd		/boot/initrd.img-2.6.24-22-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-21-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-21-generic

#itle		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-17-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-17-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=99998326-dc28-4a49-b466-2afce77293e2 none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== hda1: Location of files loaded by Grub: ===================


  78.3GB: boot/grub/menu.lst
  69.7GB: boot/grub/stage2
  69.8GB: boot/initrd.img-2.6.24-16-generic
  69.9GB: boot/initrd.img-2.6.24-16-generic.bak
  69.9GB: boot/initrd.img-2.6.24-17-generic
  69.9GB: boot/initrd.img-2.6.24-17-generic.bak
  13.6GB: boot/initrd.img-2.6.24-18-generic
  73.7GB: boot/initrd.img-2.6.24-18-generic.bak
  13.6GB: boot/initrd.img-2.6.24-19-generic
  13.6GB: boot/initrd.img-2.6.24-19-generic.bak
  69.8GB: boot/initrd.img-2.6.24-21-generic
  69.9GB: boot/initrd.img-2.6.24-21-generic.bak
  69.9GB: boot/initrd.img-2.6.24-21-rt
  69.9GB: boot/initrd.img-2.6.24-21-rt.bak
  69.8GB: boot/initrd.img-2.6.24-22-generic
  69.9GB: boot/initrd.img-2.6.24-22-generic.bak
  69.8GB: boot/initrd.img-2.6.24-22-rt
  69.9GB: boot/initrd.img-2.6.24-22-rt.bak
  70.0GB: boot/initrd.img-2.6.24-23-generic
  77.2GB: boot/initrd.img-2.6.24-23-generic.bak
  77.2GB: boot/initrd.img-2.6.24-23-rt
  70.0GB: boot/initrd.img-2.6.24-23-rt.bak
  69.8GB: boot/initrd.img-2.6.24.7-rt25
  70.0GB: boot/initrd.img-2.6.24.7-rt25-custom
  69.9GB: boot/vmlinuz-2.6.24-16-generic
  69.8GB: boot/vmlinuz-2.6.24-17-generic
  13.5GB: boot/vmlinuz-2.6.24-18-generic
  13.5GB: boot/vmlinuz-2.6.24-19-generic
  69.8GB: boot/vmlinuz-2.6.24-21-generic
  69.8GB: boot/vmlinuz-2.6.24-21-rt
  69.8GB: boot/vmlinuz-2.6.24-22-generic
  69.8GB: boot/vmlinuz-2.6.24-22-rt
  77.2GB: boot/vmlinuz-2.6.24-23-generic
  70.0GB: boot/vmlinuz-2.6.24-23-rt
  69.9GB: boot/vmlinuz-2.6.24.7-rt25
  69.8GB: boot/vmlinuz-2.6.24.7-rt25-custom
  77.2GB: initrd.img
  70.0GB: initrd.img.old
  70.0GB: vmlinuz
  77.2GB: vmlinuz.old

=========================== hda6/boot/grub/menu.lst: ===========================

default		0
timeout 	10
color cyan/blue white/blue

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
# kopt=root=/dev/hda6 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=

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
# altoptions=(single-user mode) single

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

### END DEBIAN AUTOMAGIC KERNELS LIST

title		64studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot

# NOW AN ATTEMPT TO GET UBUNTU 9:

title Ubuntu 9.04, kernel 2.6.24-21-generic
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel /boot/vmlinuz-2.6.28-11-generic ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Chainload to Ubuntu 9.04
# root (hd0,2)
uuid 04bdb9ab-fd31-472f-a19c-092d0bfca72f
chainloader +1

# COPIED FROM THE UBU 9.04 PARTITION BOOTLOADER FOR REFERENCE
# title		Ubuntu 9.04, kernel 2.6.28-11-generic
# root		(hd0,4)
# uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash 
# initrd		/boot/initrd.img-2.6.28-11-generic
# quiet

=============================== hda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1	/media/Nyo	ext3	user   0	0
# MODIFIED TO ALLOW WRITE PRIVELEGES (doesn't work yet)
# /dev/sda1	/media/Nyo	ntfs-3g	defaults,locale=en_US.utf8   0    0



=================== hda6: Location of files loaded by Grub: ===================


 200.9GB: boot/grub/menu.lst
 211.0GB: boot/grub/stage2
 211.1GB: boot/initrd.img-2.6.21-1-multimedia-amd64
 211.0GB: boot/initrd.img-2.6.21-1-multimedia-amd64.bak
 211.0GB: boot/vmlinuz-2.6.21-1-multimedia-amd64
 211.1GB: initrd.img
 211.0GB: vmlinuz

=========================== hda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=04bdb9ab-fd31-472f-a19c-092d0bfca72f

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
uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		04bdb9ab-fd31-472f-a19c-092d0bfca72f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d6a09043-40e9-4faa-a16f-eaadd3e3790c ro single 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		64studio, kernel 2.6.21-1-multimedia-amd64 (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		64studio, kernel 2.6.21-1-multimedia-amd64 (single-user mode) (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/hda6 ro vga=791 splash=silent single 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		64studio, kernel memtest86 (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/memtest86.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title		64studio, kernel memtest86+ (on /dev/sdb6)
root		(hd1,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=04bdb9ab-fd31-472f-a19c-092d0bfca72f /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== hda3: Location of files loaded by Grub: ===================


 100.6GB: boot/grub/menu.lst
 100.5GB: boot/grub/stage2
 100.6GB: boot/initrd.img-2.6.28-11-generic
 100.5GB: boot/vmlinuz-2.6.28-11-generic
 100.6GB: initrd.img
 100.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdc sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/hda3: device is busy
umount: /tmp/BootInfo/hda3: device is busy


```

---

### Post by unutbu on 2009-05-17
I'm not quite sure if I know the solution to this problem.

Here is what I think is happening:

Hardy (and perhaps Debian) uses ext3 partitions with a 128 byte inode size, and
Jaunty (and Intrepid) uses ext3 partitions with a 256 byte inode size. 
The GRUB that comes with older versions of Ubuntu can not read ext3 partitions with 256 byte inode sizes. (This info comes from [http://ubuntuforums.org/showpost.php?p=6167548&postcount=9](http://ubuntuforums.org/showpost.php?p=6167548&postcount=9)).

This might be why you are getting "Error 2" even though /boot/grub/stage1 does exist on /dev/hda3. 

If the above is correct, then try booting the Jaunty LiveCD, open a terminal and
try Brandon William's commands again from there:
```

sudo grub
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit

```

---

### Post by wendallsan on 2009-05-17
Hi,

I'm booted into my live cd and see that the hard drives have changed, so now what was hda is now hdb.  I changed the grub partition accordingly to hd1,2.

```

grub> root (hd1,2)
root (hd1,2)
grub> setup (hd1,2)
setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

```

We'll see what this does on reboot . . .

Thanks!

---

### Post by wendallsan on 2009-05-17
Grub doesn't seem to have changed at all, same menu, same OS's that boot and don't boot.  Same error messages for those that don't boot.

Here's what I was seeing while logged into the live CD when looking for the right partition to run the grub commands on:

```

ubuntu@ubuntu:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 140 2009-05-17 16:56 .
drwxr-xr-x 6 root root 120 2009-05-17 16:57 ..
lrwxrwxrwx 1 root root  10 2009-05-17 16:56 04272A707E72716F -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-05-17 16:56 3b188cc9-42c9-4ae8-ae39-f36260a52c09 -> ../../sdb6
lrwxrwxrwx 1 root root  10 2009-05-17 16:56 b480cd66-6612-4474-92ce-e1390566e047 -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-05-17 16:56 d6a09043-40e9-4faa-a16f-eaadd3e3790c -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-05-17 16:56 dea26dd4-d38d-4fa9-9f7a-b21cfbfac36c -> ../../sda1

```

It looked to me that my hda had become sdb with the live cd boot somehow, so I subbed the hd0,2 with hd1,2.

Running the original command setup (hd0,2) gives me:

```

grub> setup (hd0,2)
setup (hd0,2)

Error 12: Invalid device requested

```

Any ideas?

---

### Post by unutbu on 2009-05-17
I'm not sure how this happened, but it looks like the UUID of hda3 (or what the liveCD calls sdb3) has changed from
```

04bdb9ab-fd31-472f-a19c-092d0bfca72f
```

to 
```

b480cd66-6612-4474-92ce-e1390566e047
```

Perhaps try updating the menu.lst on hda6 with 

```
title Chainload to Ubuntu 9.04 from UUID
uuid b480cd66-6612-4474-92ce-e1390566e047
chainloader +1

title Chainload to Ubuntu 9.04 from (hd0,2)
root (hd0,2)
chainloader +1
```

If this does not work, please run boot_info_script again and record the GRUB Error you see when you try to chainload.

---

### Post by wendallsan on 2009-05-17
Hi, using root (hd0,2) worked and I'm able to get into the 9.04 boot loader and boot from there.

thanks very much for the help!

---

