---
title: "Compiz Fusion and Intel GMA 950"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by loopeando on 2007-07-29
I have a Lenovo 3000 N100 laptop with Ubuntu Feisty with Compiz (Desktop Effects) enabled and since the onboard VGA, the GMA 950, is awful I was wondering if I could run Compiz Fusion as smooth as Compiz.

Any experiences?

---

### Post by BoBoL on 2007-07-30
Hello,

I've the same graphic card and it works perfect, but there is a small performance difference (you don't see it).

Bye!!!

---

### Post by johannes_ on 2007-07-30
Hi BoBol,

can you please paste your xorg.conf or hmm, I have an Intel GMA 945 graphics card and Compiz ran smoothly  with openSUSE 10.2, but now I changed to Ubuntu Feisty Fawn 7.04 and I've installed an 64bit version of compiz fusion, but it doesn't work regardless what I'm doing:

compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

the repository I used:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
deb-source [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

I've enabled the window decorator plugin, I've installed 915resolution and I've added a few lines in xorg.conf. I really don't know what to do ... :-/

best regards,
Johannes

---

