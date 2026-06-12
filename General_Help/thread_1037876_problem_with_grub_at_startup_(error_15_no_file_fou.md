---
title: "problem with grub at startup (error 15 no file found), fstab, menu.lst, after update"
date: 2009-01-12
forum: General Help
---

### Post by 80aless on 2009-01-12
Hi. 
I cannot boot in my ubuntu anymore, the only option that grub show is the memtest86+ .
With the live cd I cannot see the /boot/grub.menu.lst nor all the vmlinuz-2.6.24-??-generic and initrd.img-2.6.24-??-generic       files, so that grub has no kernel to load. My old working ubuntu is in sda1, which I can mount correctly with 
```
sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bf63e
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9361    75192201   83  Linux
/dev/sda2            9362        9729     2955960    5  Extended
/dev/sda5            9362        9729     2955928+  82  Linux swap / Solaris
sudo mount /dev/sda1 /mnt/ #the one with 'Linux'
```

so i am afraid that ubuntu 'mounts' the hard disk uncorrectly. I tried to edit the grub line at boot putting /dev/sda1 or the UUID but no success. I get ```
Error 15: no file found
```
```

root=/dev/sda1 #or 
roor=UUID=8e83..etc #or
kernel /boot/vmlinuz root=...as above
```

Hope somebody can help
Regards
alex

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by 80aless on 2009-01-26
Hi , thanks for your reply. I managed to boot in my system using Super Grub USB, but it is too difficult for me to make it stable and boot without the USB. Initally I had to boot with  /boot/grub/menu.lst~ , which I copied to /boot/grub/menu.lst_good_one
and another /boot/grub/menu.lst 
How can I boot from the right one? If I leave the grub I get error 21 (or was it 12?), and I have to use the usb

Here below there is the info you asked. 

Thanks!


[PHP]============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97-os.1 is installed in the MBR of /dev/sdb and looks on the same 
    drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
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

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bf63e

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  150,384,464  150,384,402  83 Linux
/dev/sda2        150,384,465  156,296,384    5,911,920   5 Extended
/dev/sda5        150,384,528  156,296,384    5,911,857  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1042 MB, 1042284544 bytes
256 heads, 56 sectors/track, 142 cylinders, total 2035712 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07fcfc9f

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            56    2,035,711    2,035,656   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0ebda0d2-112d-4645-bae3-1df95201cbdf" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="feef9251-27c9-4e34-9141-1cb313eb92bf" 
/dev/sdb1: UUID="B460-8DE1" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aless/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aless)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

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
# kopt=root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=feef9251-27c9-4e34-9141-1cb313eb92bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  23.7GB: boot/grub/menu.lst
   8.8GB: boot/grub/stage2
  10.5GB: boot/initrd.img-2.6.24-19-generic
   3.9GB: boot/initrd.img-2.6.24-19-generic.bak
  20.8GB: boot/initrd.img-2.6.24-21-generic
  10.5GB: boot/initrd.img-2.6.24-21-generic.bak
  51.6GB: boot/initrd.img-2.6.24-22-generic
  24.3GB: boot/initrd.img-2.6.24-22-generic.bak
  51.7GB: boot/initrd.img-2.6.24-23-generic
  51.7GB: boot/initrd.img-2.6.24-23-generic.bak
  10.5GB: boot/vmlinuz-2.6.24-19-generic
  17.4GB: boot/vmlinuz-2.6.24-21-generic
  23.3GB: boot/vmlinuz-2.6.24-22-generic
  51.6GB: boot/vmlinuz-2.6.24-23-generic
  51.7GB: initrd.img
  51.6GB: initrd.img.old
  51.6GB: vmlinuz
  23.3GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location  of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2

=============================== StdErr Messages: ===============================

No errors were reported.[/PHP]

---

### Post by caljohnsmith on 2009-01-26
So when you boot your sda drive, do you get the Grub menu on start up (be sure to press ESC to see the menu)? And if so, what happens when you try the first entry in the Grub menu, i.e. "Ubuntu 8.04.1, kernel 2.6.24-22-generic"? It looks like that should work. Or is the problem that you are getting the Grub error before you see the Grub menu?

---

### Post by 80aless on 2009-01-26
I get the problem before getting to the Grub menu, so I cannot choose anything.
Alex

---

### Post by caljohnsmith on 2009-01-26
OK, how about from the Live CD do:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And put a pound sign or hash # in front of the "hiddenmenu" line near the beginning of the file:
```
# hiddenmenu
```
Next reinstall Grub:
```
sudo umount /dev/sda1 && sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of the commands before you do "quit". Then reboot, and let me know if that changes anything.

---

### Post by 80aless on 2009-01-26
I can try it tomorrow morning, at work. I will let you know. Thanks!
Yes, solved. I did try root (hd0,0) but probably not setup (hd0). Now it boots normally.
Thank you!!!
Alex

> 
root (hd
 Possible disks are:  hd0 hd1
grub> root (hd0,0)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub> quit

---

