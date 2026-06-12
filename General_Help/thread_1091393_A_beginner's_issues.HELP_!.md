---
title: "A beginner's issues.HELP !"
date: 2009-03-09
forum: General Help
---

### Post by kiddd on 2009-03-09
Hello to everyone ! I used Windows all my life but now I felt interested in finding out the meaning of the LINUX world.In Windows XP I have two HDD partitions : one with the OS and another one with my files and documents.What I did was create a new partition ( 20 gb for Linux ) using Partition Magic , as Primary - (ext3) and install the distribution there.It went OK but in the end I figured that the dual-boot screen ( grub ) does not see my Windows OS , just Ubuntu --- it is strange because from Ubuntu in MY PC I can see both partitions I had created with Win XP , so it's not like i've erased these partitions ).PLEASE help me .. what should I do ?!

---

### Post by mªrty on 2009-03-09
I may be mistaken, but I believe this is what's going on: When your computer turns on, it goes through the POST (power on self-test) where it checks memory and peripherals, etc. Then it boots to the Master Boot Record on the hard drive. When you installed Ubuntu, it overwrote the Master Boot Record which previously looked for windows.

I think GRUB (the Ubuntu boot loader) has an option to boot to a specific partition/drive. If so, you should just point that to your windows partition. Can anyone else confirm this?

---

### Post by kanikilu on 2009-03-09
From Ubuntu, can you post the contents of your /boot/grub/menu.lst file and the output of **fdisk -l** from the terminal?

---

### Post by ponyexpress on 2009-03-09
> **mªrty said:**
> I may be mistaken, but I believe this is what's going on: When your computer turns on, it goes through the POST (power on self-test) where it checks memory and peripherals, etc. Then it boots to the Master Boot Record on the hard drive. When you installed Ubuntu, it overwrote the Master Boot Record which previously looked for windows.

I think GRUB (the Ubuntu boot loader) has an option to boot to a specific partition/drive. If so, you should just point that to your windows partition. Can anyone else confirm this?

You may have to hit escape to view other boot options.

---

### Post by kiddd on 2009-03-09
> **mªrty said:**
> I may be mistaken, but I believe this is what's going on: When your computer turns on, it goes through the POST (power on self-test) where it checks memory and peripherals, etc. Then it boots to the Master Boot Record on the hard drive. When you installed Ubuntu, it overwrote the Master Boot Record which previously looked for windows.

I think GRUB (the Ubuntu boot loader) has an option to boot to a specific partition/drive. If so, you should just point that to your windows partition. Can anyone else confirm this?


Thank you for your time first of all.Just to sum up because I might not understand much about all this stuff , I just want to get the screen from where I choose to boot either WIN either UBUNTU..thank you once more.

---

### Post by kiddd on 2009-03-09
> **kanikilu said:**
> From Ubuntu, can you post the contents of your /boot/grub/menu.lst file and the output of **fdisk -l** from the terminal?


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
# kopt=root=/dev/sda3 ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda3 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda3 ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
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
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro ROOTFLAGS=syncio single 
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


This is the "menu.lst" file content you talked about.I do not know what you are talking about when saying "the output of **fdisk -l** from the terminal?" ...sorry..

---

### Post by miegiel on 2009-03-09
> **kiddd said:**
> I do not know what you are talking about when saying "the output of **fdisk -l** from the terminal?" ...sorry..

Terminal (or cli) is what you called a dos window in windows :twisted:

ps put the stuff in code boxes so you don't get :(:P:):o:D;):KS
```
:(:P:):o:D;):KS
```

---

### Post by kiddd on 2009-03-09
> **miegiel said:**
> Terminal (or cli) is what you called a dos window in windows :twisted:

ps put the stuff in code boxes so you don't get :(:P:):o:D;):KS
```
:(:P:):o:D;):KS
```

---from terminal---

kiddd@kiddd-desktop:~$ fdisk -l
Cannot open /dev/sda
kiddd@kiddd-desktop:~$ 


---


What should I do next ?

---

### Post by lindsay7 on 2009-03-09
go to Applications (menu bar on top of screen), accessories, terminal, type fdisk -l (the lower case letter l not the number one), copy and paste the results in the reply box, click on the # to have the results show up as code.

---

### Post by lindsay7 on 2009-03-09
sorry I have a type, it should read type fdisk -l

---

### Post by miegiel on 2009-03-09
> **kiddd said:**
> ---from terminal---

kiddd@kiddd-desktop:~$ fdisk -l
Cannot open /dev/sda
kiddd@kiddd-desktop:~$ 


---


What should I do next ?

try
```
sudo fdisk -l
```

kind of of topic:
Often administrative commands need the "sudo" command in front of them. This allows you to run commands only as administrator when you need to and is a lot safer then being administrator all the time. The password will be buffered for 15min so you will only need to give it once.

---

### Post by kanikilu on 2009-03-09
It doesn't look like GRUB knows about your Windows partition.

To list your partition information, go to Applications > Accessories > Terminal and at the prompt, type the following ```
sudo fdisk -l
``` it will ask for your password (it will not be echoed on the screen, so just type it and press enter). The output of that command should help determine how your menu.lst file should be modified to allow you to boot to Windows.

Although, if Windows is on the first partition, you could try adding the following as a bootable option after the kernels in menu.lst:

> title Microsoft Windows
root (hd0,0)
makeactive
chainloader +1

Then when you reboot, press ESC when prompted to choose which OS to boot. Without knowing how your partitions are setup, this is just a guess, though, so it might not work...

---

### Post by lindsay7 on 2009-03-09
The command should be   sudo fdisk -l
then type your password

---

### Post by kiddd on 2009-03-09
> **lindsay7 said:**
> sorry I have a type, it should read type fdisk -l

kiddd@kiddd-desktop:~$ fdisk -l
Cannot open /dev/sda
kiddd@kiddd-desktop:~$


Was this what you wanted to see ?

---

### Post by ponyexpress on 2009-03-09
> **kiddd said:**
> ---from terminal---

kiddd@kiddd-desktop:~$ fdisk -l
Cannot open /dev/sda
kiddd@kiddd-desktop:~$ 


---


What should I do next ?

sudo fdisk -l

---

### Post by kiddd on 2009-03-09
> **ponyexpress said:**
> sudo fdisk -l

kiddd@kiddd-desktop:~$ sudo fdisk -l
[sudo] password for kiddd: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77757775

   Device Boot                     Start         End      Blocks   Id  System
/dev/sda1   *                           1        3218    25848553+   7  HPFS/NTFS
/dev/sda2                            3219       27851   197864572+   f  W95 Ext'd (LBA)
/dev/sda3                           27852       30401     20482875  83  Linux
/dev/sda5                            3219       27851    197864541   7  HPFS/NTFS
kiddd@kiddd-desktop:~$

---

### Post by kanikilu on 2009-03-09
I thought you said there were 2 hard drives in your computer? Anyways, it looks like Windows is the first partition, so I think adding that stanza I put in my previous post should work. Try ```
gksudo gedit /boot/grub/menu.lst
``` and copy and paste the "Windows XP" stanza from my other post after the end of the "automagic kernel list". Or add it prior to the list if you want it to be the default. You might also want to increase the timeout variable if you need more time for it to allow you to hit ESC to get into the boot menu. I think the default is 3 seconds.

---

### Post by kiddd on 2009-03-09
IT WORKED !!! Thanks to everyone who posted in order to help me solve this issue of mine ! I can now enter WIN OS.I just added that stranza at the end of the menu.lst document and it had worked ! Once again , thank you all ! :D

---

### Post by kanikilu on 2009-03-09
Glad that worked out, because reinstalling grub or anything like that is still a little too foreign for me to recommend to or help others with ;)

---

