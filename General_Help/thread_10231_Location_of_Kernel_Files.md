---
title: "Location of Kernel Files"
date: 2005-01-06
forum: General Help
---

### Post by hardening.agent on 2005-01-06
Its been 2 months since I installed Ubuntu, and it rawks! I think I finally found a suitable MSWin replacement for myself.

I am trying to install a Cisco VPN client onto my ubuntu installation on a notebook to admin my servers at work. It requires me to insert the location of where the ubuntu's kernel source is. It states that typically its in /usr/src/linux etc.... I checked in the stated directory it isnt there.

Blindly looking ard didnt help either.
Question : Where is it?

*note: i am techie/admin on windows, dimwit/numskull in linux, so you'll have to excuse my lack of linux knowledge

thanks a million.

---

### Post by fng on 2005-01-06
If you need the kernel source : i recommend getting it from [www.kernel.org](www.kernel.org).
Or you can 'apt-get install linux-source-2.6.8.1' to get it from apt-get with all the debian patches included,

---

### Post by hardening.agent on 2005-01-06
So thats where it is! 
Apt-get...sweet.

Thank you fng. :D

---

### Post by jdodson on 2005-01-06
[QUOTE=hardening.agent]So thats where it is! 
Apt-get...sweet.

Thank you fng. :D[/QUOTE]


for most things all you need to use are the kernel-headers.  those come on the install cd, the kernel source is something like 50 megs and the headers are on the main cd and much smaller.  for most things again, the headers work well.

---

### Post by az on 2005-01-06
You should use the linux-headers.  Install that package and use that directory when prompted for your linux source tree (/usr/src/linux-headers-2.6....whatever...)

If you just install the linux source, you will need to compile configure and compile the kernel before you can use that tree for building modules.  The linux-headers however,  are all ready to go...

---

### Post by Rancoras on 2005-01-06
[QUOTE=hardening.agent]I am trying to install a Cisco VPN client onto my ubuntu installation on a notebook to admin my servers at work.[/QUOTE]

I had good luck using vpnc from universe.  I just used some of the settings from my windows .pcf file and plugged them in the appropriate places in the vpnc config file.  It's been a while since I used it, but it's there if you want to play with it.

---

### Post by jdong on 2005-01-06
please use **linux-headers**, **linux-source**, **linux-anything**. kernel-* is an artifact from Debian. These files are not Ubuntu's kernel.

---

### Post by machiner on 2005-01-08
I have the headers /usr/src...  but when I try to install the nforce sound/lan driver I get errors. I have tried to tell the script that the source is there (/usr/src/...) but it never finds what it needs.

THis was a month ago I forget the actual error message, but the install of these drivers always fails.

Ideas?  Thanks

---

