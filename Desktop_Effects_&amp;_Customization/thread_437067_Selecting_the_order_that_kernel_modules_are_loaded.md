---
title: "Selecting the order that kernel modules are loaded"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by TheFuzzy0ne on 2007-05-08
Hi.

I have just compiled a module call lmpcm_usb, which gives me the functionality I am lacking with my Logitech MediaPlay cordless mouse. Every time I reboot my machine, the functionality is lost, and I have to rmmod usbhid.ko from the module, the re-add lmpcm_usb, and then add hidusb back again. Only then will my mouse work.

How would I go about ensuring that lmpcm_usb gets loaded before hidusb?

Thanks in advance.

Daz.

---

### Post by jputman01 on 2007-05-08
> **TheFuzzy0ne said:**
> Hi.

I have just compiled a module call lmpcm_usb, which gives me the functionality I am lacking with my Logitech MediaPlay cordless mouse. Every time I reboot my machine, the functionality is lost, and I have to rmmod usbhid.ko from the module, the re-add lmpcm_usb, and then add hidusb back again. Only then will my mouse work.

How would I go about ensuring that lmpcm_usb gets loaded before hidusb?

Thanks in advance.

Daz.

have you tried ```
sudo gedit /etc/modules
``` and add the module to the list before hidusb? i believe they load in the order the are in the list, please correct me if i am wrong

---

### Post by TheFuzzy0ne on 2007-05-09
Hi, Thanks for your reply.

The only modules in /etc/modules are fuse and lp. I don't think I only load two modules at start up :lolflag: 

Sorry. :confused: 

Daz.

---

