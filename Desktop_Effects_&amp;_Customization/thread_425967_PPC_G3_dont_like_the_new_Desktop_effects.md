---
title: "PPC G3 dont like the new Desktop effects"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by SXR on 2007-04-28
I cannot get the new desktop effects to run on my PPC G3 Any Ideas?> ?

---

### Post by A Zen Roshi on 2007-12-12
My ppc doesn't seem to like desktop effects either.  I have looked for a way to edit the configuration file to default to "workspaces on a cube" and I couldn't find that either.  I believe it doesn't work well because the video ram is so low.  I'll keep searching and will post if I find something.

---

### Post by A Zen Roshi on 2007-12-12
from terminal  you can type

desktop-effects --help

the output for a G3 should read something like this

modinfo: could not find module ipw3945
modinfo: could not find module fglrx
modinfo: could not find module nvidia_legacy
modinfo: could not find module nvidia_new
modinfo: could not find module nvidia
nvidia hardware not available

apparently the nvidia hardware is not compatible with desktop-effects.

sorry for you and me

---

