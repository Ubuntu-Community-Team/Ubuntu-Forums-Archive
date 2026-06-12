---
title: "Printer not recognized in Kubuntu 14.04"
date: 2014-05-14
forum: Desktop Environments
---

### Post by Abd_el_Rahman_Magdy on 2014-05-14
Hi there. I was using Ubuntu until recently. Then, I switched to Kubuntu 14.04 because its Wacom configuration tool is more convenient and appropriate for me. However, I have a small problem. Back, when I was using Ubuntu, I was able to use any printer just by plugging it in to the USB port. I cannot do the same in Kubuntu. For some reason, I am unable to setup and use any printer. I solved the problem with HP printers by installing hplip-gui. But this is for HP printers only. What should I do with the other brands.

---

### Post by SeijiSensei on 2014-05-14
Plug in the printer, then follow one of two paths.  I usually just open a browser on the machine and visit [http://localhost:631/](http://localhost:631/) to use the native CUPS interface.  See if CUPS can detect the printer and install a driver for it.  You'll be prompted for a login along the way.  Use your own username and password if you have sudo privileges.

Alternatively, select System Settings from the main menu, then choose Printers.  That's really just another front-end to CUPS though.  The [http://localhost:631/](http://localhost:631/) method works on any Linux system with CUPS installed regardless of the desktop environment.

---

### Post by Abd_el_Rahman_Magdy on 2014-05-14
I will try this... But I might need some help since I tried it with one of the HP printers before installing hplip-gui, and I was unable to install it appropriately.

Just in case, is there any other solution that makes things as easy as they were with Ubuntu?

---

### Post by Abd_el_Rahman_Magdy on 2014-05-16
CUPS is also not recognizing the printers... I really don't know what to do... the only solution I have right now is to install Ubuntu on VirtualBox, and use it when I want to print any document

---

