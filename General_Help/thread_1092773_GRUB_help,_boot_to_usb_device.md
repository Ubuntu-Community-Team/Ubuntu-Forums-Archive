---
title: "GRUB help, boot to usb device"
date: 2009-03-10
forum: General Help
---

### Post by PreviousN on 2009-03-10
Hi ubuntu community. I have an old compter that I want to turn into a media server/file server. I currently have ubuntu Feisty installed on it, but want to eventually trash EVERYTHING on the boot disk and install Ibex as a fresh install. The computer I want to do this to is relatively fast, IE: a pentium 4 2.4GHz with 512MB of RAM.

Sadly, I don't have a cd drive laying around for it. I live far from the city and really can't plan to go pick up a cd drive for a task that I'll do once. AND, the mobo doesn't support booting from USB. But I already have grub on the Feisty install... So here is what I want to do:

1. Download ibex and use UNetBootin to create a live usb disk
2. Plug the usb disk into my old computer
3. Boot the computer into Feisty's Grub
4. Use feisty's grub to boot the USB live disk.
5. Install Ibex onto the hard drive.
6. Reboot into fancy fresh ibex install

Is this even possible? I've read a little bit about grub, but any help would be appreciated. Also, I DO think that my computer supports netboot, but I don't really want to mess around with that..especially if doing this only requires a few booting arguments..

Thanks in advance for the help. :-)

---

### Post by meierfra. on 2009-03-14
It depends on your bios. But more likely you will have to put  the kernel and initrd of the "liveusb" onto the internal drive in order to boot the USB disk.

You might also give [Plop]("http://www.plop.at/en/bootmanager.html") at try. It is a boot manager which is capable of booting USB  devices, even if the  Bios can't.

---

