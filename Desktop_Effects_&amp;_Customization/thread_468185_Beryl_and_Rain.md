---
title: "Beryl and Rain"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by WaeV on 2007-06-08
Hey I am running ubuntu 7.04 feisty with ubuntu studio packages and for some reason the rain plugin doesn't distort the underlying desktop, it only adds a rain overlay of sorts.  I can see a transparent shadow-like ripple, but the isons, text, background etc. aren't distorted.  Does anyone know how to fix this?  It had worked previously on this machine with all of the default settings and the same setup (AIGLX).  I have an ATI Radeon 9800.

---

### Post by WaeV on 2007-06-10
Does anyone know what the problem is?

---

### Post by searayman on 2007-06-11
i'm not sure but i do kow soem graphics cards don't support some shadign thing that this plugin uses....

---

### Post by metroplex on 2007-06-11
I would also guess that your graphics card / drivers don't support vertex / fragment shaders which is required for the rain plugin.

---

### Post by WaeV on 2007-06-13
Do you know how I would check if I had those plugins, if they are compatible, or how I could install them?

This did work before with the same setup, except I didn't have xorg.conf last time.  I don't know how it ran without it but I didn't have to do any modifications or anything so I just let it be.

I don't know if there is a xorg.conf setting that has to do with vertex fragment shading, but it should be compatible with my card becuase it worked before with AIGLX and all.

---

