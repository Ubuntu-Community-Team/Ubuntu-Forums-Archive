---
title: "Need Assitence with grub"
date: 2006-09-03
forum: Desktop Environments
---

### Post by amunimanghi on 2006-09-03
Hi,

Earlier today, I installed Windows 2000 on my second hard drive.
A little later, I installed Ubuntu on my first hard drive. Everything installed correctly. I just don't know how to boot into windows. When I go to grub, it doesnt show Windows. All it shows is Linux(kernal number), linux (kernal number) recovery, and memtest. I read around a little and found out that you have to add a windows section to your /boot/grub/menu.lst

Can anyone help me do this with the way my computer is set-up. I would post my fdisk -l, but I can't access the internet on my computer. I need the download the drivers for it. Thats why I would like to boot into Windows. Thanks  :grin:

---

### Post by anaconda on 2006-09-03
If your windows is on a secondary hard-disk then you want to add these lines to the end of your /boot/grub/menu.lst  -file

title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader	+1

And if your windows is on the main hard-disk then add these lines: 

title		Windows NT/2000/XP 
rootnoverify (hd0,0)
makeactive
chainloader	+1

Actually you can add both of these and try booting with both of them.. and later delete the one, which didn't work...

And to edit your menu.lst -file you need root rights. To get them just open terminal and type:
sudo nano /boot/grub/menu.lst
then do the changes you want and exit with "Ctrl-x" and answer yes to "do you want to save"...

oh. and the important part is the (hd0,0) first 0 means the first hd and the second 0 means first partition. (hd1,1) would mean second hd and second partition. Windows likes to think that it is on the first hd.. that is why the remapping is needed in the first example.. (to make windows think it is in the first hd..) 

Here I assumed your windows is on the first partition of your windows hard-disk.. if it isn't then just change the number of partition to match your windows partition..

---

### Post by anaconda on 2006-09-03
Usually the windows entry is added automatically by the ubuntu-installer. Wonder why it didn't work with you..

---

### Post by amunimanghi on 2006-09-03
Sadly it didn't work. Here is my /boot/grub/menu.lst ```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot


title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

title Windows NT/2000/XP
rootnoverify (hd0,0)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```
and here this is the output of ```
fdisk -l
``` ```
ameen@manghi:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9732    78172258+   7  HPFS/NTFS

```

Hope this helps.

---

### Post by Ramses de Norre on 2006-09-03
Why don't you swap your two disks and install grub from the first? Ubuntu will boot fine from both (when you just install grub again) and windows will boot easier from the first..
It should be automatically found then which isn't the case now it seems..

---

### Post by bulldog on 2006-09-03
Have you the possibility to push F11 or something like that at startup,so you get a menu where you can choose which device should be used to boot?

Your CD or floppy or even a choice between multiple hdd's.

If so use that to change which hdd you will use to boot.

I do this a long time and a reinstall of Windows or even Ubuntu has no effect on the other OS.

I have set my Ubuntu hdd as default bootdevice in my BIOS,because this is the one I use the most.
But when I want to play a game I restart the computer and push F11 after memory counting and choose to start from the other hdd.
Works for me anyway.

---

### Post by Ramses de Norre on 2006-09-03
That's even better than physically swapping the drives =)

---

### Post by amunimanghi on 2006-09-03
ok, I'll try that out.

EDIT: When I boot it up with the second hard drive, it said that **ntdlr** was missing. Does anyone know how to fix this? Thanks

---

### Post by amunimanghi on 2006-09-03
Ok, I did a little research and I found out how to fix this problem. I did mine this way and it does work. Just be sure to read it before you do anything. 
Heres the link:
[http://support.microsoft.com/kb/318728/]("http://support.microsoft.com/kb/318728/")

---

