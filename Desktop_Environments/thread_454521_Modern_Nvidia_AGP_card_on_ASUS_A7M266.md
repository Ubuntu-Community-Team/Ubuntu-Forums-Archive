---
title: "Modern Nvidia AGP card on ASUS A7M266"
date: 2007-05-25
forum: Desktop Environments
---

### Post by moopere on 2007-05-25
This post for the archives.  If you are running an ASUS A7M266 (Iv'e got the -D type) and a reasonably recent Nvidia card you will have noticed the crashing....

Try this in your BIOS settings:

AGP 4X Support - Enable
AGP Fast write - Enable
AGP Signal Driving - Manual
AGP Drive Strength P Ctrl - E
AGP Drive Strength N Ctrl - A
AGP Data Strobe P Ctrl - D
AGP Data Strobe N Ctrl - 6
Graphics Aperture - 128MB

I'm running an 8X FX5700 in my A7M266-D with the above settings and it appears stable, even with high OpenGL loads.  Before setting the above values I couldn't even get to the desktop before hard locking.

Thanks to the Nvidia web site and the Nvidia forums for providing the basic information.

Cheers,
Craig

---

