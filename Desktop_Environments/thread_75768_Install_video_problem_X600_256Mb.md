---
title: "Install video problem X600 256Mb"
date: 2005-10-14
forum: Desktop Environments
---

### Post by MeijUbuntu on 2005-10-14
Hello,

When i wan't to install Ubuntu my video gets scrambled (during install). I have a ATI X600 256 MB video card (DVI connection) and a DEll 1905FS Screen.

Any suggestions ?

---

### Post by MeijUbuntu on 2005-10-14
Update

I finally could install Ubuntu with the option --> linux vga=771

But when the installation is completed X server can't start.
I noticed in the xorg.conf that it detected an ATI driver (which is oke), but it fails X server.

Who can help ?

---

### Post by tjabri on 2005-10-14
Hey bud,

Try to set the driver from "ati" to "vesa" in your xorg.conf file. That might bring you up into the X server.

Also, does your X server bring up any error messages? It should ask you if you want to see any output on the error. That would help to troubleshoot your problem.

---

### Post by MeijUbuntu on 2005-10-14
Yub, you are right

It says something about missing fonts and other crap.

When i install Ubuntu i have no internet connection. Could that be the problem ? Does it need something to download ?

---

