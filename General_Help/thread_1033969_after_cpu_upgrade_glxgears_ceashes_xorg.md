---
title: "after cpu upgrade glxgears ceashes xorg"
date: 2009-01-07
forum: General Help
---

### Post by bowens44 on 2009-01-07
**that should read crashes xorg not ceashes xorg ******

I'm not sure if I posted this in the right forum or not. Feel free to move it to where it belongs.

I am using Ubuntu 8.04 with KDE 3.5. I have a nvidia gforce 7600 video card. I am using compiz. Tonight I did a cpu upgrade. I went from an AMD athlon X2 3800 to an amd athlon x2 5400. Before I swapped out the CPU , everything was fine. glxgears was showing about 6500 fps. After the cpu swap glxgears starts rapidly flickering and the the desktop scrambles completely and is unreadable. This is basically a hard crash. I can't get the machine from another box on my network to restart it so I have to hard boot.

So far all I have  done to try to resolve the issue is uninstall the nvidia driver and re-install the nvidia driver. I am used envyNG to install the driver. I have driver 173.14

---

### Post by dcstar on 2009-01-07
> **bowens44 said:**
> **that should read crashes xorg not ceashes xorg ******

I'm not sure if I posted this in the right forum or not. Feel free to move it to where it belongs.

I am using Ubuntu 8.04 with KDE 3.5. I have a nvidia gforce 7600 video card. I am using compiz. Tonight I did a cpu upgrade. I went from an AMD athlon X2 3800 to an amd athlon x2 5400. Before I swapped out the CPU , everything was fine. glxgears was showing about 6500 fps. After the cpu swap glxgears starts rapidly flickering and the the desktop scrambles completely and is unreadable. This is basically a hard crash. I can't get the machine from another box on my network to restart it so I have to hard boot.

So far all I have  done to try to resolve the issue is uninstall the nvidia driver and re-install the nvidia driver. I am used envyNG to install the driver. I have driver 173.14

I can only suggest that you do a full BIOS reset as there may be some settings still configured to the old CPU (voltage etc).

You may also see if there is a newer BIOS as well that may have full support for the newer CPU as it may well be a different chip "family" to the old one.

---

