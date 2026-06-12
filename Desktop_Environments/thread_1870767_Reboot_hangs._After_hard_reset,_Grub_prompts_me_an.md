---
title: "Reboot hangs. After hard reset, Grub prompts me and I am able to boot."
date: 2011-10-27
forum: Desktop Environments
---

### Post by oakdog8 on 2011-10-27
If I do a normal reboot from X or if I type sudo reboot, my computer reboots to a maroon screen where it then hangs indefinitely. I have to hold down the power button until it shuts off and then hit it again. Once it powers on, the Grub menu appears in a maroon screen where I can select Linux, at which point it successfully boots. 

This is a pain. I cannot reboot over SSH because it never comes back online. I don't want to have to hard reset the computer every time I reboot. Has anyone else run into similar problems? 

Also, slightly unrelatedly, every time I get to the login screen, it crashes if I hit the enter key. The screen goes black for a few seconds before the login screen comes back. After that everything works fine.

I am wondering if part of it is related to the nVidia graphics driver. I have two GTS 450 cards running with Xinerama.

---

### Post by drs305 on 2011-10-27
I'll think about your situation, but the first thing I wondered is what happens if you press ENTER at the maroon screen. I've had some posts where the Grub menu wasn't visible, but it was there awaiting input; in those cases pressing ENTER would boot the default menuentry.

---

### Post by oakdog8 on 2011-10-28
Nope, it's completely unresponsive. I've hit every key on the keyboard. I am using a logitech wireless with usb dongle, but I don't think that should matter since I can use it just fine after the hard reboot and I can even use it to get into the BIOS.

---

### Post by oakdog8 on 2011-11-13
For anyone that's curious, here's what happened:

After installing ubuntu, I had added an old hard drive to my computer in a lower slot than the drive with ubuntu on it, so the new disk  became sda, and the boot disk moved from sda to sdb. I made sure the change was reflected in my BIOS, but grub must have still been trying to load from sda. I only found this out after I removed the old hard drive from my system and everything returned to normal.

---

