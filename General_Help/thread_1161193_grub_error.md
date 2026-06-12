---
title: "grub error"
date: 2009-05-16
forum: General Help
---

### Post by pluMmet on 2009-05-16
***Was resolved but when I woke up today it's back**

I see lots of grub problems and I've tried a few solutions but non of them have worked so I though I would differ to someone who might know.

Here is my fdisk:
```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f57111c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716   83  Linux

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce7549db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7716

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       31926   256445563+   7  HPFS/NTFS
/dev/sdc2           31927       57685   206909167+   7  HPFS/NTFS
/dev/sdc3           57686       87508   239553247+  83  Linux
/dev/sdc4           87509       91201    29664022+   5  Extended
/dev/sdc5           87509       91201    29663991   82  Linux swap / Solaris
```

Here is my grub menu:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66c2bf84-4e90-4c91-8b39-e48099d7065b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66c2bf84-4e90-4c91-8b39-e48099d7065b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
rootnoverify	(hd2,0)
savedefault
makeactive
map (hd2) (hd0)
map (hd0) (hd2)
chainloader	+1
```



Help!

It's ERROR:22 No such partition.

---

### Post by Legace on 2009-05-16
Umm.. When do you get the error? When booting into Windows or Ubuntu? Or both?

---

### Post by pluMmet on 2009-05-16
Thanks for answering :)

Ubuntu loads fine. Windows does not.

---

### Post by Legace on 2009-05-16
Is Windows installed on sdc (hd2,0) or (hd2,1)?

Try this:
```
title		Microsoft Windows XP
rootnoverify	(hd2,1)
savedefault
makeactive
chainloader	+1
```

If that doesn't work, type in **blkid** in Terminal and post output here.
And did Windows boot fine before? If it did, then what happened to Windows so that it stopped from booting?

---

### Post by pluMmet on 2009-05-16
I tried, same error but I'm sure it's installed on the /dev/sdc1 * 1 31926 256445563+ 7 HPFS/NTFS

---

### Post by Legace on 2009-05-16
> **pluMmet said:**
> I tried, same error but I'm sure it's installed on the /dev/sdc1 * 1 31926 256445563+ 7 HPFS/NTFS

OK.
Type in **blkid** in Terminal and post output here.
And did Windows boot fine before? If it did, then what happened to Windows so that it stopped from booting?

---

### Post by pluMmet on 2009-05-16
/dev/sda1: UUID="66c2bf84-4e90-4c91-8b39-e48099d7065b" TYPE="ext4" 
/dev/sdc1: UUID="72D42427D423EC53" TYPE="ntfs" 
/dev/sdc2: UUID="01C989B85B913300" TYPE="ntfs" 
/dev/sdc5: TYPE="swap" UUID="9fefaa5e-e25e-48c9-9cbc-a4b9b1a5f49e" 

And just to mention, I have a program called paragon partitioner and it has a featuer to look for OSs and with it I can load the windows OS

---

### Post by Legace on 2009-05-16
Try this then:
```

title Windows XP Professional x64 Edition
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

(you had hd2 hd0, i just changed it the otherway round)

---

### Post by pluMmet on 2009-05-16
That worked!!! A thousand thanks. 

It seems that the Ubuntu install was the one who switched it around.. Maybe I did it when trying to fix it?

Have a Great day
[IMG]http://www.kangaruni.com/files/u9/happy_living.jpg[/IMG]

---

### Post by Legace on 2009-05-16
Glad I could be of assistance :)
Enjoy.

---

### Post by pluMmet on 2009-05-17
I woke up this morning and it doesn't work again ](*,)

It's ERROR:22 No such partition (again.)

---

### Post by pluMmet on 2009-05-17
It's working speratically...

One time out of 6 so far and not the seventh...

---

### Post by pluMmet on 2009-05-17
I'm up to about 20 tries...it only worked once.

It worked over and over yesterday once it started working that is.

---

### Post by pluMmet on 2009-05-17
Bump

---

### Post by Legace on 2009-05-17
How many harddrives do you have installed on your machine?
And please post the content of /boot/grub/menu.lst

---

### Post by pluMmet on 2009-05-17
Thanks again for trying to help :D

```
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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66c2bf84-4e90-4c91-8b39-e48099d7065b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=66c2bf84-4e90-4c91-8b39-e48099d7065b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		66c2bf84-4e90-4c91-8b39-e48099d7065b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
rootnoverify	(hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader	+1

```

It should be the exact same as last time but with the changes you gave me last night...

Ohhh and I have 3 HD but the second is not formatted right now.

---

### Post by pluMmet on 2009-05-17
bump

---

### Post by pluMmet on 2009-05-18
Hello out there ):P

Can anyone help?

---

### Post by pluMmet on 2009-05-18
Help :confused:

---

### Post by pluMmet on 2009-05-19
No one has any suggestions at all?

---

### Post by pluMmet on 2009-05-25
I figured out the bug... I must load Ubuntu first then I can restart then load my windows partition. From there I can restart all I want (from windows or Ubuntu) and the windows partition will load.

But when I fully shut down my system I can't start up and go directly to my windows partition.

I've reported this this bug!

---

### Post by pluMmet on 2009-05-25
I've just discovered it's even odder then that. The work around I listed only 'works' when my printer is on. I have a cannon mp390.

This is too too odd....

---

### Post by pluMmet on 2009-05-25
Last piece of the puzzle... My printer has a 1GB sd card plugged into it. When I remove the card The work around does not work.

Side note: It acts as a usb drive. I have never installed Ubuntu live on it or any other OS for that matter.

---

### Post by pluMmet on 2009-05-25
I looked and I have no Linux files on the SD card.

I can deal with it now that I know but it is a pain...

**[SIZE="5"]Does anyone have any idea what is going on?[/SIZE]**

---

### Post by VMC on 2009-05-25
Lets start over. Unplug your printer. Get a copy of Super Grub Disk. When it boots up, immideatly push 'c' key. You should have the "grub>" prompt.

Then type the following:

```
find /boot/grub/stage1
```

Lets find out what grub finds that way.

---

### Post by Brandon Williams on 2009-05-25
It sounds like your printer is being recognized as a hard-drive, but only after you boot into linux, and that the windows setup in grub is only correct when the printer it being seen as a hard drive. This makes me wonder whether the printer becomes /dev/sdb when it's plugged in, pushing the windows drive to /dev/sdc, but that when the printer isn't plugged in, the windows drive is /dev/sdb.

What happens if you specify (hd1,0) as the root for the windows boot? 
```
Windows on /dev/sdb
root (hd1,0)
chainloader +1
```
Will windows cold boot without having started linux first? And what about when the printer is not attached?

If this works, then you could add two entries to grub, one for when the printer is recognized as a drive and one for when it isn't.

---

