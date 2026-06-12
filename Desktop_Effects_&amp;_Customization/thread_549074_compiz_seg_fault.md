---
title: "compiz seg fault???"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by phazer on 2007-09-12
Anyone got any ideas????

phazer@Skull:~$ compiz --replace
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by overdrank on 2007-09-13
> **phazer said:**
> Anyone got any ideas????

phazer@Skull:~$ compiz --replace
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Hi could you tell us what model of video card you have and maybe we can help!

---

### Post by soro2005 on 2007-09-13
Try switching off the screensaver plugin. There seems to be an issue there.

---

### Post by phazer on 2007-09-14
Where do you turn off the screensaver plugin?

---

### Post by Forlong on 2007-09-14
That issue is only related to Compiz Fusion and only to a specific repository.
Are you using the version of Compiz that came with Feisty?

Please answer overdranks question about your graphics card. You can also post the output of this in the terminal:
```
grep -v ^# /etc/X11/xorg.conf
``` (use the forum's CODE tag please)

---

### Post by maoz3000 on 2007-09-22
I have the exact same problem with Intel 82852/855GM Integrated Graphic Device. I installed compiz according to this link: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
Anyone?
10x,

Itay.

---

