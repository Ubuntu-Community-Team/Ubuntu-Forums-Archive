---
title: "Switched video card X server crash"
date: 2006-08-17
forum: Desktop Environments
---

### Post by RMSe17 on 2006-08-17
Hi, I swaped out a video card in my machine running Dapper Drake 6.06, and now there is a msg saying that X server crashed because the settings are wrong...

What I had: ATi Radeon X1300  PCIe
What I have now: S3 Virge VX    (STB Velocity 3D)   PCI

I assume I need to run the X server config wizard or something, but I dont know exactly what to type to launch it, cause I just have command line, no desktop...

So, if you could tell me what to type, I would be very thankful :)

Thanks,
RMSe17

---

### Post by stinerman on 2006-08-17
```
sudo dpkg-reconfigure xserver-xorg
``` 
That should do the trick.

---

