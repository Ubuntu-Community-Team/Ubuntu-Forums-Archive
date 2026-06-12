---
title: "xorg.conf oboslete?"
date: 2009-09-11
forum: Desktop Environments
---

### Post by Debianforce on 2009-09-11
Hi there.
I have tried to use gnome desktop and I cannot use the 3D functions because I cannot figure out how to configure my DVI - HDMI connected PC to my TV.
Graphics card: Asus EAH 4850 series. 
You are able to "enable" some hardware drivers through gnome desktop by clicking on "System Tools" but this does not work and gives me a blank screen if I try...

Question: Is xorg.conf obsolete now, and could someone explain to me how I can manually configure the drivers, and the TV? How to make X use drivers from ATI with full 3D support, and use my settings. For example 1024x768 resolution and 24bits. 

Thanks in advance.

---

### Post by markbuntu on 2009-09-12
If you have no xorg.conf then the driver has not been initialized.

sudo aticonfig --initial

This will write a new xorg.conf. To configure the driver you need to use the Catalyst Control Center or aticonfig

aticonfig --help

---

