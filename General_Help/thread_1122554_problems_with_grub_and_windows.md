---
title: "problems with grub and windows"
date: 2009-04-11
forum: General Help
---

### Post by fallen seraph on 2009-04-11
I dual boot windows and hardy heron. I was foostering about with partitions and (intentionally) deleted three from my 2nd hard drive. After having done so I could no longer boot into windows. I got Error 22: Partition could not be found (or something to that effect).

To fix this I tried root (hd0,1) setup (hd0) and root (hd0,0) setup (hd0) in the grub CLI. This didn't work.

my fdisk -l looks like: > 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x05c4bcc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2      121904    61439112    f  W95 Ext'd (LBA)
/dev/sda3          182857      924996   374038560    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c599c59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdb2            8925       30400   172505970    f  W95 Ext'd (LBA)
/dev/sdb5            8925       30400   172505938+  83  Linux



Any suggestions as to how to fix this without reinstalling windows?

---

### Post by Guy_AD on 2009-04-11
Would it be possible for you to post the contents of /boot/grub/menu.lst up here? I think I have an idea as to what the problem might be.

Also, what version of Windows are you using? Windows Vista and Windows Seven use a separate boot partition, whereas Windows XP and previous use the same partition.

---

### Post by fallen seraph on 2009-04-11
> 
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
# kopt=root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro single
#initrd		/boot/initrd.img-2.6.24-23-generic

#title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro quiet splash
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

#title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro quiet splash
#initrd		/boot/initrd.img-2.6.24-21-generic
#quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro single
#initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro single
#initrd		/boot/initrd.img-2.6.24-19-generic
#
#title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5071638b-ef6f-4ae1-9856-02897610775e ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 8.04.2, memtest86+
#root		(hd1,4)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader test hd 0 0)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows NT/2000/XP (loader test hd0 1)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


I'm using windows XP, and the hd0,0 entry there is just a test case I added myself to see if anything would happen.

---

### Post by fallen seraph on 2009-04-11
okay, so I just noticed that it should probably have been (hd1, 0) in my menu.lst file. So I changed that, and when I try to boot into that it says 'starting up' but it just sticks at that screen permanently.

also when I try root (hd1, 0) setup (hd1) it tells me Error 17: Cannot mount selected partition.

---

### Post by dhysk on 2009-04-11
I know you're using XP, however I had some similar issues with Vista when I let Hardy repartition the drive instead of using the Vista tool.  When I booted into Vista it would hang at the loading screen.  The point being I messed up the partitions and I fixed it by using the repair MBR utility for windows under the recovery options.  After that I had to reinstall grub again then everything since has been working great.

---

