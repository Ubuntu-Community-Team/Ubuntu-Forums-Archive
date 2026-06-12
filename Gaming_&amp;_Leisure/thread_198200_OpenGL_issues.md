---
title: "OpenGL issues"
date: 2006-06-16
forum: Gaming &amp; Leisure
---

### Post by Turkten on 2006-06-16
I am running an ibook G3/900. Its got a radeon 7500 in it and 384 megs of RAM. X seems to be detecting everything fine with my openGL, however whenever I try to use it in any software (in this case I am trying to get it to work in SNES9x) it is very slow. Even the bundled screensavers that run ogl are slow. Excruciatingly so. Any comments on possible causes/fixes? Thanks for any help in advance!

---

### Post by eqisow on 2006-06-17
Have you installed video drivers? Do "glxinfo | grep direct" at the terminal to find out. If you do, it should say "direct rendering: Yes." If it doesn't, try following the [ATI driver wiki]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI").

---

