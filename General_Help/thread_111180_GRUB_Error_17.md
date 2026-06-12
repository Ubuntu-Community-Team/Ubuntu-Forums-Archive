---
title: "GRUB Error 17"
date: 2006-01-01
forum: General Help
---

### Post by Mazin on 2006-01-01
GRUB Stage 1.5 is giving me Error 17 when I start my computer, so I can't boot into any OSes.

I think it may be related to me messing around with my partitions, so I edited the menu.lst file

My menu.lst:

```
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

...left out the recovery mode one

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

...left out the windows one
```

_And my partitions_ (as reported by GParted)

hda1:Windows NTFS
**hdb1:Linux Ext3**
hdb3:Shared FAT32
hdb2:Extended
  -   hdb5:Linux-swap

Did I have it pointed at the wrong one or something?

Excerpt from GRUB Legacy Manual:

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by Sef on 2006-01-04
Gentoo has this fix for a GRUB 17 error:

> 5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Be sure to check your root(x,y) settings in your grub.conf. 

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

---

### Post by mezhaka on 2006-01-07
i am absolutely new to linux, so it's really hard to understand what is written above... so here is my story for newbies.
yesterday my computer rebooted on logon screen, so now i get the same error and have absoulutely no idea how to fix it. i have booted from live cd and ran System->Administrative tools->Disks to determine the name of my linux hard drive which was /dev/hdd it was written that the disk is unformatted. than i did ```
sudo fsck /dev/hdd
``` which made me pushing the 'y' button for apr. 15 minutes. i tried to do ```
sudo fsck -p /dev/hdd
```  to make file system check to work in silent mode, but it said that i have to do it manually. than i rebooted and rejoiced to see that GRUB (btw i don't know what is that) has loaded so i could choose between my windowsXP or ubuntu. choosing ubuntu pushed me in some sort of safe mode with a terminal running, so i just reinstalled the whole OS. i did not have any valuable information on ubuntu hdd. i am not aware of the reason of that accident. it might be problems with hdd... i would REALLY apriciate any comments on my actions, cause i feel there was a way to reanimate my ubuntu without reinstalling.

---

