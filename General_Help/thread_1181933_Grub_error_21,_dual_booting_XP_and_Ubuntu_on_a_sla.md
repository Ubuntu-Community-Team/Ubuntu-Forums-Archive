---
title: "Grub error 21, dual booting XP and Ubuntu on a slave"
date: 2009-06-08
forum: General Help
---

### Post by cloudfrog on 2009-06-08
Hey everyone!

Just got finished installing Ubuntu on an external usb drive (sdb I believe) with XP running on the primary drive(sda), and I've run into an issue with Grub.  If I boot my computer up with the external drive plugged in and set up as highest priority in the boot menu, it loads fine.  However, if the external is unplugged and I try and boot into XP, I get a Grub Error 21.

I checked around the forums and found a few solutions, but the links to where the directions for taking care of an issue like this were broken.  Any helpful advice or information would be GREATLY appreciated!

---

### Post by cloudfrog on 2009-06-08
Also, I copied the following information from fdisk in terminal:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19f619f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris
```

---

### Post by cloudfrog on 2009-06-08
I'm still having continued issues with this.  I've additionally since tried changing my external drive to Auto in Bios, as this resolved many people's problems, but I'm afraid it's still not working.  I would appreciate any input at all on this.

Thanks!

---

### Post by bumanie on 2009-06-08
You will have to rewrite the mbr to the windows drive without the external hard drive plugged in. To do this use the windows installation disk in console mode and type FIXMBR. Windows should now boot. Unplug your windows drive from the motherboard. Then boot a live ubuntu cd and then plug the external hard drive in. Go to terminal > sudo grub > root (hd0,0) > setup (hd0)>  quitAs long as your bios can be set to boot from usb-hdd, whenever the external hard drive is plugged in at boot, ubuntu should load.

---

### Post by boof1988 on 2009-06-08
Another option would be to use the [Super GrUB Disk](http://www.supergrubdisk.org/) as follows...

[LIST=1]
[*]Download the CD iso from [Super GrUB Disk's CD download page](http://www.supergrubdisk.org/index.php?pid=5).
[*]Burn the iso-image to a CD.
[*]Make sure the external USB drive is not connected to the computer.
[*]Boot the computer to the Super GrUB Disk.
[*]Find (and then choose) the fix windows boot option.
[*]Let the SGD (Super GrUB Disk) work it's magic.
[/LIST]

---

### Post by name123 on 2009-06-09
> **cloudfrog said:**
> Hey everyone!

Just got finished installing Ubuntu on an external usb drive (sdb I believe) with XP running on ...

Now my problem is a bit different. I instaled ubuntu 8.04 on a 80GB internal HDD (ata). The installation was with "Manual: Use entire disk". 
After the installation, at first reboot: <bum> Eror grub stage 1.5, please wait error 21.

Any idea?  Thanks!

---

