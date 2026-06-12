---
title: "Can't use Windows"
date: 2009-05-03
forum: General Help
---

### Post by Cameron88799 on 2009-05-03
Hey.
I have just installed Ubuntu 9.04 onto my 8gb USB (not the image, I selected it as the drive to install Ubuntu on in regular install [Not a good idea?]) And now, whenever I turn on the computer I used to install it, it comes up with "Loading Grub" or some such, but fails if the USB stick isn't in, and just stays at that screen, not letting me use Windows.
But if the USB is in when I boot up, it will give me the option of either booting 9.04 or Windows XP.
Seeing as it's not my computer, this is quite an issue, seeing as using someone elses USB just to get into the OS isn't prefferable.
Is there any way to fix this without earasing anything on Windows?
Any help would be great. 

And also, if I put in a, say, 3 gb partition on the hard drive for another version of Ubuntu, would that make the Grub load properly, and allow the boot menu to come up?

---

### Post by delcypher on 2009-05-03
When you installed Ubuntu to the USB stick the GRUB bootloader was installed to the Master boot record of your hard drive which well then in turn look for grub which will be on USB stick (/boot/grub/). 

You really shouldn't install ubuntu directly to your USB stick as it will probably severely reduce the life of your USB stick (it will be constantly writing to it).

You should of used the "USB startup disc creator" on Ubuntu (System > Administration > USB startup disc creator) with a live cd .iso. The tool also allows a persistence file (saves the changes you made to ubuntu when you use it in live cd mode).

You could also use unetbootin, although that doesn't create a persistence file.

To fix the mess on your hard drive you need the original Windows XP Setup disc. Boot into the recovery console and run ```
fixboot
fixmbr
```. Then exit, this process is described [here]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/")

When you do an Ubuntu install again when you're at the last stage of the setup click advanced and you can control where GRUB goes (if you want it)

See [screenshot here]("http://ubuntuforums.org/attachment.php?attachmentid=112243&d=1241334255")

---

### Post by bumanie on 2009-05-03
If you have a windows installation disc, go to repair and then in console mode do FIXMBOOT followed by FIXMBR - that will remove grub from the hard drive's mbr and allow xp to boot, but the usb drive won't boot any longer. If you have a bios that boots from usb, boot a ubuntu live cd and install grub to (hd0,0), if you don't have a bios that boots from usb try a persitent install from [here]("http://www.pendrivelinux.com/")on the usb drive or else try the tool from within ubuntu that creates an install onto a usb device.

---

