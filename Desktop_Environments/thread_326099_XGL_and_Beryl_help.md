---
title: "XGL and Beryl help"
date: 2006-12-27
forum: Desktop Environments
---

### Post by sdmike on 2006-12-27
Ok so I have an ATI 1800XL video card and I checked and my system says it has 3d acceleration. I went through this whole tutorial on how to load the 2. Then at the end I got this error but I still had the Beryl red gem as my icon.

jack@jack-desktop:~$ beryl-manager
jack@jack-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension

So what should I do. Keep in mind I was using the ATI tutorial.

Thanks

---

### Post by ZERO_SHIFT on 2006-12-28
Have you tried sing AIGLX instead of XGL??

---

### Post by rigdzinthar on 2006-12-28
there have been problems with ATI and XGL, if you card supports compisite extension then use:
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX)

cheers

---

