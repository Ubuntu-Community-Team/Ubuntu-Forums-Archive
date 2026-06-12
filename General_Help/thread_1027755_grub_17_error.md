---
title: "grub 17 error"
date: 2009-01-01
forum: General Help
---

### Post by shabinzon on 2009-01-01
I create another partition from the NTFS one
and after that my computer needed reboot

and suddenly the message grub 17 error appear

What can I do?

thanks in advance.

---

### Post by ajgreeny on 2009-01-01
Show us the output of ```
sudo fdisk -l
``` from the live CD, and also mount the ubuntu install partition and show us the /boot/grub/menu.lst from that.

I think you have probably added a partition and therefore the numbering has changed, thiough the UUID is supposed to avoid that happening.  I hope you have not formatted your ubuntu partition by mistake!

---

### Post by toolfan2k4 on 2009-01-01
I get this error and error 21 all the time. All I need to do is go into BIOS and reset the BIOS to defaults....works everytime for me.

---

### Post by shabinzon on 2009-01-01
No bro
I didn't format my ubuntu partition because via the LiveCD
I have access to the partitions and the files still there :D


Menu.lst:

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
# kopt=root=UUID=96d8d3df-e583-4c61-a90e-d215b703986d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96d8d3df-e583-4c61-a90e-d215b703986d

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
uuid		96d8d3df-e583-4c61-a90e-d215b703986d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=96d8d3df-e583-4c61-a90e-d215b703986d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		96d8d3df-e583-4c61-a90e-d215b703986d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=96d8d3df-e583-4c61-a90e-d215b703986d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		96d8d3df-e583-4c61-a90e-d215b703986d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d8d3df-e583-4c61-a90e-d215b703986d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		96d8d3df-e583-4c61-a90e-d215b703986d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96d8d3df-e583-4c61-a90e-d215b703986d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		96d8d3df-e583-4c61-a90e-d215b703986d
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

fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x603d9300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6502    52227283+   7  HPFS/NTFS
/dev/sda2            6503        7905    11269597+   f  W95 Ext'd (LBA)
/dev/sda3            7906        9727    14628087    7  HPFS/NTFS
/dev/sda5            6503        7905    11269566   83  Linux


I think the first one is the Windows Partition

the second one is the Linux partition
the third one is the New partition the I created
and the four one is the LiveCD

---

### Post by ajgreeny on 2009-01-01
> I think the first one is the Windows Partition

the second one is the Linux partition
the third one is the New partition the I created
and the four one is the LiveCD
No, I think that is where you are wrong, the first three partitions are all windows and the fourth is your ubuntu partition.  You should also have a small swap partition, which is not apparently present, but lets gat the system booting first and then deal with that problem.  Can you run the live CD again and show the output of ```
sudo blkid
```which will show us the UUIDs of all partitions.  We can the ensure you have the correct UUIDs showing in the menu.lst file.

---

### Post by shabinzon on 2009-01-01
blkid:

/dev/sda1: UUID="E0B0F038B0F0172E" TYPE="ntfs" 
/dev/sda3: UUID="F2F635B450A2555B" LABEL="disk0s3" TYPE="hfsplus" 
/dev/sda5: UUID="96d8d3df-e583-4c61-a90e-d215b703986d" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

---

### Post by caljohnsmith on 2009-01-01
Are you getting the Grub error before seeing the Grub menu, or after you get the Grub menu and select to boot Ubuntu?

---

### Post by shabinzon on 2009-01-01
Before I'll getting the menu bro

---

### Post by caljohnsmith on 2009-01-01
OK, how about trying:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Reboot, and let us know exactly what happens.

P.S. Happy New Year, ajgreeny! :)

---

### Post by ajgreeny on 2009-01-01
Well, your UUIDs in the menu.lst file are correct, so I'm a bit baffled at the moment.  I assume you are running 8.10 from the kernel numbers shown so the UUIDs shown on the second line of the various entries should work OK. but just to try it out, edit the menu.lst file for temporarily to show the second line of each as ```
root        (hd0,4)
``` (hd0,4 is the same as sda5 in grub language) instead of the UUID reference.  Make a backup first just in case and save it to a usb drive if possible, so you can get back to the UUID naming if necessary.

---

### Post by ajgreeny on 2009-01-01
> OK, how about trying:
 	Code:
 	sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit 
Reboot, and let us know exactly what happens.

P.S. Happy New Year, ajgreeny! :smile:
You're obviously on the same track as me with that answer, caljohnsmith, but it seems that the OP has got other problems such as needing a swap partition as well, so I hope we are not going to add to the difficulties.  I was assuming a grub menu appeared as I seem to remember grub error 17 appeared after the menu, when the partition of the operating system was wrong, but perhaps I'm not remembering correctly, and it is simply a case of grub pointing to the wrong partition for the menu.lst file.

Happy new year to you as well, and to all other forum users.

---

### Post by shabinzon on 2009-01-01
caljohnsmith: after I wrote root (hd0,4)

and than setup (hd0)

it's said Error 17: Cannot mount selected partition

ajgreeny: I don't understand what you told me to do on the menu.lst

can you explain me exactly again please

thanks in advance and happy new year

---

### Post by ajgreeny on 2009-01-01
I could but as you don't even see the grub menu there is no point doing so, that is obviously not the problem.

---

### Post by caljohnsmith on 2009-01-01
OK, I think you probably need to do an fsck:
```
sudo fsck -yCM /dev/sda5
```
Please let us know what that returns.

---

### Post by shabinzon on 2009-01-01
> **caljohnsmith said:**
> OK, I think you probably need to do an fsck:
```
sudo fsck -yCM /dev/sda5
```
Please let us know what that returns.

fsck 1.41.3 (12-Oct-2008)

---

### Post by caljohnsmith on 2009-01-01
So did the fsck return any errors? How about doing the grub commands from post #9 again, and please post the full output.

---

### Post by shabinzon on 2009-01-01
grub> setup (hd0)

output- Error 12: Invalid device request

---

### Post by ajgreeny on 2009-01-02
Another possibilty:-
Run the live CD and do the following, which is very similar to caljohnsmith's suggestions

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,4) ,probably]
then:
    ```
setup (hd1)
```
This is not the disk where your windows partition and MBR is, which according to your last post is not found by grub for some reason, but is your second hard disk, so you will need to go to BIOS and set the second hard disk as the first boot device
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

I just wonder if your disk mapping is incorrectly read by grub so the boot process is going to the wrong disk for the grub process.  If so it may be possible to put that right later, but let's get you booted first.

---

