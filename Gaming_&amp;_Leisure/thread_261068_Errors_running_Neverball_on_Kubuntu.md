---
title: "Errors running Neverball on Kubuntu"
date: 2006-09-19
forum: Gaming &amp; Leisure
---

### Post by srunni on 2006-09-19
Hi,

I installed Neverball on Kubuntu 6.06, using apt-get. However, when I clicked on the icon in the KMenu, it just wouldn't load. I tried to launch it from Konsole, and I got this: ```
open /dev/sequencer: No such file or directory
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
neverball: Couldn't find matching GLX visual
```

Does anyone know what's wrong?

Thanks

---

### Post by skymt on 2006-09-19
Are you running [the right drivers](https://help.ubuntu.com/community/BinaryDriverHowto) for 3D?

---

### Post by srunni on 2006-09-19
Thanks so much for that link. All I needed to do was go to the binary page and cofigure xorg.conf so that it would work with my X300. I already had the  xorg-driver-fglrx package installed, but I hadn't configured xorg right. The simple tutorial worked just fine for me.

---

