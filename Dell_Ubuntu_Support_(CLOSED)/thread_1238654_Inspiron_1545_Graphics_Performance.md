---
title: "Inspiron 1545 Graphics Performance"
date: 2009-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Masterofpsi on 2009-08-12
I just bought a Dell Inspiron 1545 with Intrepid on it. Everything seems fine, except the graphics performance is far below what my card is capable of. glxgears flickers and gets me about 160 FPS; meanwhile, running glxgears on a Fedora 10 LiveCD gets me about 1200 FPS.

"glxinfo | grep direct" gets me "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)"

lspci returns:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

It seems like the main problem is that direct rendering is not enabled, but I know that it can be. Can anyone tell me how to do that?

---

### Post by Masterofpsi on 2009-08-13
Ok, so I upgraded to Jaunty. Now glxgears gets me 800 fps with compiz and 850 with metacity, but glxinfo | grep direct still gets "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)," and 850 still isn't the 1200 I was getting with Fedora.

Does anyone know how I can enable direct rendering?

---

