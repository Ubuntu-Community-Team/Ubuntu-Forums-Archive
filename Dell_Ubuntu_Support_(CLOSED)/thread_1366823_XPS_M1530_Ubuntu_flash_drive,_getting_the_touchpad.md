---
title: "XPS M1530 Ubuntu flash drive, getting the touchpad working"
date: 2009-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pascal11110 on 2009-12-28
I made a bootable flash drive of ubuntu 8.1, and that works fine, it's just that when I boot it on my laptop, the touchpad completely flips out and zooms all over the screen. This is a known issue, and there are fixes, it is just that the fixes are for an installation and not a bootable flash drive. The most common solution is [here]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530") it is just that when I use alt+ctrl+F1 and go into the terminal, and type sudo nano /boot/grub/menu.lst it creates a new file, because their isn't one in that location. I even tried find menu.lst and it didn't find it that way either. I assume this is because grub is installed differently on a pen drive, but I just don't now. Any help is greatly appreciated.

(and my bios is A12)

---

### Post by bobcollard on 2010-01-02
> **Pascal11110 said:**
> I made a bootable flash drive of ubuntu 8.1, and that works fine, it's just that when I boot it on my laptop, the touchpad completely flips out and zooms all over the screen. This is a known issue, and there are fixes, it is just that the fixes are for an installation and not a bootable flash drive. The most common solution is [here]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530") it is just that when I use alt+ctrl+F1 and go into the terminal, and type sudo nano /boot/grub/menu.lst it creates a new file, because their isn't one in that location. I even tried find menu.lst and it didn't find it that way either. I assume this is because grub is installed differently on a pen drive, but I just don't now. Any help is greatly appreciated.

(and my bios is A12)
I'm not sure about Ubuntu 8.1, I started in 9.04 then 9.10.  If you have a "System Settings" you should be able to control your touchpad through that, in keyboard/mouse.  If so it may save the configuration when you are using the flashdrive.  Also there are applets to disable a touchpad or control parts of it especially if, like me, you use a mouse.  Try installing "gsynaptics" first, it has the most controls.  It is being replaced by "gpointing-device-settings"  You can get both through the Synaptic Package Manager or through Terminal.  Hope this helps.

---

