---
title: "&quot;Read-only file system&quot;"
date: 2009-02-25
forum: General Help
---

### Post by KilledXDestiny on 2009-02-25
Hey I have a couple of USB drives that I've been trying to use (two of the same model/size. SanDisk Cruzer Micro 2GB) but whenever I attempt to put files in them I get an error because they are apparently a "Read-only file system"

Is there any way to work around this or should I simply avoid that model in the future?

Thanks

---

### Post by mb_webguy on 2009-02-25
It could just be that those drives are mounting as read-only for some reason.  Could you plug one in and run the command "sudo fdisk -l"?

(Btw, if you're typing that rather than copying it, that's a letter "l", not the number "1".)

---

### Post by KilledXDestiny on 2009-02-25
Ok, I get the follow:

[B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x193a43e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002255360 bytes
4 heads, 16 sectors/track, 61103 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       61104     1955319+   e  W95 FAT16 (LBA)
[/B]

---

### Post by mb_webguy on 2009-02-25
Ok, it looks like the USB drive is being detected by the system, it's just not being mounted for some reason.

You can do this manually with the following commands.```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```
Maybe someone else can help you figure out why it's not being automatically mounted.

---

