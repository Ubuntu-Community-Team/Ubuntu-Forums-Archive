---
title: "Gnome-Shell won't start"
date: 2010-04-25
forum: Desktop Environments
---

### Post by Ultra_Man on 2010-04-25
I tried gnome-shell using the default karmic repositories, it was good, so I tried ricotz, it was buggy and slow, so I forced version in synaptic. It worked fine for a bit after that, but after I logged off and logged on again I get this error in terminal:

(mutter:12662): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by Ultra_Man on 2010-04-25
I fixed it myself. If you're using ricotz's ppa and don't like it, use the search tool in synaptic and in the filter use "version". Uninstall any package that has his version installed. They'll revert back to the normal defaults, but first you have to delete his ppa. Then just install gnome-shell again.

---

