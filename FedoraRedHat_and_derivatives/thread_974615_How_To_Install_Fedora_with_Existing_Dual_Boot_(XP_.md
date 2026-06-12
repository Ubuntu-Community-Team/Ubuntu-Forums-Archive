---
title: "How To Install Fedora with Existing Dual Boot (XP and Ubuntu)"
date: 2008-11-07
forum: Fedora/RedHat and derivatives
---

### Post by ysNoi on 2008-11-07
I have already an installer of Fedora 9, was just curious so I want to try.
My problem is how can I Install it on my system with already Dual boot in it..? 

Can I ask for any assistance on How To...? Thanks in advance....!

---

### Post by djhyland on 2008-11-08
Yes, you should be able to install Fedora alongside XP and Ubuntu.  I assume that you installed Ubuntu on a computer that came with XP on it: the process is the same.

You'll need to make room for your Fedora install.  If you're not adding a separate drive for Fedora, you'll be partitioning (one of) your existing drive(s).  I recommend using gparted from a live cd or live usb to do so: if you're using the Fedora livecd, gparted should be available on it.  Set up partitions for Fedora as you see fit.  You'll likely already have a swap partition for Ubuntu, Fedora can use the same swap so you don't have to make a new one.

Once you've partitioned your drive, you're ready to install.  When the installer asks where to install Fedora, select the custom install option (or similar, I can't remember what it's called exactly).  This will ask you where on the drive you want to install Fedora.  Select your new partition for your / directory.  If your partition scheme is more complicated, select whatever additional partitions you made for stuff like /boot, /etc, and others.

Once you've told Fedora where to install, continue with the installation.  Once successfully installed, you'll be able to restart and boot into Fedora...but your XP and Ubuntu installs may be unavailable.  If this happens, it's because GRUB is now pointing to Fedora's menu.lst, which may not have picked up the options from Ubuntu's menu.lst.  To remedy this, take a look at [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=947715") thread.  Good luck!

---

### Post by ysNoi on 2009-01-05
[COLOR="DarkRed"]Hi..! It's been a long time for me to reply here in this thread but I really want my Fedora installation works for me..!

The chainloader command added on my Ubuntu grub will not boot my Fedora...

For more info, here is my Fdisk report:[/COLOR]

ysnoi@ysNoi:~$ sudo /sbin/fdisk -l
[sudo] password for ysnoi: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8bb28bb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6438    51713203+   7  HPFS/NTFS
/dev/sda2            6439        6836     3196935   82  Linux swap / Solaris
/dev/sda3            6837       13558    53994465   83  Linux
/dev/sda4           13559       19457    47383717+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6a8f6a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5306    42620413+   7  HPFS/NTFS
/dev/sdb2            5307       12114    54685260    f  W95 Ext'd (LBA)
/dev/sdb3           12115       19457    58982647+   7  HPFS/NTFS
/dev/sdb5   *        5307       12114    54685228+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22462246

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6842    54958333+   7  HPFS/NTFS
/dev/sdc2            6843       14669    62870377+   7  HPFS/NTFS
/dev/sdc3           14670       30401   126367290    f  W95 Ext'd (LBA)
/dev/sdc5           14670       30401   126367258+   7  HPFS/NTFS

[COLOR="DarkRed"]Also I added here my menu.lst report:[/COLOR]

# menu.lst - See: grub(), info grub, update-grub()
#            grub-install(), grub-floppy(),
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
# kopt=root=UUID=a5f3bace-f758-4152-bed2-3c41ead77a28 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a5f3bace-f758-4152-bed2-3c41ead77a28 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a5f3bace-f758-4152-bed2-3c41ead77a28 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5f3bace-f758-4152-bed2-3c41ead77a28 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5f3bace-f758-4152-bed2-3c41ead77a28 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-9-server (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-server root=UUID=e30dda43-d75d-498e-bfc5-5c59a2787b5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-9-server (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-server root=UUID=e30dda43-d75d-498e-bfc5-5c59a2787b5f ro single 
initrd		/boot/initrd.img-2.6.27-9-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-server (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=e30dda43-d75d-498e-bfc5-5c59a2787b5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=e30dda43-d75d-498e-bfc5-5c59a2787b5f ro single 
initrd		/boot/initrd.img-2.6.27-7-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


title           Fedora
chainloader     (hd1,4) +1


title           Fedora
configfile      (hd1,4)/boot/grub/grub.conf


[COLOR="DarkRed"]Can anybody here help me configure my menu.lst to boot my Fedora 9 installation..?

Thanks in advanced...Be lated Happy New Year To All...![/COLOR]

---

