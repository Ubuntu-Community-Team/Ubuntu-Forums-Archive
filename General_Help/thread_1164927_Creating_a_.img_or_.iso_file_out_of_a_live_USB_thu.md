---
title: "Creating a .img or .iso file out of a live USB thumbdrive?"
date: 2009-05-20
forum: General Help
---

### Post by cpeee on 2009-05-20
I've googled around but could not find a tool to help me create a .img or .iso file out of a USB thumdrive. The USB thumbdrive is running a livecd version on persistent mode which I create using usb-creator. I've customized the livecd by removing some packages and adding some. And I hope to create a .img/.iso image from the USB thumdrive so I could pass the file over to a friend via the network instead of physically shipping the USB thumdrive across. Any clue on how could I achieve my goal? The closest tool I've found is winimage (which runs on windows but I don't use windows). 

Thanks.

---

### Post by Joeb454 on 2009-05-20
Thread moved to General Help :)

---

### Post by Brandon Williams on 2009-05-20
With the thumb-drive inserted, first determine what the device file is. On my machine, if I insert one usb drive, it will be /dev/sdb. The first partition on the drive will be /dev/sdb1.

If you want to copy the whole thumb-drive to an image file: 'sudo dd if=/dev/sdb of=usbdrive.img' will copy the entire thing to the file usbdrive.img in the current directory. If you just want to copy the first partition: 'sudo dd if=/dev/sdb1 of=usbpartition.img'.

Before making the image, I suggest that you do this inside of a directory on the thumb drive: 'dd if=/dev/zero of=discardme.img'. The command will eventually fail, telling you that there is no space left on the disk. When that happens: 'rm discardme.img'. This will have zeroed out all the unused space in the partition to make for more effective compression of the final .img file. Repeat this for each partition on the drive if you are imaging the whole drive and it has multiple partitions.

Your friend can just use: 'sudo dd if=usbdrive.img of=/dev/sdb' to restore the image to a usb drive, once-again replacing /dev/sdb with the correct device name.

---

### Post by Cheesemill on 2009-05-20
Check out [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html").

Cheesemill

---

