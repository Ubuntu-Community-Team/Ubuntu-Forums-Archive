---
title: "Ubuntu on USB with language screen"
date: 2013-09-08
forum: Development CD/DVD Image Testing
---

### Post by geekrod on 2013-09-08
Hi, I've been trying to get the advanced welcome page booting an Ubuntu 12.04 or 13.04 iso from USB, just as the Live CD does.

I have tried Grub2 and Grub4DOS with these tutorials but I can't find any menu entry example to get the language screen.

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1#TOC-The-Easy2Boot-v1-folders-and-menu-system](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1#TOC-The-Easy2Boot-v1-folders-and-menu-system)

The only tutorial that worked as I wish was the one from RMPrepUSB, but takes a lot of time scanning for isos, is it possible to achieve it manually with Grub2/Grub4DOS?

Thanks


[IMG]http://i.stack.imgur.com/bqzjR.png[/IMG]

[IMG]http://i.stack.imgur.com/FfEwE.png[/IMG]

---

### Post by steve63752 on 2013-09-27
If Easy2Boot takes too long to enumerate the ISOs, then use the FASTLOAD feature. There are also other things you can do which are also [mentioned]("http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1#TOC-Speed-up-the-loading-of-the-Main-Menu") in the tutorial.

---

### Post by sudodus on 2013-09-27
> **geekrod said:**
> Hi, I've been trying to get the advanced welcome page booting an Ubuntu 12.04 or 13.04 iso from USB, just as the Live CD does.

I have tried Grub2 and Grub4DOS with these tutorials but I can't find any menu entry example to get the language screen.

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1#TOC-The-Easy2Boot-v1-folders-and-menu-system](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1#TOC-The-Easy2Boot-v1-folders-and-menu-system)

The only tutorial that worked as I wish was the one from RMPrepUSB, but takes a lot of time scanning for isos, is it possible to achieve it manually with Grub2/Grub4DOS?

Thanks


This is the syslinux boot. Some methods to make USB boot drives will make systems that skip it, or use another boot loader, for example grub2. I know two methods, that make USB boot drives with syslinux,

- The ***Startup Disk Creator*** (usb-creator-gtk and usb-creator-kde) and
***- Cloning with dd*** (which is risky unless you use a tool to help selecting the correct target drive).

See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

