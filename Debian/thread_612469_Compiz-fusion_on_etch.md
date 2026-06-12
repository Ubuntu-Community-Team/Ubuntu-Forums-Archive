---
title: "Compiz-fusion on etch"
date: 2007-11-13
forum: Debian
---

### Post by mevets on 2007-11-13
I have in the past ran compiz fusion under ubuntu. I now have an installation of debian etch and cant get compiz to work. I used this tutorial to get it installed: [http://shame.tuxfamily.org/repo/?cat=11](http://shame.tuxfamily.org/repo/?cat=11)

When I run fusion-icon I get this output:
```

debian@debian-steve:~$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * Intel detected, exporting: INTEL_BATCH=1
 * No GLX_EXT_texture_from_pixmap with direct rendering context
 ... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
compiz.real (core) - Fatal: No composite extension

```

---

### Post by cprofitt on 2007-11-14
My assumption is that you are using an ATI card, but I could be wrong. If you are using an ATI card you will want to do a search on the Debian Forums about installing the ATI driver from the repos and then recompiling so you have openGL support.

Then things should work for you...

If you do not have an ATI card then the issue is with what ever graphics driver you have installed for your card... openGL is not being supported.

---

