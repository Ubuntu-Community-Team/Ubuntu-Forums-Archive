---
title: "WLAN/ Boot default OS issues"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gsmtnbiker on 2008-04-29
I'm new to linux and experimenting with dual-booting into Ubuntu and XP.  I had Gutsy Gibbon and my wireless card (TrueMobile 8500) worked fine after installing a hardware driver.  Now, Harty Heron is not recognizing my wireless card and doesn't detect a download under System-Administration-Hardware Drivers.  Not sure what's going on but any help is appreciated.

Also, when trying to change the default OS selection when booting in GRUB, I have been trying to change /boot/grub/menu.1st so that "default     0" is "default      8" but gedit will not allow me to save the file when I'm done with it.  Is there an easier way to edit the default boot OS or what do I need to do to save the file?  Thank you.

---

### Post by groovete on 2008-04-29
Hi, 
I can't say anything about the WLAN issue. but it would be helpful for others, if you describe more detailed what you tried to get wlan working.

Changing the boot order is quite easy, type in a terminal: 
```
sudo gedit /boot/grub/menu.lst
```
Then just put the windows entry in front of the entry relating to Ubuntu.

---

### Post by nermalthecat on 2008-04-29
In Hardy, Canonical decided to switch to the new iwlwifi driver, which is open source. 

For previous versions (i.e Gutsy), they used the ipw3945 driver, which uses a closed source daemon to monitor network traffic.

Just try setting your network with networkmanager. It should work out of the box!

---

