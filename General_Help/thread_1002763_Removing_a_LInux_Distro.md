---
title: "Removing a LInux Distro"
date: 2008-12-05
forum: General Help
---

### Post by ASK87 on 2008-12-05
Hi,
I did initially install Linux Mint in my system and later installed Ubuntu 8.10. in sda1 i have Ubuntu and sda2 i have Mint. Since i installed Ubuntu the second, its GRUB is there in the MBR. I want to free the sda1 partition as i want to store data in it. Can i just format it, will it affect the GRUB, please help.

Thanks in advance

---

### Post by caljohnsmith on 2008-12-05
To let Mint take control of Grub in the MBR, just open a terminal (applications > accessories > terminal) and do:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
And you should be all set. :)

---

### Post by ASK87 on 2008-12-05
I tried the code from Mint. It shows the following on the first command

> grub> root (hd0,1)
File system type is ext2fs, partition type is 0x83

Does that mean i have to have ans ext2 partition??? All my partitions are ext3.

Thanks for the quick response

---

### Post by caljohnsmith on 2008-12-05
> **ASK87 said:**
> I tried the code from Mint. It shows the following on the first command
> grub> root (hd0,1)
File system type is ext2fs, partition type is 0x83 

Does that mean i have to have ans ext2 partition??? All my partitions are ext3.

Thanks for the quick response
You can run those Grub commands from either Mint or Ubuntu, it shouldn't matter; but it looks like your Mint Grub might be a slightly different version than Ubuntu's Grub since it echoes that file system info. Did you follow through with the "setup (hd0)" command? If it says it is successful, you should be all set. Also, you could check the file system type of sda2 with:
```
sudo blkid
```
If that says sda2 is ext3, I don't know why your Mint Grub would think it is ext2. How about posting the output of all the Grub commands and the blkid command above, and we can work from there if you want.

---

### Post by ASK87 on 2008-12-06
This is my output

> grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


This setup succeeds but when I restart its not reflected. Still ubuntu GRUB only shows up. How do i check if GRUB is installed in MBR???

> sudo blkid
/dev/sda1: UUID="c8411e87-cf79-4510-8734-f8ad1a89db2a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="f765ad6b-7f60-46ef-945e-d98f1cea4dfe" TYPE="ext3" 
/dev/sdb1: UUID="233f1f2b-5a2b-488c-ab95-f30ff2dd087f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="f3fdced5-241a-4b8f-abf8-ec3698c9dcfc" 
/dev/sdb3: UUID="b1a78b06-fc29-4006-917c-153718be15d0" SEC_TYPE="ext2" TYPE="ext3" 

This is my blkid output

---

### Post by caljohnsmith on 2008-12-06
How posting the contents of your menu.lst from your Mint sda2 partition:
```
cat /boot/grub/menu.lst
```
And do that when you are in Mint.

---

### Post by ASK87 on 2008-12-06
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint Fluxbox CE 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

#title		Linux Mint Fluxbox CE, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda2 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Linux Mint Fluxbox CE, kernel memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Ubuntu 8.10 #, kernel 2.6.27-7-generic (on /dev/sda1)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9f1fe97-3193-493c-a7b5-0cdd6c503585 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9f1fe97-3193-493c-a7b5-0cdd6c503585 ro single 
#initrd		/boot/initrd.img-2.6.27-7-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
#root		(hd0,0)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot


If you notice at the end, you will find Ubuntu at the end. It was added before the second install of Ubuntu, that is I installed in the following sequence. First Ubuntu in sda1, Mint in sda2, later tried Mandriva in sda1 and later Ubuntu(again) in sda1. Now thats why i have a ubuntu thing in mint menu.lst

---

### Post by caljohnsmith on 2008-12-06
So on start up, you don't see an option for "Linux Mint Fluxbox CE"? Do you have more than one HDD? How about posting the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by ASK87 on 2008-12-06
Output of fdisk
> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e427e42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+  83  Linux
/dev/sda2        39070080    78156224    19543072+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009bad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    39070079    19535008+  83  Linux
/dev/sdb2       310568580   312576704     1004062+  82  Linux swap / Solaris
/dev/sdb3        39070080   310568579   135749250   83  Linux

Partition table entries are not in disk order


Next set of outputs
> anish@anish-desktop ~ $ sudo xxd -l 2 -p /dev/sda
eb48
anish@anish-desktop ~ $ sudo xxd -l 2 -p /dev/sdb
eb48
anish@anish-desktop ~ $ sudo xxd -s 1049 -l 2 -p /dev/sdb
0081
anish@anish-desktop ~ $ sudo xxd -s 1049 -l 2 -p /dev/sda
01ff


---

### Post by caljohnsmith on 2008-12-06
OK, I believe I see the problem; you have Grub installed to the MBR of both your drives, and the Grub in the sdb drive points to sda1 for its boot files (which includes the menu.lst). So if you are still getting the Ubuntu Grub menu on start up, you must be booting the sdb drive. How about going into your BIOS and change it so that the sda drive boots first on start up. If you do that, I think it will solve your problem, but let me know if you run into problems.

---

### Post by ASK87 on 2008-12-06
Ok from what you say,
sda1- Ubuntu installed
sda2-Mint installed

sdb1-ext3 for data
sdb3-for data
sdb2-swap.

This is my config.

> you have Grub installed to the MBR of both your drives, and the Grub in the sdb drive points to sda1 for its boot files (which includes the menu.lst).
How is that GRUb in sdb points to sda1.Do you mean the MInt Grub is in sdb.

> How about going into your BIOS and change it so that the sda drive boots first on start up.
I think ill have a problem doing this.cause my sda is IDE and sdb is SATA and i think SATA must be the first boot device.

---

### Post by caljohnsmith on 2008-12-06
> **ASK87 said:**
> 
How is that GRUb in sdb points to sda1.Do you mean the MInt Grub is in sdb.

I think ill have a problem doing this.cause my sda is IDE and sdb is SATA and i think SATA must be the first boot device.
What I mean is that Grub is in the MBR (Master Boot Record) of your sdb drive, and it points to the sda1 partition for its boot files. The Grub you have installed to the MBR of your sda drive points correctly to your sda2 Mint partition, so if you were able to boot the sda drive, you should get the Mint Grub menu. Since you can't boot your sda drive, you can instead reinstall Grub to the MBR of you sdb drive and have it correctly point to sda2 instead sda1 for its boot files. To do that, just do:
```
sudo grub
grub> device (hd1) /dev/sda
grub> device (hd0) /dev/sdb
grub> root (hd1,1)
grub> setup (hd0)
grub> quit
```
Reboot, and let me know what happens on start up.

---

### Post by ASK87 on 2008-12-06
> grub> device (hd1) /dev/sda

grub> device (hd0) /dev/sdb

grub> root (hd0,1)
 Filesystem type unknown, partition type 0x82

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 



I am getting this.I dont know if i am understanding it right, am i making sdb1-hd0 by using the device command. Cant i say root (hd1) instead??

---

### Post by caljohnsmith on 2008-12-06
Sorry, that was my mistake for typing it out too fast; please see my previous post for the correction.

---

### Post by ASK87 on 2008-12-06
Ya i did what you said. I ahve the following problem
When it boots, the ubuntu menu does not show (thats good), but there is an error that says 'cannot boot Mint' and this shows a blue screen with only my Mint boot (as in menu.lst, posted here). But when i click it it shows an error and says 'press any key....'
I tried editing the boot and made the root (hd0,1) to (hd1,1), then it loaded.

NOw do i haev to make the changes in the menu.lst.And will it display the mint screen instead of the blue one after i make changes in menu.lst???

---

### Post by caljohnsmith on 2008-12-06
OK, I think I see the problem again; first open up your Mint menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "timeout 0" line to:
```
timeout 10
```
Or however many seconds you want before Grub tries to load the default entry. Then change your Mint entry to use (hd1,1):
```
title Linux Mint Fluxbox CE
root [COLOR="Blue"](hd1,1)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
```
And change "#groot=(hd0,1)" to:
```
#groot=(hd1,1)
```
Also, you can either manually copy over your Ubuntu's boot entries from your Ubuntu menu.lst, or you can link to your Ubuntu's menu.lst by adding the following entry in Mint's menu.lst:
```
title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
You might also have to edit Ubuntu's menu.lst so that the entries use (hd1,0) and not (hd0,0), or it might be that the entries use "uuid" instead of the "root" line. But give the above steps a try first and let me know how it goes.

---

### Post by ASK87 on 2008-12-06
Oh, that rectifies my problem. Thanks a lot for the help. Everything is working fien. Now i have only 2 more queries.
1. Now can i just format the partition which i want to free, which was my original query.

2. Now hereafter when i am installing any new partition, how do i make it not install the GRUB, since i want to retain the Mint GRUB?

Regards

---

### Post by caljohnsmith on 2008-12-06
> **ASK87 said:**
> Oh, that rectifies my problem. Thanks a lot for the help. Everything is working fien. Now i have only 2 more queries.
1. Now can i just format the partition which i want to free, which was my original query.

Yes, you should be fine now.
> **ASK87 said:**
> 
2. Now hereafter when i am installing any new partition, how do i make it not install the GRUB, since i want to retain the Mint GRUB?

Regards
When you install a new distro and want Mint to stay in control of Grub, usually the best way to accomplish that is to let the distro install its own boot loader (like Grub), but make sure the distro installs its boot loader to the boot sector of its own partition, not the MBR. For instance, when you go through a Ubuntu installation and want to install Ubuntu to sda1, if you click on the "advanced" button near the end, you can tell Ubuntu to install Grub to "/dev/sda1", which is the boot sector of sda1. If you instead tell the installer to install Grub to /dev/sda, that would be the MBR. If you have the distro install its boot loader to the boot sector of its own partition, then to boot it all you have to do is add an entry in your Mint menu.lst like:
```
title New Distro's Grub Menu
root (hdX,Y)
chainloader +1
```
Or you can use the "configfile" notation that I gave in my last post to link directly to the distro's menu.lst/grub.conf file if it has one. Anyway, good luck and have fun trying out new distros.

---

### Post by ASK87 on 2008-12-06
Thanks a lot mate. Thats was really helpful and i learned a lot.
Any suggestions for a lightweight distro???

---

### Post by caljohnsmith on 2008-12-06
Well, if you like Ubuntu and Mint, you could try Fluxbuntu as a "lighter weight" alternative. I'm not sure how lightweight you want it though. If you want a really barebones distro, you could try something like Puppy Linux.

---

