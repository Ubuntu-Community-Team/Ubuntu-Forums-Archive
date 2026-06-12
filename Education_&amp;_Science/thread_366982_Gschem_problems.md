---
title: "Gschem problems"
date: 2007-02-21
forum: Education &amp; Science
---

### Post by bebop_tango on 2007-02-21
I don't know what happened, but gschem suddenly stopped working.

First it accused it couldn't find ice-9/slib-old.scm in the library path. I tried recompiling guile (I installed gschem through the gEDA CD) but no good... so I tried to recompile gschem and now I get this error:

```
Creating ps (using groff)
troff: fatal error: can't find macro file s
make[2]: *** [nc.ps] Error 1
make[2]: Leaving directory `/opt/geda-sources/gedagaf/geda-symbols-20060906/documentation'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/opt/geda-sources/gedagaf/geda-symbols-20060906'
make: *** [symbols_install] Error 2

```

So I'm stuck...

---

### Post by Adrian Nania on 2007-02-22
You have no way of installing parts of gEDA, as this stuff is unbelivable fussy. You MUST delete anything and install all from schratch, as the developers kindly advise us ...
Have fun!

---

