---
title: "How to boot Ubuntu from USB disc?"
date: 2009-05-13
forum: General Help
---

### Post by rkj951 on 2009-05-13
I installed Ubuntu on an extrnal USB disc on a computer in my old office. Now have no access to this computer. On that computer I was able to boot Ubuntu from this USB disc but my computer at home does not have option to boot ftom USB Disc. How can I boot Ubuntu from this disc now? I read some where that possibly Live CD can be used to boot from USB disc. But detail information was not available. I do not want to change anything on my local hard disc (Windows XP) & so do not want to install GRUB/Lilo etc. Can booting from USB disc be done without installing GRUB/Lilo?

---

### Post by dragonbeast25 on 2009-05-13
Easy enough i made a tutorial how to boot via live cd , through USB

[http://www.youtube.com/watch?v=nMXCqC4ZziA]("http://www.youtube.com/watch?v=nMXCqC4ZziA")

---

### Post by dragonbeast25 on 2009-05-13
never mind i reread it, i dont no

---

### Post by abhilashm86 on 2009-05-13
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/]("to install ubuntu on linux")

in this method you can save back changes to USB.

---

### Post by JK3mp on 2009-05-13
Ubuntu comes with a built in installer on live cd. Just stiick the live cd in and boot from it, then System >Utilities> and then there should be some option to creat bootable usb drive. Make sure you format the drive for it first, FAT32 prefferably, not sure entirely abou the System > Utilities thing, i don't use ubuntu nor gnome (ArchLinux w/ Openbox)

---

### Post by abhilashm86 on 2009-05-13
well you can use gparted to make boot set from USB, make sure you do 
boot flag= checkmark, so you can boot it,
from terminal,
```
sudo gparted
```
then to select USB,
Gparted-> Devices -> select device

---

### Post by michy99 on 2009-05-13
You can make a boot CD which will load from the USB drive. I've never done it, but I found this topic

[http://ubuntuforums.org/showthread.php?t=266068](http://ubuntuforums.org/showthread.php?t=266068)

It's a little old, but should probably work.

Actually, this is probably better:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

