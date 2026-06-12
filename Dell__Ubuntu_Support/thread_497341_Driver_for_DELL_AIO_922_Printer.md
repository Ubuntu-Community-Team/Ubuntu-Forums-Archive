---
title: "Driver for DELL AIO 922 Printer"
date: 2007-07-10
forum: Dell  Ubuntu Support
---

### Post by Guennarr on 2007-07-10
Hi everyone, 

I have a DELL 5000 and a DELL AIO 922 printer scanner combo. 
I am aware of the fact that only a handfull of scanners is supported by linux. But if possible I would like to use the device as a printer. 

I use ubuntu 7.04 and the printer is recognized by the system when trying to install the printer. Unfortunately during the next step ubuntu wants me to add the printer drivers. Does anyone know where to get the drivers for ubuntu 7.04?

Thanks in advance for your help! 

Greetings, 
Günther

---

### Post by MyR on 2007-07-10
I have the same printer. I've done a lot of searching and haven't been able to get it to work. Such a shame, it's a good printer.
:[

---

### Post by MyR on 2007-07-14
however, you can print from winblows on a virtual machine. i use/recommend virtualbox.

---

### Post by Wiebelhaus on 2007-07-14
I'm sure you both know , Dell printers are manufactured by Lexmark , how about an equivalent driver for the lexmark counterpart?

---

### Post by MyR on 2007-07-14
it's a lexmark x5270. also a paperweight (obviously). i tryed a driver for a different lexmark.. and i got it to feed some paper through but thats about it.

---

### Post by strabes on 2007-07-15
Have you tried adding it through the CUPS interface? Simply type ```
http://localhost:631/
``` in the address bar of your browser. This interface seems to have more drivers.

---

### Post by ragu99 on 2007-07-15
Here are the z600 drivers. I have Dell AIO 920 on a windows networked computer and it worked with it. It should work with the Dell AIO 922 also
Install the deb files
the ppd driver will be located at

usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz

[http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Lexmark/Z600/z600cups_1.0-2_i386.deb](http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Lexmark/Z600/z600cups_1.0-2_i386.deb)
[http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Lexmark/Z600/z600llpddk_2.0-2_i386.deb](http://www.elinuxstop.com/support_center/Downloads/Drivers/Printers/Lexmark/Z600/z600llpddk_2.0-2_i386.deb)

---

### Post by MyR on 2007-07-15
> **strabes said:**
> Have you tried adding it through the CUPS interface?
I tryed both "recommended" drivers on the CUPS interface. the printer did not respond to either.

> **ragu99 said:**
> Here are the z600 drivers. I have Dell AIO 920 on a windows networked computer and it worked with it. It should work with the Dell AIO 922 also
i tryed the z600 drivers. the printer did not respond to these either. your printer works because it is connected to a windows computer, correct?
btw, those link are broken.

thanks for the suggestions but until someone somehow writes a driver for the 922 it appears to be a lost cause.

---

