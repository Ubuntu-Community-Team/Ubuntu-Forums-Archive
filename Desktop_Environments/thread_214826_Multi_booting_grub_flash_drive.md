---
title: "Multi booting grub flash drive"
date: 2006-07-13
forum: Desktop Environments
---

### Post by paridoth on 2006-07-13
I am attempting to create a usb flash drive which contains grub, that will be able to boot multiple OS’s either on a connected machine, within its hard rives, and inside partitions in the usb flash drive itself.

I first googled for guides in order to learn the basics of grub, as I myself am fairly new to the Linux world myself. I found this guide [http://www.knoppix.net/wiki/USB_Based_FAQ]("http://www.knoppix.net/wiki/USB_Based_FAQ") to boot Knoppix and figured I could use part of it in order to install a basic grub system, one which I could later edit to include a menu for the OS’s on the flash drive, and use the command line to boot other OS’s for the computer its plugged into. Granted what I wanted to do is different from the guide, I figured I could replace those parts in the guide that where different with what I wanted to do. However my end result was nonfunctional, which I'm sure is attributed to my lack of knowledge to exactly how grub does what it does. So I will write bellow what I attempted to do, and how I thought that would work, and you can reply as to why that was incorrect so that I can get this working.

Ok, so I am running on Ubuntu dapper, and I have a 512 MB usb flash drive. I have formated it using gparted with a single 7.81 (smallest it would go) partition formated in EXT3. Here I plan to keep only grub, I plan later to create more partitions, where I will install small Linux OS’s and a live windows XP OS. But for now this is all that is on the drive.

The guide directed me to copy all of my grub files to my flash drive, which is mounted to /media/usbdisk and is /dev/sdd1 however I decided not to include the menu.lst file, as its entry's would be irrelevant, and I plan to create one later with relevant entry's, and will not need one until then.

It then tells me “To install the stage1 boot loader to the drives master boot record (MBR), edit the device.map file to tell grub-install that /dev/sda1 is a bios drive:” and gives me the following code
```
# echo ‘(hd0) /dev/sda’ > /mnt/boot/grub/device.map
``` I rearrange this code to the following to make it work for me ```
# echo ‘(hd0) /dev/sdd’ > /media/usbdisk/device.map
``` which then replaces the previous contents of the file to the following ```
(hd0) /dev/sdd
```
now what I'm guessing this all means is that when I run grub-install it will read the device map and recognize, that, what my Linux sees as sdd is where it is to install itself to.

So continuing, it tells me to run the grub-install with the following code ```
# grub-install --root-directory=/mnt --no-floppy ‘(hd0)’
``` which I change to the following
```
# grub-install –root-directory=/media/usbdisk --no-floppy ‘(hd0)’
```

everything goes fine and I get no errors just something mentioning something about freeze and xfs that assured me it wouldn't matter. However when I look at the flash drives contents I see that it has created a boot/grub folder with grub files in it, and that the device.map’s contents are
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

I attempted to test it by plugging the flash drive into my laptop which supports booting from a flash drive, and only get a blank black screen with a blinking _

so what am I doing wrong here? Is there a different guide I should follow? Is what I'm going not possible? Thank you for any help and if you need any more info don't hesitate to ask.

---

