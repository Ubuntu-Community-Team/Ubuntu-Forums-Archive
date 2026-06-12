---
title: "HELP Ubuntu has stopped my xp Booting!!!!!!!!!!!!"
date: 2008-12-07
forum: General Help
---

### Post by mr_shedges on 2008-12-07
Hello

I want to start good, I like Linux. I like that its free I like that I can contribute, I like that it has such a nice feel.

But

My parents had an issue where they decided to install a lovely virus. I finaly got it out of the machine and decided that I would install Ubuntu and get em to use that.

:-({|=God do I wish I did not.:-({|=

They use a speed touch usb modem. I have tried every how to package  etc. none have worked. So no internet. Considering that my pareents pretty much only use the internet or word processor it aint much use to them.

So I think cool i'll change the grub lst and make windows the default. Low and behold Windows no longer works. Some files have been currupted by the install of Ubuntu and it no longer works.

:-({|=PLEASE HELP......:-({|=

If it was my machine would not care as I back up all of my stuff.  My parents how ever think backing up is only for cars out of the drive.

How do I get the speedtouch to work (ps it isn't showing in the usb/devices section either)? How do I get Windows to work?

:-({|=PLEASE HELP.........!!!!!!!!!!!!:-({|=

---

### Post by oilchangeguy on 2008-12-07
> **mr_shedges said:**
> Hello

I want to start good, I like Linux. I like that its free I like that I can contribute, I like that it has such a nice feel.

But

My parents had an issue where they decided to install a lovely virus. I finaly got it out of the machine and decided that I would install Ubuntu and get em to use that.

:-({|=God do I wish I did not.:-({|=

They use a speed touch usb modem. I have tried every how to package  etc. none have worked. So no internet. Considering that my pareents pretty much only use the internet or word processor it aint much use to them.

So I think cool i'll change the grub lst and make windows the default. Low and behold Windows no longer works. Some files have been currupted by the install of Ubuntu and it no longer works.

:-({|=PLEASE HELP......:-({|=

If it was my machine would not care as I back up all of my stuff.  My parents how ever think backing up is only for cars out of the drive.

How do I get the speedtouch to work (ps it isn't showing in the usb/devices section either)? How do I get Windows to work?

:-({|=PLEASE HELP.........!!!!!!!!!!!!:-({|=

first, ubuntu did not corupt any windows files. that's not possible. second, did you ask your parents if it was ok to change to a new os? maybe they don't want to have to learn linux. why not just do a fresh install of windows? and use a good anti-virus program (avg's free version). not the expired version of norton, or mcafee that came with the computer.

---

### Post by caljohnsmith on 2008-12-07
What exactly happens when you try and boot Windows? Any errors? How about booting into Ubuntu, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there if you want.

---

### Post by mr_shedges on 2008-12-07
Grub is working fine.

The list is correct, and the order as per normal.

Ubuntu is working fine asdie from the issue of not getting the speedtouch modem working.

When I select windows from the list it starts to load I get a flicker of the xp boot screen then it reboots.

In safe mode I get to the mup.exe file then it reboots.

Read a number of posts that said they updated ubuntu and they got a similar issue. Presumed it could be similar. happy to be wrong and blame XP for its self preservation.

With my parents should it matter? Ubuntu is just as good as XP, once it is set up, as long as they do not try to do any techy stuff it should last better than XP. That is the point. If I am wrong i'll just tell them to buy another Micro$oft clone and the majority of the world can continue to ignore Linux.

Any ideas?

if I could get the internet working on ubuntu it wouldn't be such a problem.

Cheers in advance.

---

### Post by mr_shedges on 2008-12-07
posted by accident been a long day.

---

### Post by mr_shedges on 2008-12-07
**Sudo fdisk -lu **
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xa617a617 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   215560169   107780053+   c  W95 FAT32 (LBA) 
/dev/sda2       215560170   312576704    48508267+   5  Extended 
/dev/sda5       215560233   309556484    46998126   83  Linux 
/dev/sda6       309556548   312576704     1510078+  82  Linux swap / Solaris 
 
**cat /boot/grub/menu.lst **
 
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
# kopt=root=UUID=cace332d-c820-45d0-985d-02fd0f42a879 ro 
 
## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,4) 
 
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
 
title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cace332d-c820-45d0-985d-02fd0f42a879 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 
 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cace332d-c820-45d0-985d-02fd0f42a879 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
 
title		Ubuntu 8.04, memtest86+ 
root		(hd0,4) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Home Edition 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1

---

### Post by caljohnsmith on 2008-12-07
Do you have your Windows Install CD? If so, how about booting that, go to the "recovery console" and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. After that, reboot, and let me know exactly what happens when you try and boot Windows again.

---

### Post by mr_shedges on 2008-12-07
I have a xp disk it is a "backUp" as i only have a recovery disk. I have entered the recovery console and it does not reconise any drives.

If the ChkDsk works with out it reconising a disk i'll let you know .

In the UK so have given up for the night will have another good look tomorrow. Well my parents kicked me out saying go to bed. Old people who'd have em.

Do you know if the ChkDsk will work if the drive is not found?

---

### Post by Kizamime on 2008-12-07
No, Checkdisk wont work if there isnt any disk to check. Thats how winblows is....Well, even in Linux, how would you be able to do anything with something that isnt there?

---

### Post by mr_shedges on 2008-12-08
I presumed as much, well it looks like I may have found a problem. any ideas on how to resolve? how do I get it to find a drive????

[CENTER]):P):P):P):P):P):P):P):P[/CENTER]

---

### Post by mr_shedges on 2008-12-08
Ah ha think I have something after a lot of digging, found that the file system is not reconised at some sort of level. it appears that  when I resized the drive to install ubuntu the files system decided it was going to throw a wobbler.

Trying to think of the best way to rectify this open to suggestions. Even open to suggestions that I am totally wrong.

---

