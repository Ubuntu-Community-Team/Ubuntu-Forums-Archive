---
title: "Added HD, messed up Grub"
date: 2006-04-18
forum: Desktop Environments
---

### Post by dawhoo on 2006-04-18
I put in another HDD and now, although nothing else cahnged, I can no longer boot to windows from Grub.

I have an odd setup.  

Windows is installed on sda with the original windows MBR completely intact. Kubu is installed on hda and has grub written to its MBR. I did this, in case I had to boot to windows, I can change the boot disk order in BIOS and boot to windows without having to worry about Grub.

I can still boot to windows IF I change the boot disk order, but that's really a pain. The Grub interface worked perfectly until I installed another HDD (hdb).  

If anyone has a suggestion, I'm open.

menu.list
```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

device.map
```
(hd0)	/dev/hda
(hd1)	/dev/sda
```

Seems to me, device.map should have another entry for my new HDD, I can access it and store files there. SHould I manually edit it and if so, what should I do?

fdisk -l
```
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1305    10482381    c  W95 FAT32 (LBA)
/dev/hda2   *        1306        4717    27406890   83  Linux
/dev/hda3            4718        4866     1196842+   5  Extended
/dev/hda5            4718        4866     1196811   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2611    20972826    c  W95 FAT32 (LBA)
/dev/hdb2            2612        4867    18121320    c  W95 FAT32 (LBA)

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2603    20908566    7  HPFS/NTFS
/dev/sda2            2604       10011    59504760    7  HPFS/NTFS

```

I sure would like to resolve this issue. Any suggestions?

---

### Post by Storm Rider on 2006-04-19
Is Windows on the Master Drive.  I think it needs to be on partition 1 of the first hard drive (hd0) to boot.  

Perhaps if you set the sda to master and the hda to slave then reinstalled Grub...

I'm a rookie but it's an idea.

---

### Post by dawhoo on 2006-04-19
hda is the IDE master
hdb is the IDE slave

sda is the SATA master

---

### Post by Hiew on 2006-04-19
Have you tried reinstalling Grub?

I find the Lest painfull way of doing so would be to just boot up with the ubuntu disc in, and run the install until you get to the partition section. Once there press Esc and choose install grub it will complain a bit saying it can't install unless its a clean and formatted disk, just exit and reboot andt it should work. I've done this a couple times from installing Windows AFTER installing Linux and it seems to work quite easily.

---

### Post by dawhoo on 2006-04-19
No, I haven't reinstalled Grub. I thought it might be something I could do with just editing files.  I'll give it a try though. Thanks for the method :D

---

### Post by dawhoo on 2006-04-19
installing grub thaat way did not work for me, when I tried to install Grub, it would take me right back to wanting to set up partitions - 6 times in a row.

---

### Post by pranav on 2006-04-19
[QUOTE=dawhoo]installing grub thaat way did not work for me, when I tried to install Grub, it would take me right back to wanting to set up partitions - 6 times in a row.[/QUOTE]

Hi, I have faced a similar situation.

When you reach the partitioner.. 
1) the swap partition will be chosen for formatting by default (skull symbol)
2) now choose the partition where ubuntu is already installed
3) go into the ubuntu partition and change the mount point to "/" only and also choose "keep existing data, do not format" THIS IS VERY IMPORTANT.
4) now choose done setting up the partions & go ahead.
5) the error messages will be displayed but now you can go ahead and install GRUB again. 
 


[http://ubuntuforums.org/showthread.php?t=126585]("http://ubuntuforums.org/showthread.php?t=126585")

This is the link.

---

### Post by pranav on 2006-04-19
[QUOTE=dawhoo]No, I haven't reinstalled Grub. I thought it might be something I could do with just editing files. [/QUOTE]

Try changing the map ... and show grub exactly where the Win partition is.

I am not certain about what commands, but logically speaking, in the menu.lst you just have to tell grub where windows is installed. 

If you are really in a hurry and/or menu.lst is greek and hebrew then reinstall grub.

But if you  are keen on GNU/Linux then this is the time to learn a couple of GRUB commands that will come in handy. In fact even i want to know the commands as the situation you are facing is likely to arise once i add a HD.

---

