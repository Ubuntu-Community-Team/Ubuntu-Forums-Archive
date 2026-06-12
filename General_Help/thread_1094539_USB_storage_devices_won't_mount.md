---
title: "USB storage devices won't mount"
date: 2009-03-12
forum: General Help
---

### Post by Orionriver on 2009-03-12
When I plug in a USB storage device, it will not automount. lsusb says that I have nothing plugged in. I am a serious Linux noob, so that is about as far as my expertise can take me. I am running Ubuntu 8.04 on a T41 laptop, and have verified that both the USB ports and storage device work. (By using peripherals/trying it on another computer)

---

### Post by mb_webguy on 2009-03-12
Plug in the USB device, then enter the command "sudo fdisk -l".  If you see an entry corresponding to the USB drive, you can mount it manually with "sudo mkdir /media/usb; sudo mount /dev/*xxxn* /media/usb" where *xxxn* is the device associated with the USB drive.

---

### Post by Orionriver on 2009-03-12
This is my output from fdisk -l. The 60 gig is my laptop hard drive, so it doesn't look like it can see the external. 

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc72dc72d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

---

### Post by pavmav on 2009-03-26
Ok here is my problem. I have a USB  stick that does not mount. But my problem is a bit different - the USB was formated (or maybe something like that) ; Ubuntu and Windows does not recognize it anymore. When i click properties on the USB drive (i can click only that.) on all the places there is "unknown"  as if its just something plugged in. I have tried to low format .... and that was not very smart ... how do you low format something that you don't recognize (see) first. I really need some help here .

---

### Post by coffeecat on 2009-03-26
**pavmav**, install Gparted from the repository. You can do that from Synaptic. Plug the USB flash drive in and start up Gparted (System > Adminstration > Partition Editor). Click on the little device chooser at top right and choose your USB drive. Make sure you get the right one - you don't want to be reformatting any partitions on your main hard drive. :wink:

Gparted is fairly easy to use. Post back if you need any help. Just remember to click on  'Apply' for any reformatting to be done. USB flash drives are usually formatted FAT16. You can choose another filesystem if you want, but you don't want a journalled one on a flash drive and FAT16 is a MS filesystem, so your Windows machine will be able to recognise it.

---

