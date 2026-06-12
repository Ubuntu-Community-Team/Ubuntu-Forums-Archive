---
title: "Completly eliminate windows"
date: 2008-09-30
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2008-09-30
Hi all,

My system have 2 Hard disk drives(HDD) one is 15GIG and having windows on it and the other 4GIG having Ubuntu on it. 

I wanted to completely eliminate windows and use it to Ubuntu. How can I do that. I also like to transfer all my software to 15Gig drive and I wanted to use 4Gig as a storage.

Regards,

Swaroop Kunduru.

---

### Post by chewearn on 2008-09-30
hi
First we need to understand how the harddisks are connected and how they are partitioned.  Please answer below as best you can.

1. Which harddisk is primary, which is slave?

2. Boot into Ubuntu, open a terminal, post the output from the following commands:
```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by SwaroopKunduru on 2008-09-30
Thanks chewearn for your reply,

swaroop@swaroop-desktop:~$ sudo fdisk -l
[sudo] password for swaroop: 

Disk /dev/sda: 15.0 GB, 15020457984 bytes
240 heads, 63 sectors/track, 1940 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1561    11801128+   c  W95 FAT32 (LBA)
/dev/sda2            1562        1940     2865240    f  W95 Ext'd (LBA)
/dev/sda5            1562        1940     2865208+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 4303 MB, 4303756800 bytes
255 heads, 63 sectors/track, 523 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb11c1240

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         493     3959991   83  Linux
/dev/sdb2             494         523      240975    5  Extended
/dev/sdb5             494         523      240943+  82  Linux swap / Solaris

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

swaroop@swaroop-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=3fc87834-8799-406e-a26e-17a310613a91 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3fc87834-8799-406e-a26e-17a310613a91 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3fc87834-8799-406e-a26e-17a310613a91 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by steveneddy on 2008-09-30
Personally I would set the 4 gig as /home and the 15 gig as OS and swap.
 
You may try getting some larger capicity hard drives in the future.
 
If you DL lots of pics, music or video you may run out of room before you know it.
 
On the other hand, my daughter's desktop has a 20 gig HD and she rarely DL's anything and it works great for her.

---

### Post by chewearn on 2008-09-30
Here are the steps, as complete as I can write them :smile: Please double check each step, because I am writing from memory, and there might be mistakes.

1. Back-up all data in the Windows harddisk (HDD1) that you still wanted to keep to an external storage (usb thumbdrive, etc).

2. Boot into the Ubuntu LiveCD.

3. Once in the LiveCD desktop, launch the partition editor.

4. Select the HDD1.  Delete the Windows primary partition.  You have another logical partition (probably D:\).  You can keep this, but I suggest to delete it as well (hence the back-up in step 1).  Keep the extended partition in place.

5. Apply changes.

6. Select the Ubuntu harddisk (HDD2).  Right-click on the primary partition, select copy.  

7. Select HDD1.  Right-click on the unformatted space left behind by the Windows partition, select paste.

8. Repeat step 6 for the swap partition; make sure the swap is copy inside the extended partition.

9. Apply changes.  This will take a while to complete.

10. Move/drag the swap partition to the rightmost.  Resize the extended partition smaller against the swap.

11. Apply changes.  This will take a while to complete.

12. Resize the primary partition to fill up the entire space left behind by the previous operation.

13. Apply changes.  This will take a while to complete.

14. Close partition editor.  Shutdown your computer.

15. Remove HDD2 for safe keeping (for the moment).

16. Boot into liveCD again.

17. Mount HDD1 partition 1.  Edit the menu.lst file of the partition.
```
gksudo gedit /media/disk/boot/grub/menu.lst
```Go to the end of the file.  Delete this part (which was the Windows menu entry):
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1     
```Find all instances of (hd1,0), replace them with (hd0,0).

18. Save and close.

19. Now, reboot into HDD1 (remove liveCD).  Hopefully no error and you can reach the desktop.

20. Check if swap partition is properly mounted and used.
```
free -m
```21. If all is well, you can shutdown, put back HDD2.  Boot into liveCD again to erase HDD2 and create a new data partition in it.

Phew!  That was long. :mrgreen:

---

