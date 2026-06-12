---
title: "Splash screen doesn't show up after booting up"
date: 2008-12-05
forum: Desktop Environments
---

### Post by bd@cb8be8510 on 2008-12-05
I did a fresh install of Intrepid (I installed Ubuntu on one partition and Kubuntu on another one). After selecting (either Ubuntu or Kubuntu) a message pops up (Starting up. Loading, please wait ...) Then the monitor drops dark and a monitor-error-message pops up: Out of range Vf: 86.7 Hf: 46.4 K). It looks as if the monitor is not properly interfaced for displaying the splash. After a while the brown screen appears (in case of Ubuntu) and the gnome starts up (In case Kubuntu is selected, the KDE starts up). Everything is working fine, only the splash screen is not shown.

What bothers me most is that when I boot from the live-CD (be it Ubuntu or Kubuntu) that then the splash screen is properly shown. I worked with Ubuntu 6.10 .. 8.04 and had never problems with the splashscreen.

I checked already for bug [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990).  

I added various vga =  after ro quiet splash in menu.lst, but nothing helps: no splashscreen!

Any ideas what to check further? Thank you in advance for your advice.

I addes dmesg.txt (booting up with Ubuntu - no splash screen) and dmesg-LiveCD.txt - with splash screen!!).

---

### Post by bd@cb8be8510 on 2008-12-06
Some more additional info :

/boot/grub/menu.lst

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
color dark-gray/green light-red/light-gray

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
# kopt=root=UUID=0f66836c-712e-4865-9d28-1d3f5434b458 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0f66836c-712e-4865-9d28-1d3f5434b458

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

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		0f66836c-712e-4865-9d28-1d3f5434b458
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=0f66836c-712e-4865-9d28-1d3f5434b458 ro quiet splash
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, memtest86+
uuid		0f66836c-712e-4865-9d28-1d3f5434b458
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d91ca88f-9700-48f0-811b-00a9c8f5e7cc ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d91ca88f-9700-48f0-811b-00a9c8f5e7cc ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



/dev/sda1: UUID="0f66836c-712e-4865-9d28-1d3f5434b458"sud TYPE="ext3" 
/dev/sda3: UUID="d91ca88f-9700-48f0-811b-00a9c8f5e7cc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="3df86767-5be4-4487-b9a5-5902d85f808e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="957efd42-9a0d-41e2-866e-5837f0aba429" 
/dev/sdb1: UUID="52A4967BA49660F1" TYPE="ntfs" 

// File in /etc/initramfs-tools/conf.d

RESUME=UUID=957efd42-9a0d-41e2-866e-5837f0aba429

sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.27-10-generic

ls -alh /dev/disk/by-uuid

lrwxrwxrwx 1 root root  10 2008-12-02 19:17 0f66836c-712e-4865-9d28-1d3f5434b458 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-12-02 19:17 3df86767-5be4-4487-b9a5-5902d85f808e -> ../../sda4
lrwxrwxrwx 1 root root  10 2008-12-02 19:17 52A4967BA49660F1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-12-02 19:17 957efd42-9a0d-41e2-866e-5837f0aba429 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-12-02 19:17 d91ca88f-9700-48f0-811b-00a9c8f5e7cc -> ../../sda3


Any suggestion where to look? I Know it's a minor issue, Ubuntu is running great otherwise. Nosplash works fine, but I prefer to work
with splash as sometimes I demonstrate Ubuntu for friends & relatives.

---

### Post by sunoccard on 2008-12-06
yeah i got the same thing on mine after i tried to install a new splash theme. did you install anything since you put on the OS?

---

### Post by bd@cb8be8510 on 2008-12-08
> **sunoccard said:**
> yeah i got the same thing on mine after i tried to install a new splash theme. did you install anything since you put on the OS?

Yes, I did install and update a lot of new apllications. Ubuntu & Kubuntu is working fine. I only don't get the splash screen at booting up/logging off.

I filed this minor problem as a bug : [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/305936](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/305936)

---

