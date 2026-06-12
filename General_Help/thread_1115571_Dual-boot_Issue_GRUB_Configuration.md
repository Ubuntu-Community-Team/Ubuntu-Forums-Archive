---
title: "Dual-boot Issue: GRUB Configuration"
date: 2009-04-04
forum: General Help
---

### Post by Kaidona on 2009-04-04
I am rather new to Ubuntu; after spending multiple months fighting with Windows, I made a complete switch to Linux, and have been familiarizing myself with it over the past few weeks. Much to my misfortune, I found out later that I would still need to use Windows for a minor few things, and set about dual-booting.

I'm using Windows 2000. I installed it to my secondary harddrive, and followed what directions I could find to set up GRUB to boot it, and I seem to have either made a mistake somewhere, or missed something entirely, because when I select the Win2000 option in my bootloader, it returns GRUB error 8, that no kernel has been loaded. I've tried to research my situation, and haven't been having much luck in finding anything, so...

Help? I would love you all to death.

---

### Post by easybake on 2009-04-04
Could you post the output of ```
fdisk -l
```

and also post your /boot/grub/menu.lst

---

### Post by Kaidona on 2009-04-04
Well, this is slightly unsettling. This is the first time I've ever gotten this result:
```
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

```
And I'm pretty certain I had taken a look after trying to get my dual-booting set up...wait, usually I do it using sudo. Hmh. Should I post the result of the fdisk command with sudo?

And here is my menu.lst:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8f10eb04-1200-48ce-bac9-d55e099b101f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8f10eb04-1200-48ce-bac9-d55e099b101f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8f10eb04-1200-48ce-bac9-d55e099b101f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8f10eb04-1200-48ce-bac9-d55e099b101f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8f10eb04-1200-48ce-bac9-d55e099b101f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f10eb04-1200-48ce-bac9-d55e099b101f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8f10eb04-1200-48ce-bac9-d55e099b101f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f10eb04-1200-48ce-bac9-d55e099b101f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8f10eb04-1200-48ce-bac9-d55e099b101f
kernel		/boot/memtest86+.bin
quiet

title Microsoft Windows 2000
rootnoverify (hd1,0)
makeactive
chainloader +1
```

---

### Post by wanderingarticfox on 2009-04-04
Sorry I'm new to Ubuntu so I'll defer to others on that; however if you are using W2000 you really should think of upgrading. You can get XP Pro OEM w/SP3 for under $140 everywhere. Then if it is on a separrate drive well all I can sugest is a POST select for the drive at start-up. I have been told it is better to put the windows on first then instal Ubuntu that way GRUB set up choices are made and the windows MBR does not fight with the Linux. I'm sure someone will correct me if I'm wrong. Just trying to help.
I think the dual boot is best if on the same drive.

---

### Post by Melk79 on 2009-04-04
Do you have a SuperGrub disk? [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

This thing works miracles, check out their site.  I don't know how many times I've popped this thing in and come out clean.  No jokes, it's late.

---

### Post by easybake on 2009-04-04
> **Kaidona said:**
> Well, this is slightly unsettling. This is the first time I've ever gotten this result:
```
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

```
And I'm pretty certain I had taken a look after trying to get my dual-booting set up...wait, usually I do it using sudo. Hmh. Should I post the result of the fdisk command with sudo?

Yes, my fault run 
```
sudo fdisk -l
```

---

### Post by Kaidona on 2009-04-04
Okay, then. *chuckle* Here it is:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa32aa32a                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1023     8217216   83  Linux 
/dev/sda2            1024       14593   109001025    f  W95 Ext'd (LBA)
/dev/sda5            9825       14593    38306992+  83  Linux          
/dev/sda6            1024        5356    34804759+  83  Linux          
/dev/sda7            5357        9824    35889178+  83  Linux          

Partition table entries are not in disk order

Disk /dev/sdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41464145                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         765     6144831    b  W95 FAT32
/dev/sdb2             766        2480    13775737+   5  Extended 
/dev/sdb5            2168        2480     2514141   82  Linux swap / Solaris
/dev/sdb6             766        2167    11261502    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdc: 255 MB, 255852544 bytes
16 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x7068ad9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         976      249840    b  W95 FAT32

```

---

### Post by Kaidona on 2009-04-05
Not particularly fond of double-posting, but since it's been over a week since I started trying to set myself up to dual-boot, here I go.

---

### Post by easybake on 2009-04-05
> **Kaidona said:**
> Not particularly fond of double-posting, but since it's been over a week since I started trying to set myself up to dual-boot, here I go.

Sorry for the delayed response. Your partitions appear to be set right. In my boot menu I have this for all of my windows partitions```
title		Windows 7 Ultimate
root		(hd1,0)
savedefault
chainloader	+1
makeactive
```

See if using root rather than rootnoverify works. 

I have had issues with a mix up of the hd#'s before. You could also try ```
title		Windows 7 Ultimate
root		(hd**2**,0)
savedefault
chainloader	+1
makeactive
```

---

### Post by Kaidona on 2009-04-05
Changing "rootnoverify" to "root" returns GRUB error 8 still. Changing the listed harddrive from "1,0" to "2,0" returns an error that the selected disk does not exist. I recall what few instructions I did find saying to add a line to my device.map, but I did nothing to that file, since the line I would have been adding already existed.

EDIT: Now that I think about it, I feel I should also be asking if selecting Win2000 in the GRUB menu is supposed to send me to a command prompt.

---

### Post by meierfra. on 2009-04-06
Add these three items to menu.lst


title Microsoft Windows 2000  (hd0)
rootnoverify (hd0,0) 
chainloader +1

title Microsoft Windows 2000  (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Microsoft Windows 2000  (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


If one of them works, you can deleted the others from menu.lst


**If none of them worked:**

Report all error messages you got and download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags). The results of that script will help clarify your setup.

---

### Post by Kaidona on 2009-04-06
Ahhah! I needed the map lines! The second one worked. Thank you very much, and thank you to everyone else for your efforts. Now to go clean up my clumsy mess. XD;

---

### Post by meierfra. on 2009-04-06
> The second one worked. 
Great. Have fun W2000  and Ubuntu.

---

