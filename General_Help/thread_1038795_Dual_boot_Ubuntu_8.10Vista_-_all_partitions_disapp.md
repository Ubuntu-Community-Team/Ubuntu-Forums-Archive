---
title: "Dual boot Ubuntu 8.10/Vista - all partitions disappeared - only Ubuntu works"
date: 2009-01-13
forum: General Help
---

### Post by bueller on 2009-01-13
I run a dual boot laptop with Ubuntu 8.10 and Vista Home Premium. Today I turned the machine on and grub came up as usual with all of the normal boot choices. When I selected Windows Vista I got the following error message:

Windows could not start because the following file is missing or corrupt: <Windows root>\System32\hal.dll

I could boot Ubuntu just fine, but once it was done loading when I used GParted and looked at the partitions it showed the entire disk space as unallocated. I have tried to use the Vista DVD to do a repair or a restore, but it can't even find a windows installation. I have tried to use the Vista bootloader/repair program (can't remember the name off hand) at the command line after booting from the Vista DVD, but it can't find a windows installation.

Any suggestions? I have searched these forums and google, and can't come up with a good answer. I'd also be interested in any programs that could read and repair the boot sector and/or partition information rather than starting over. I am bandwidth-challenged and the thought of having to download over 6 gigs of updates, patches, software and other stuff I'd need after a reinstall of both OS's makes me want to puke.

Thanks in advance.

---

### Post by mikewhatever on 2009-01-14
Can you post the output of the following command from Applications->Accessories->Terminal.
sudo fdisk -l

---

### Post by bueller on 2009-01-14
> **mikewhatever said:**
> Can you post the output of the following command from Applications->Accessories->Terminal.
sudo fdisk -l

I should have done that last night.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x610873c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19197       19458     2096128    c  W95 FAT32 (LBA)
/dev/sda2            7296        9727    19535040   83  Linux
/dev/sda3            9728       19457    78156225    5  Extended
/dev/sda5            9728       19332    77152131    b  W95 FAT32
/dev/sda6           19333       19457     1004031   82  Linux swap / Solaris

Partition table entries are not in disk order



Also:



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
# kopt=root=UUID=7ad4ef5e-176a-4951-b903-8bb0905e5fd9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ad4ef5e-176a-4951-b903-8bb0905e5fd9

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7ad4ef5e-176a-4951-b903-8bb0905e5fd9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7ad4ef5e-176a-4951-b903-8bb0905e5fd9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7ad4ef5e-176a-4951-b903-8bb0905e5fd9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7ad4ef5e-176a-4951-b903-8bb0905e5fd9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7ad4ef5e-176a-4951-b903-8bb0905e5fd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7ad4ef5e-176a-4951-b903-8bb0905e5fd9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7ad4ef5e-176a-4951-b903-8bb0905e5fd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7ad4ef5e-176a-4951-b903-8bb0905e5fd9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7ad4ef5e-176a-4951-b903-8bb0905e5fd9
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

---

### Post by mikewhatever on 2009-01-14
Well, your windows partition seems to be in place (not disappeared), and grub menu looks ok. The problem seems to be purely windows related, so let's get you some windows experts in the windows section, also, check out the link below.
[http://users.bigpond.net.au/hermanzone/p15.htm#hal.dll_is_missing_or_corrupt](http://users.bigpond.net.au/hermanzone/p15.htm#hal.dll_is_missing_or_corrupt)

---

### Post by bueller on 2009-01-14
I figured it out. Apparently when the MediaDirect button is pushed on a Dell laptop it overwrites or redirects Windows boot information. I was not aware this had happened. After exhausting every other option I could think of and after reading through the links provided I finally decided to see if the media center option would actually work (I've never used it before). Much to my surprise the Grub screen came up. I selected the Vista option and it booted Vista normally. I then shut down and restarted the computer. When the Grub menu came up I selected Vista again and it booted normally. I then restarted and booted Ubuntu 8.10, ran GParted, and all of my partitions were visible again.

I've looked in the BIOS to see if there is a way to kill MediaCenter, and unfortunately there isn't. Next time I format the hard drive I will make sure I find that pesky hidden MediaCenter partition and get rid of it for good.

Thanks for all of your help!

---

