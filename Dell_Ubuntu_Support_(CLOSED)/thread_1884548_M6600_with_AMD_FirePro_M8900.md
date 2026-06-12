---
title: "M6600 with AMD FirePro M8900"
date: 2011-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tamale on 2011-11-21
I have a new dell precision M6600 with the AMD FirePro M8900 GPU: [http://www.amd.com/us/products/workstation/graphics/ati-firepro-mobility/m8900/Pages/m8900-overview.aspx](http://www.amd.com/us/products/workstation/graphics/ati-firepro-mobility/m8900/Pages/m8900-overview.aspx)

All I'd like to know is how to get a decent ubuntu experience with this laptop.  I was using the default open-source drivers that come with 11.10 fine for a few days, but this morning an update must have broken them, because now it's very laggy to perform any operations in Gnome or unity.

I've also tried fglrx, but there are numerous artifacts with rendering fonts and transparency effects, so I'm guessing either my card isn't supported or I'm doing it wrong somehow.  (I tried both the standard fglrx package from ubuntu and the AMD preview drivers for OpenGL mentioned here: [http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx))


Please help.. I know I can't be the only one with this video card that's trying to use ubuntu.

---

### Post by Tamale on 2011-11-22
w00t.. found out the cause of my problems was a poorly-made GTK3.0 theme.. "Ambiance Wolfe V4".  Once I switched to a different theme with gnome-tweak-tool, the open-source drivers started working fine again. Still no luck with fglrx, but I'm happy to keep using the open-source drivers for now... just wish battery life was better.

---

