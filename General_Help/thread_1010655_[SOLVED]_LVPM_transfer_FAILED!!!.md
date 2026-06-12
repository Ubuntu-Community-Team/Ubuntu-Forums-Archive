---
title: "[SOLVED] LVPM transfer FAILED!!!"
date: 2008-12-14
forum: General Help
---

### Post by Jammanuser on 2008-12-14
LVPM transfer FAILED!!! :( I tried transferring my Wubi install to a dedicated partition...and it gave me a message saying that it was done, and had completed successfully (which it thought was odd, because in my mind at least it should have taken a LOT longer...and it only took a few SECONDS!), and that i needed to reboot...well i rebooted, got back to the same boot entry in my WINDOWS boot loader, selected it...and guess what happened? i got right back into my Wubi install...and so i decided to run it again, which i did, after which i got back to the SAME boot entry again, and once more i chose it, and got back into frickin Wubi once again! :mad: It has obviously failed completely, because when i tried looking in my BootIT NG (partition program) menu, i had lost the 50GB partition that i had created for Ubuntu, and it was now simply "free space"! not only that, but it also overwrote the FIRST partition in the menu (which fortunately was only a 36MB partition for a dell utility)! 

In my MBR partition table, were listed (BEFORE the attempted transfer with LVPM!) four partitions in the following order:

Ubuntu 8.10 (the partition that i had created for the transfer)
Dell utility (this is the 38MB partition that i mentioned above)
Recovery partition 
OS-2 (this is where Windows is installed)

Hmm...now that i think about it, perhaps i made a mistake with the partition that i chose with LVPM (although it seems strange it didn't give me a message saying that the partition was large enough!)...i know i selected "sda1" in the "choose partition" dialog box of LVPM, thinking that that would be the correct partition, since it was the first in the MBR table!

Anyway, i hope somebody can explain why LVPM didn't work for me...or can tell me where i went wrong! 

Cheers! ):P

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-14
Well...i think i figured out where i went wrong! ;) it seems that LVPM was able to read the partitions in the EMBR (Extended Master Boot Record used by BootIt NG, and enabling the ability to have more than 4 primary partitions), in addition to the standard MBR...so i guess when LVPM detected that the partition order was different in the EMBR than in the MBR, it produced weird results when trying to migrate to a partition labeled #1 in the MBR but #4 in the EMBR! :popcorn:

After a little tinkering and hacking, that thought occured to me, and so after fixing the messed up partitions using BootIt NG, and setting the place of the Ubuntu partition #4 in both instead of just in the MBR, i tried LVPM again, and this time it took the expected amount of time to migrate the files over to the dedicated partition!

I don't know yet, though, if it has worked, because i haven't set the partition that i have migrated to active yet...i will post here an update when i do! :guitar:

Cheers! ):P

Jam Man

:popcorn:

---

### Post by Jammanuser on 2008-12-14
Nope...still didn't work! :confused: i tried setting the partition active again, and then rebooting it, but i got the same error as the last time! it seems that LVPM doesn't want to work... 

I would really appreciate if someone could offer a solution for my problem! ;) Hell! at this point, **any** comments or suggestions would be much appreciated! ):P

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-14
I get error 17 (cannot mount partition) when i use the Grub bootloader...:mad:

Anyone know what the problem could be? :guitar:

Thanks in advance! :popcorn:

Jam Man

):P

---

### Post by azmo35 on 2008-12-14
Hello mate but i think you only need to edit the menu.1st and add this (hd0.1)
title		Ubuntu 8.04.1
root	#-o(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f  ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
the (hd0....) start for windows (hd0.0) ubuntu (hd0.1) and so one,don't be deceived by gparted because we show (sd0.2) or (sd0.3) bla..bla..you can do this with live cd /boot/grub/menu.1st.):P

---

### Post by Jammanuser on 2008-12-14
> **azmo35 said:**
> Hello mate but i think you only need to edit the menu.1st and add this (hd0.1)
```
title		[COLOR="Red"]Ubuntu 8.04.1[/COLOR]
root	#-o(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ad51ef36-da6e-4e45-8d6a-c989ffa69d2f  ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
```
the (hd0....) start for windows (hd0.0) ubuntu (hd0.1) and so one,don't be deceived by gparted because we show (sd0.2) or (sd0.3) bla..bla..you can do this with live cd /boot/grub/menu.1st.):P

Thanks for the reply! :guitar: although i'm not exactly sure what u were trying to say... :confused: Shouldn't it be "Ubuntu 8.10" instead of "Ubuntu 8.04.1" since that's actually the version of Ubuntu it is? and r u saying that i should use the LiveCD to edit the menu.lst? if so, then am i supposed to put in all of the above code that I distinguished from the rest of the text...?

Anyway, while i'm waiting for ur next reply, i will try to make sense of what u wrote, and then do what u suggested! ;) Thanks!

Cheers! ):P

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-15
I also wanted to mention that LVPM apparently deleted my swap partition as well! It was **supposed** to use it... :D
i created one for the transfer, with BootIt NG...but LVPM apparently deleted it! :-k I suppose its possible though that the partition could still exist, and BootIT NG can just not read it, which would be odd...

---

### Post by Jammanuser on 2008-12-15
Well...i tried it, but it still didn't work. :( I added **(hd0,1)** like u said to the menu.lst...i found the place u were talking about (although the title was indeed Ubuntu 8.10 like i thought), and saw where "root" was, and right next to it the parenthesis "()" in which i entered "hd0,1". i also did this to the recovery one, and to the memtest one. (I'll try to post later the complete menu.lst so u can take a look at it)

One thing i forgot to mention before is my grub menu is lost now...when i boot it, it goes straight to the Windows boot menu. So what i tried to do to see if what u suggested worked, is add a boot entry to the WINDOWS boot menu, titled "Ubuntu 2", with EasyBCD...of course selecting the right partition to boot from, i.e. partition 3 (20 GB) as it shows up in EasyBCD. I also made sure to select Grub in the drop-down menu. 

I'm not sure, azmo, if u have ever used EasyBCD before...but its basically a program for modifying the Windows bootloader quickly and easily...there's several different OSes that EasyBCD can work with, including Linux. And so it was **supposed** to work with EasyBCD... :confused:

Anyway, thanks for ur help, and I would certainly appreciate any **further** help! ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by azmo35 on 2008-12-15
Hi, first don't use the the code because that way you never will boot ubuntu 8.10 that is only for example the thing you need add is (hd0.1) i assume you only have windoze V and ubuntu 8.10 if so this is only what you have to add on menu.1st or you can first click on E when grub is booting and add (hd0.1) and B for boot if this work then you need edit sudo gedit /boot/grub/menu.1st.I hope this help,AZMO.
PS:you can do the same with live cd to edit menu.1st and to see with gparted all about you partitions.

---

### Post by Jammanuser on 2008-12-15
> **azmo35 said:**
> Hi, first don't use the the code because that way you never will boot ubuntu 8.10 that is only for example the thing you need add is (hd0.1) i assume you only have windoze V and ubuntu 8.10 if so this is only what you have to add on menu.1st or you can first click on E when grub is booting and add (hd0.1) and B for boot if this work then you need edit sudo gedit /boot/grub/menu.1st.I hope this help,AZMO.
PS:you can do the same with live cd to edit menu.1st and to see with gparted all about you partitions.

Yeah...never mind about that now! :D I finally figured out precisely what u were talking about, and i've already (like i mentioned above) edited the menu.lst...but it still didn't work! :confused:

Cheers! ):P

Jam Man

:guitar:

---

### Post by azmo35 on 2008-12-15
See this link maybe give you more ideas [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Jammanuser on 2008-12-15
> **azmo35 said:**
> See this link maybe give you more ideas [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Thanks for the link. It gives instructions on how to do what i've **already** done using EasyBCD. :D It doesn't describe how to change where the boot entry points to...which is what i suspect is my problem now, and is what i need to figure out. Its obvious to me that its pointing to the wrong thing, because when i open up EasyBCD, and go to "View Settings" it shows the bootloader path for the Ubuntu 2 entry as: \NST\nst_grub-EE9F9FAF81C48EDF78CC68AEBDAF799C.mbr

So i go to that file in **C:/NST/nst_grub-EE9F9FAF81C48EDF78CC68AEBDAF799C.mbr** and this is what it shows:

```
ë<                                                           ú3À&#381;Ð¼ |¸°&#381;Ø&#381;À¹ &#8249;ñ¿ ó¥¸ÐP&#381;Ø&#381;À¸dPËû¾èo ¹Áÿº&#8364; 3ÛS» |S¾é¸BÍs¸BÍs¸BÍr.&>þ}Uªu%¸  Àt&¢$|¸  Àt&¢%|¸  &£|¸  &£|Ë¾&#8212;è ´Ít2äÍëô2äÍ3ÒÍü¬
ÀuÃV´Í^ëò   |  õ¸3            BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant http://www.winimage.com/bootpart.htm

[B]Loading new partition

Bootsector from C.H. Hochst&#8222;tter

 Cannot load from harddisk.

Insert Systemdisk and press any key.[/B]

                                     Uª
```

The bold part of the code is the same message that shows up when i try to select the "Ubuntu 2" boot entry. So its obvious to me that its pointing to the wrong thing, and so what i need to know is how to edit the NST file **correctly** so that it will be pointing to the right place! :p

Cheers! ):P

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-15
hmm...i found something else. here's a quote from [HERE]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors") that might partly explain why it didn't work:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

That's the original error that i got when trying to boot Ubuntu (using Grub) after the transfer...its possible that the reason it doesn't work is because i chose "Linux Native" filesystem type in BootIt NG. although that would be odd... :confused:

---

### Post by Jammanuser on 2008-12-15
Here is the output that i get with "sudo fdisk -l":

```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x3c5a8d58 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           5       40131    6  FAT16 
/dev/sda2           38911       38911        8032+  df  BootIt 
/dev/sda3   *        1280       31541   243072920    7  HPFS/NTFS 
/dev/sda4           31542       34090    20474842+  83  Linux 

Partition table entries are not in disk order 
ubuntu@ubuntu:~$ 
```

Hope it helps someone figure out the solution to my problem! :D

---

### Post by Jammanuser on 2008-12-15
And here is a copy of the menu.lst file:

```
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
# kopt=root=UUID=b18b9c1c-30f6-4cae-b04e-6695ca9ddb79  ro ROOTFLAGS=syncio 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=()/ubuntu/disks 

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
root		(hd0,1)/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b18b9c1c-30f6-4cae-b04e-6695ca9ddb79  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
root		(hd0,1)/ubuntu/disks 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b18b9c1c-30f6-4cae-b04e-6695ca9ddb79  ro ROOTFLAGS=syncio  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, memtest86+ 
root		(hd0,1)/ubuntu/disks 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title		Microsoft Windows XP Professional 
root		(hd0,1) 
savedefault 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda3 
title		Windows Vista/Longhorn (loader) 
root		(hd0,2) 
savedefault 
chainloader	+1 



title Ubuntu-on-/dev/sda1 
root (hd0,0) 
configfile /boot/grub/menu.lst 




title Ubuntu-on-/dev/sda1 
root (hd0,0) 
configfile /boot/grub/menu.lst 




title Ubuntu-on-/dev/sda4 
root (hd0,3) 
configfile /boot/grub/menu.lst 

 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


title Windows 
root (hd0,2) 
makeactive 
chainloader +1 
boot 


title Windows Vista/Longhorn (loader) 
root (hd0,2) 
makeactive 
chainloader +1 
boot
```

Hopefully someone can figure out what i'm doing wrong! ;)

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-15
Whooopppeeeeeee!!! :D :D :D :D it WORKED!!! azmo...u r a GENIUS!!! :D i went ahead and tried the transfer again (so that Grub would work again) to the same partition, and then edited the menu.lst file again (this time from my Wubi install, instead of the LiveCD)...and put "hd0,3" in "()" instead of "hd0,1", because i noticed that it said farther down in the menu.lst that the root was "hd0,3", and i guessed **correctly** that that was the correct device in my case...and i rebooted, and it WORKED!!! Whoa! :D 

I don't know how to thank u enough...

Now i've finally got Ubuntu installed (as a **real** install, instead of within crappy Windows!), in **addition** to Wubi, which i'll probably uninstall once i'm sure that the real install works fine... 

Thank you, thank you, thank you, thank you...oh! and thanks again, azmo! :lolflag:

Jam Man

:guitar:

---

### Post by azmo35 on 2008-12-16
Sorry,mate but I'm not a genius the thing i can say is learn as mutch you can and ubuntu as been a good teacher,I'm happy that i poit you to the correct location.

---

