---
title: "[SOLVED] External Hard Disk Problem"
date: 2008-12-12
forum: General Help
---

### Post by Nirva on 2008-12-12
Hi,

last week, I tried installing openSUSE on my external hard disk.
But it turned out quite bad.
I can't boot from my external hard disk into my new openSUSE installation, but even worse : I can't mount my Ext Hard Disk in any os anymore :s

I think there is a problem with my MBR.
Does anyone has a solution ?

Thanks in advance.

---

### Post by az on 2008-12-12
> **Nirva said:**
> Hi,

last week, I tried installing openSUSE on my external hard disk.
But it turned out quite bad.
I can't boot from my external hard disk into my new openSUSE installation, but even worse : I can't mount my Ext Hard Disk in any os anymore :s

I think there is a problem with my MBR.
Does anyone has a solution ?

Thanks in advance.

Install gparted if you don't already have it.  Plug in the drive and then run Gparted.  Does the partition table look intact?

When you say it doesn't boot, do you mean no disk is detected or it tries to boot and fails?  In the latter case, you can try fixing the /boot/grub/menu.lst to point to the proper partition.  Does your computer support booting from an external USB drive?  


If you want to erase the external drive, use Gparted to delete the existing partitions on it and start over with an empty partition of your choice (ext3, ntfs, fat32, etc...)

---

### Post by Nirva on 2008-12-12
When I run gparted, he tells me that the full size of the disk is unallocated.  

Is it possible to repair this ?  I hope the data is still on my disk, but isnt recognized because something I did with the MBR.  
It is possible that I copied the MBR of an OSX installation to the MBR.  Something with EFI ?  I don't know much about this stuff.

Sorry about my lack of knowledge on this matter :-)

---

### Post by Graf555 on 2008-12-12
Nirva, Try to find gpart (not "GParted"!) As I know, it's not in repositaries;)

---

### Post by az on 2008-12-12
> **Nirva said:**
> When I run gparted, he tells me that the full size of the disk is unallocated.  

Is it possible to repair this ?  I hope the data is still on my disk, but isnt recognized because something I did with the MBR.  
It is possible that I copied the MBR of an OSX installation to the MBR.  Something with EFI ?  I don't know much about this stuff.

Sorry about my lack of knowledge on this matter :-)

Testdisk recovers lost partitions.  Install testdisk and run it.

sudo testdisk

You may need to enlarge your terminal window on your desktop.  Use the menus to pick the external drive and let it try to recover any lost partitions.  Make it add them back to the partition table.

---

### Post by Nirva on 2008-12-12
gpart did the trick.  Thank you very much

---

### Post by Nirva on 2008-12-12
Hi,

I'm trying to install linux on my external hard disk.
The installation went fine, I can boot from my Ext HD, grub comes in.  But when I select my linux partition I get error 17 : cannot mount selected partition.

This is my menu.lst

```
# Modified by YaST2. Last modification on Tue Dec  2 11:31:46 CET 2008
default 0
timeout 8
gfxmenu (hd1,2)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3 splash=silent showopts vga=0x314
    initrd /boot/initrd-2.6.25.5-1.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x314
    initrd /boot/initrd-2.6.25.5-1.1-default
```

This is the response on fdisk -l /dev/sdb

```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c2dbcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37859   304094385    c  W95 FAT32 (LBA)
/dev/sdb2           37860       44387    52436160   83  Linux

```

And this is an error I get in the grub-prompt.

```

grub> root (hd1)

grub> setup (hd1)

Error 17: Cannot mount selected partition


```

Does anyone has an idea  ?
Thanks in advance.

---

### Post by Nirva on 2008-12-12
Hi,

I'm trying to install linux on my external hard disk.
The installation went fine, I can boot from my Ext HD, grub comes in.  But when I select my linux partition I get error 17 : cannot mount selected partition.

This is my menu.lst

```
# Modified by YaST2. Last modification on Tue Dec  2 11:31:46 CET 2008
default 0
timeout 8
gfxmenu (hd1,2)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3 splash=silent showopts vga=0x314
    initrd /boot/initrd-2.6.25.5-1.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x314
    initrd /boot/initrd-2.6.25.5-1.1-default
```

This is the response on fdisk -l /dev/sdb

```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c2dbcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37859   304094385    c  W95 FAT32 (LBA)
/dev/sdb2           37860       44387    52436160   83  Linux

```

And this is an error I get in the grub-prompt.

```

grub> geometry (hd1)
drive 0x81: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sdb
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83

grub> root (hd1)

grub> setup (hd1)

Error 17: Cannot mount selected partition


```

Does anyone has an idea  ?
Thanks in advance.

---

### Post by adult swim on 2008-12-12
you didnt specify a partition at your grub prompt, it should be root (hd1,1)

---

### Post by caljohnsmith on 2008-12-12
If you are booting the sdb drive on start up, then your OpenSUSE entries in the menu.lst should use (hd0,1) instead of (hd1,1). That's because whichever drive you boot on start up is (hd0), so if you boot sdb, then sdb is (hd0). How about trying that and let me know how it goes.

---

### Post by Nirva on 2008-12-13
Thanks, that worked fine, but now I have another error :-)

While booting he tells me that he is unable to find :

/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3

so he suggests to switch to /dev/sdb3.  But that one isn't found either.

So I changed my menu.lst en replaced root=/dev/disk/by-id/usb-ST350082_0AS_50DBE8888888-0:0-part3 with root=UUID=X
With X = the correct ID of my partition.

But this results in :

cant find /dev/root while booting
Any ideas ?

---

### Post by caljohnsmith on 2008-12-13
I would try replacing the root line with:
```
kernel /boot/vmlinuz-2.6.25.5-1.1-default [COLOR="Blue"]root=/dev/sdb2[/COLOR] splash=silent showopts vga=0x314
```
But you also will need to modify Grub's "device.map" file, so you would do:
```
sudo mount /dev/sdb2 /mnt
gksudo gedit /mnt/boot/grub/device.map
```
And change your device.map to be:
```
(hd0)	/dev/sdb
(hd1)	/dev/sda
```
So you need to map (hd0) to sdb since you are booting sdb on start up. Anyway, how about giving the above steps a shot and let me know what happens.

---

### Post by Nirva on 2008-12-13
Thanks for your help, but still the same error :

could not find /dev/sdb2

---

### Post by Nirva on 2008-12-15
I solved it !
I had to change /dev/sdb2 into /dev/sda2 because I was booting from my exteral hard disk so it became /dev/sda

Thanks to everyone who helped me out.

---

