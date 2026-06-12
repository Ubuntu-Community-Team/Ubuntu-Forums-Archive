---
title: "Trying to go back to Windows, error on boot"
date: 2009-05-02
forum: General Help
---

### Post by Sims12345 on 2009-05-02
Hi,

I have been using Ubuntu for about 6 months now, and as great as it was,  I would like to go back to XP. 

Here is the problem...I have an Acer Aspire One, with a live USB stick with XP on it, and everytime I insert it, I get 'Remove disks or other media. Press any key to restart' :confused:

How do I install XP?

Thanks

---

### Post by delcypher on 2009-05-02
[This will tell you the basics of installing XP onto a system with Ubuntu installed]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

How did you make your bootable USB winXP install stick because it sounds like you didn't do it right (your netbook doesn't think it's bootable)? Also check your netbook's bios is correctly configure to boot from a USB device.

You can make a working bootable Windows XP install USB stick using [UNETBOOTIN (for linux or Windows)]("http://unetbootin.sourceforge.net/") and an .iso image of the WINDOWS XP INSTALL CD.

when you use UNETBOOTIN on the usb stick make sure you get the device name correct, e.g. /dev/sdb1  . To find out the device name use ```
mount
``` and match the device name with the correct folder in /media/ . You could also use ```
sudo fdisk -l 
```

If you have the windows xp setup CD in your drive in Ubuntu you can make an iso image (it will go in your home directory) by typing the following in terminal (it will take a while).

```
dd if=/dev/cdrom of=~/winxpcd.iso
```

---

### Post by Sims12345 on 2009-05-02
Would it be easier if I removed Ubuntu all together using Gparted? If so, could you point me in the direction of a guide for that, as I have tried it in the past but have not really been successful...

---

### Post by aesis05401 on 2009-05-02
The issue shouldn't be getting Ubuntu off, as you can do that very easily from within the windows installer.  You just need to get booted into the XP installer.  Have you tried the suggestions from delcypher?

Edit: I should mention that the big problem with removing Ubuntu first is that you could find yourself without a bootable environment at all. You shouldn't have any problem installing XP over Ubuntu if you have proper XP install materials.

Edit 2: What happened after you removed disks and pressed a key to restart?  I am not familiar with your setup, but it sounds like that would have rebooted your system into the USB based windows installer.

---

### Post by delcypher on 2009-05-02
I've found that the Windows XP setup sometimes crashes if there is a foreign filesystem present.

However DO NOT USE GPARTED for the moment. You need to make sure you have a working bootable USB stick. You will also need to make a bootable UBUNTU USB STICK if you want to use gparted, because you cannot use it within ubuntu to delete/modify a partition in use. Read [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") to find out how to make a UBUNTU USB STICK, you will need a ubuntu live cd image (.iso - available from the ubuntu website).

How did you make the BOOTABLE USB WINDOWS XP STICK?

---

### Post by Sims12345 on 2009-05-02
Using Unetbootin, I get to the Unetbootin screen, press enter for default but nothing happens, it just goes back to the unetbootin screen with the 10 second countdown

---

