---
title: "PDFs slow to open"
date: 2009-05-19
forum: General Help
---

### Post by hammeraxe on 2009-05-19
ok, I'm experiencing a weird problem here. When I open any PDF in Evince it just says Loading... and nothing really happens. Sometimes it manages to open the file after a while, but it is not usable anyway, because every page takes a long while to load. This is extremely annoying, as it is impossible to quickly browse through PDFs. It is the same in ePDFView, but not in xpdf. Yet xpdf isnt my favourite so maybe you guys have some ideas on how to fix this.
Thanks.

---

### Post by Legace on 2009-05-19
Reinstall the following packages from Synaptic and see if that helps:

- poppler-utils
- libpoppler4
- libpoppler-glib4
- evince

---

### Post by hammeraxe on 2009-05-19
no luck. I couldn't reinstall poppler-utils as it would require uninstalling a whole lot of other packages... The Mark for reinstallation option in Synaptic was greyed out. There was no libpoppler4 or libpoppler-glib4 on my system, only libpoppler3 and libpoppler-glib3, which I couldn't reinstall for the same reason. Reinstalling evince alone had no effect

---

