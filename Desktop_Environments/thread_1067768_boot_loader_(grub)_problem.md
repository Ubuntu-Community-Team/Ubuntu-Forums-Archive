---
title: "boot loader (grub) problem"
date: 2009-02-12
forum: Desktop Environments
---

### Post by RWise on 2009-02-12
Ok I am not all that on Linux, but I am learning,,,
When I first installed Ubuntu I set the box up dual boot using grub with Ubuntu living on the second hard drive (hd1). The windows hard drive has failed and was the master drive (hd0). I would like to change the jumpers on the hard drive and have it be the only drive in the system for now. So how do I get grub (or another boot loader) to boot my system?

---

### Post by caljohnsmith on 2009-02-12
The first thing to do would be to install Grub to the MBR of your Ubuntu drive, but you will probably also have to change your Grub's menu.lst if you aren't using Intrepid. So in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by RWise on 2009-02-12
This will show a primary drive that I had, I do wish to remove it. And Thanx!

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 75956287 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977   c W95 FAT32 (LBA)


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c6f7a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   228,380,039   228,379,977  83 Linux
/dev/sdb2         228,380,040   234,436,544     6,056,505   5 Extended
/dev/sdb5         228,380,103   234,436,544     6,056,442  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="MINE" UUID="3AAF-BC55" TYPE="vfat" 
/dev/sdb1: UUID="a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="5e7fa556-7e9c-424b-9f98-7a4673d5196f" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# lockold=ture

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

title		Ubuntu 7.10, kernel 2.6.22-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 7.10, kernel 2.6.22-15-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.17-12-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 7.10, kernel 2.6.15-29-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.15-29-386

title		Ubuntu 7.10, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 7.10, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 7.10, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.15-23-386

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=5e7fa556-7e9c-424b-9f98-7a4673d5196f none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=764CBAE34CBA9CF5 /media/windows ntfs umask=0222 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=6D02-C1B2 /fat_files vfat rw,iocharset=utf8,umask=000 0 0
/dev/fd0	/media/floppy0	auto    rw,user,noauto  0       0
/fat_files vfat iocharset=utf8,umask=000 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/menu.lst
  38.8GB: boot/grub/stage2
  38.8GB: boot/initrd.img-2.6.15-23-386
  38.8GB: boot/initrd.img-2.6.15-27-386
  38.9GB: boot/initrd.img-2.6.15-28-386
  38.8GB: boot/initrd.img-2.6.15-29-386
  38.8GB: boot/initrd.img-2.6.17-12-386
  38.7GB: boot/initrd.img-2.6.17-12-386.bak
  38.9GB: boot/initrd.img-2.6.20-16-386
  38.8GB: boot/initrd.img-2.6.20-16-386.bak
  38.9GB: boot/initrd.img-2.6.22-14-386
  38.9GB: boot/initrd.img-2.6.22-14-386.bak
  38.9GB: boot/initrd.img-2.6.22-15-386
  38.9GB: boot/initrd.img-2.6.22-15-386.bak
  38.9GB: boot/initrd.img-2.6.22-16-386
  38.9GB: boot/initrd.img-2.6.22-16-386.bak
  38.8GB: boot/vmlinuz-2.6.15-23-386
  38.8GB: boot/vmlinuz-2.6.15-27-386
  38.8GB: boot/vmlinuz-2.6.15-28-386
  38.8GB: boot/vmlinuz-2.6.15-29-386
  38.8GB: boot/vmlinuz-2.6.17-12-386
  38.8GB: boot/vmlinuz-2.6.20-16-386
  38.8GB: boot/vmlinuz-2.6.22-14-386
  38.8GB: boot/vmlinuz-2.6.22-15-386
  38.8GB: boot/vmlinuz-2.6.22-16-386
  38.9GB: initrd.img
  38.9GB: initrd.img.old
  38.8GB: vmlinuz
  38.8GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-12
OK, it looks like you all ready have Grub correctly installed to the MBR of your sdb Ubuntu drive, but your Grub's menu.lst needs some tweaking. How about doing:
```
sudo mount /dev/sdb1 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd1,0) similar to:
```
title		Ubuntu 7.10, kernel 2.6.22-16-386
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=a9e2dbe9-bcc8-4071-8076-3cb1fb7a40da ro 
initrd		/boot/initrd.img-2.6.22-16-386

```
Also change the "# groot..." line:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Now if you boot your Ubuntu drive, you should be able to boot into Ubuntu OK. Let me know how it goes or if you run into problems.

---

### Post by RWise on 2009-02-12
Ok thats done but I have to back to work, I'll try it when I get back, thanx for the fast reply!!!!

---

### Post by RWise on 2009-02-12
I think this drive is failing as well as the other, looks like time for a new computer! 

I got a grub error 15 (I think) and then a BIOS error about to large a hard drive and then the drive died completly! At least I can run on the live disk,,,

---

### Post by RWise on 2009-02-13
Thanx for the help! I swapped the two cables and it booted right up! but now the cd burner doesn't work, go figure,,, anyway thanx for the supper fast reply and detailed help!!!!

---

