---
title: "Usplash question."
date: 2008-12-27
forum: General Help
---

### Post by exploder on 2008-12-27
When I start up or shut down Intrepid my 15" wide screen monitor displays "Auto Config Please Wait. This only happens when the usplash is on the screen and the resolution is correct for the desktop, (1366X768 @ 60 Hz)

Is it possible to adjust the resolution of the usplash to correct this? My display is an Acer 15.6 Wide LCD.I am sure someone here has figured this out and can help me out.

---

### Post by red_team316 on 2009-01-04
Try adding a vga=### line to your kernel line in /boot/grub/menu.lst

See here to figure out what ### number you will need to use.
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

