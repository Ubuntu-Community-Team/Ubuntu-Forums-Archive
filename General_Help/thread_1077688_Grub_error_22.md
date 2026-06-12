---
title: "Grub error 22"
date: 2009-02-22
forum: General Help
---

### Post by CircuitMeltdown on 2009-02-22
I have 2 harddrives on my computer. Windows XP is on my first hard drive. I have ubuntu 8.10 on my second hard drive on the first partition. Recently I decided to try the latest version of Kubuntu. I installed it on my second hard drive on a different partion than Ubuntu, but sharing the swap. I set up startup manager in Ubuntu to start grub the way I wanted it, but after Kubuntu was installed it changed back to default settings, I'm assuming the Kubuntu grub took over. 

I recently deleted the Kubuntu partition using Ubuntu partition manager, but when I restarted my computer I got an error 22 from grub. How do I fix this? I want it to recognize grub from ubuntu again. 
And if I decide to install Kubuntu again, how can I make sure that it recognizes the Ubuntu grub and not the Kubuntu grub? 

Please help. Thanks.

---

### Post by Elfy on 2009-02-22
You need to reinstall grub for the ubuntu - you can use the livecd - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start 

If you want to install kubuntu again - then when you get to the final screen - there is an advanced option - use that and install grub to the partition you installed kubuntu on rather than the default hd0.

Then add the kubuntu install to the ubuntu grub menu

---

### Post by CircuitMeltdown on 2009-02-22
Thanks! I'll try that now. 

And just to clarify, when installing kubuntu agian I should set grub to be installed on the kubuntu partition? is there anyway I can just opt not to install grub when I install kubuntu?

---

### Post by Elfy on 2009-02-22
Possibly - but then I'm not sure how you could boot it then - I use chainloading - I have my grub installed on jaunty and have grub installed for other versions. For instance if kubuntu was on hd0,3 then install grub there and chainload it.
> 
title 		---OTHER OPERATING SYSTEMS---
root

title		---OzOs---
root		(hd0,3)
chainloader 	+1

title 		---Intrepid---
root		(hd0,1)
chainloader	+1

title		---Xubuntu
root		(hd2,3)
chainloader	+1

---

### Post by CircuitMeltdown on 2009-02-22
> **forestpixie said:**
> You need to reinstall grub for the ubuntu - you can use the livecd - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start 


Thanks again, that worked for me. 

I am going to try to install kubuntu and chainload it, I just don't know how to tell what the correct root numbers are for the partitions. windows xp is root (h0,0), and that is also the one that grub is installed on. I don't know the other root numbers, or how to find out.

---

### Post by CircuitMeltdown on 2009-02-22
Now I'm getting an error when I try to start up windows xp. "error 13: invalid or unsupported executable file". What should I do? please help. Thanks.

---

### Post by Elfy on 2009-02-23
Boot into ubuntu - open a terminal, run these and post results please

```
sudo fdisk -l
blkid
cat /boot/grub/menu.lst
```

---

### Post by CircuitMeltdown on 2009-02-23
I didn't know which parts you wanted, so I posted it all. There are two entries for windows xp in the grub menu.lst because I wasn't sure which part to pout the entry in. It wasn't working before I put the windows xp entry directly under the linux entries either. 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46184617

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9729    37190475    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x568f3077

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056   83  Linux
/dev/sdb2            7296       12766    43945807+   5  Extended
/dev/sdb3           35093       60763   206193664+   b  W95 FAT32
/dev/sdb5            7296        7903     4883728+  82  Linux swap / Solaris
kristine@kristine-desktop:~$ sudo fdisk -l

```

```
 menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		60

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color dark-gray/magenta black/light-gray

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4

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
# defoptions=quiet splash vga=799

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8003aecb-5c08-4c3a-97d7-d1a98dd15ec4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4 ro quiet splash vga=799 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8003aecb-5c08-4c3a-97d7-d1a98dd15ec4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		8003aecb-5c08-4c3a-97d7-d1a98dd15ec4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4 ro quiet splash vga=799 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8003aecb-5c08-4c3a-97d7-d1a98dd15ec4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8003aecb-5c08-4c3a-97d7-d1a98dd15ec4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1

```

---

### Post by Elfy on 2009-02-23
mmm - looks ok to me, can you do

```
cat cat /boot/grub/menu.lst~
```

See if you have a backup and check that against the non-working one

If it doesn't give the old menu list do

```
ls /boot/grub/menu*
``` and find the backup. If there are no obvious differences you could try to use your windosc to fix the windows boot from the recovery console using the fixboot command - check that it boots then reinstall grub using the livecd again.

---

### Post by caljohnsmith on 2009-02-23
To get a Grub error 13 with your current Windows entry that uses (hd0,0) means that you might be booting the Linux drive on start up instead of the Windows drive, because then (hd0,0) would be booting sdb1 which is your linux partition. So if you are booting your linux drive on start up, your Windows entry should be:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
How about giving that a shot and let me know if it works or not.

---

### Post by CircuitMeltdown on 2009-02-23
Thanks for the fast replys :). 

I will try both of your suggestions when I get home later tonight.

---

### Post by CircuitMeltdown on 2009-02-23
> **caljohnsmith said:**
> To get a Grub error 13 with your current Windows entry that uses (hd0,0) means that you might be booting the Linux drive on start up instead of the Windows drive, because then (hd0,0) would be booting sdb1 which is your linux partition. So if you are booting your linux drive on start up, your Windows entry should be:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
How about giving that a shot and let me know if it works or not.

Thanks! Worked like a charm.

---

### Post by caljohnsmith on 2009-02-23
Glad to hear that worked OK; cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

