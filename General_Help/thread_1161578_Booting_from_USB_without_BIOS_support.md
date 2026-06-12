---
title: "Booting from USB without BIOS support"
date: 2009-05-16
forum: General Help
---

### Post by justcop on 2009-05-16
I am using an old mobo to boot [XBMC live]("http://xbmc.org/") (a distro based on jaunty) from a USB pen but the motherboard has no support for this. I plan to use [this]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/") method to create a CD to launch USB drivers and load GRUB.

I am a relative linux newbie (so please be kind with answers) but have a couple of questions on how this is going to work. The usb pen has its own version of grub on it which allows the ability to choose which video drivers are loaded for XBMC. This feature needs to be retained or at least choose a default for me. Could this perhaps be done by taking the menu.lst from the pendrive and using it to replace the default one or maybe just leaving it as it is will retain these options.

JC

---

### Post by Locutus_of_Borg on 2009-05-16
you should be able to chainload grub on your MBR to the grub on your USB device assuming the drive assignment remains persistent across boots, though it rarely does...

i used to boot from an external drive using grub on my MBR and i would have to ctrl+alt+del at the grub screen to reload it in order for the external drive and grub to work..i dont know why, but it would only work if i did this...

---

