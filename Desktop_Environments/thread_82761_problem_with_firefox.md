---
title: "problem with firefox"
date: 2005-10-27
forum: Desktop Environments
---

### Post by nene on 2005-10-27
Hi a have a problem with firefox;
please see the picture.
AD MAIORA

if I run the command mozilla-firefox on the shell, it get this error:

(Gecko:9272): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed

---

### Post by mykey on 2005-10-27
run it without pango support - pango causes problems on some systems - I run it without because its faster

**sudo nano /usr/bin/firefox** - find these two lines
```
MOZ_ENABLE_PANGO=1
export MOZ_ENABLE_PANGO
```
and put a # in front of each of them - start firefox ;)

---

