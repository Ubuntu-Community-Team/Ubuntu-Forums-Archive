---
title: "What is the max resolution for XGL+Nvidia with two screens and twinview?"
date: 2006-11-17
forum: Desktop Environments
---

### Post by xutopia on 2006-11-17
I have a setup at work with 2x24 inch LCD monitors, an Nvidia card and XGL.  

The native resolution of my monitors is 1920x1200 but they currently run at 1680x1050 which as everyone knows blurs text and isn't fun to use.  I haven't been able to run XGL with a resolution above that.

Does anyone know if the limitation is driver based, XGL based or hardware based?  My xorg.conf says my video card is a "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]".

---

### Post by fuzz500 on 2007-08-30
Hi, I have read that the xgl max width is 2560 pixels. I did find that to be true when I was running an ATI X300 video card, with XGL and compiz running. When I ran glxgears on my dual monitor 3200 pixel wide screens, the gears would stop turning past the 2560 pixel mark. However, I recently installed an nvidia 8600 gts and using twinview, I have not been limited to 2560, but have been able to push the compiz desktop (running the proprietary nvidia driver, 100.14.11 w/ AIGLX not XGL) to both screens at 1920x1200 = 3840 pixels wide, and glxgears runs anywhere on the screen. You can even rotate the cube and everything is working just fine. Pretty sweet actually. I think maximum xgl width is a function of the video driver.
regards,
Fuzz500

---

