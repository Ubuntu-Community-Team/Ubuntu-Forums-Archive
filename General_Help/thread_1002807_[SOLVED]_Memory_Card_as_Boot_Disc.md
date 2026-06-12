---
title: "[SOLVED] Memory Card as Boot Disc"
date: 2008-12-05
forum: General Help
---

### Post by jheaton5 on 2008-12-05
Can you make a boot disk from a memory card and then can you boot from it?

---

### Post by snowpine on 2008-12-05
Hi Jheaton, do you mean a SD card (like the one from a digital camera)? 

If so the answer is yes. I run Crunchbang linux (a variant of Ubuntu) from a 4gb SD card. I am pretty sure the same process works fine with Ubuntu or Xubuntu as well.

All you need to do is boot from the Live CD and run the installer. Make sure that when you get to the partitioner stage, you choose your SD card and not your hard drive! Also, when you get to the last step in the installer, you need to click Advanced Options and make sure you install Grub on the correct device (the SD card).

Then you should be able to reboot, change the boot order in your bios (this varies from computer to computer) and boot from the SD card. This all assumes that your computer is capable of booting from SD. :)

I will warn you that it is very slow compared to running from a hard drive. :(

---

### Post by redilyn on 2008-12-05
You can also create a live usb installation on your memory card....I think.

System -> Administration -> Create A USB Startup Disk

Then you could boot any computer from the memory card as long as the bios supports booting from a usb device.

*Note - I havn't tryed this myself.

---

