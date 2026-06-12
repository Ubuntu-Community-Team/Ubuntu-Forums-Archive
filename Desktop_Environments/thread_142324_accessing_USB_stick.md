---
title: "accessing USB stick"
date: 2006-03-10
forum: Desktop Environments
---

### Post by zina on 2006-03-10
Hello,

I just plugged in a USB stick. What should I do next in order to access it? Where can I find the mounting point, for example? Or is it already mounted authomatically somewhere?

Thanks,
Zina

---

### Post by meborc on 2006-03-10
well... you should have nautilus pop up with the contents of your usb stick... 

otherwize, the mounting point should be /media

---

### Post by skirkpatrick on 2006-03-10
It should automount and put an icon on your desktop.  However, you might have the same problem I have.  Most newer USB sticks are 2.0 and 1.1 compliant.  Which means that they want to run at 2.0 speeds but will work at 1.1 speeds.  My sticks work fine on my laptop but I couldn't get them to work with the ports at the front of my desktop machine.  I managed to find a webpage that talked about the fact that some cables that connect a front jack to a port on your motherboard will not allow USB 2.0 devices to operate.  The solution is to either get a case with better cables, only use the back ports, use the back ports with a USB 2.0 hub (my daughter found out she had bought a 1.1 hub), or to use the command **sudo rmmod ehci_hcd** to remove the high-speed driver module.  However, removing the high-speed driver module that way only works until you reboot and prevents you from using 2.0 devices at high speeds through any of your other ports.

---

### Post by zina on 2006-03-10
I finally removed the stick without umounting (as I couldn't do it anyway), and rebooted the system. It wouldn't boot properly, however, and wanted that I run fdisk! So after a colleague helped me with it, the USB stick mounted perfectly. So it seems it wasn't a USB stick problem, but a hard disk error.

Zina

---

