---
title: "I can't get the chromium browser to work"
date: 2009-06-20
forum: General Help
---

### Post by destreet on 2009-06-20
I running Ubuntu 9.04

When I select it by menu it doesn't start, so I tried the command line:

$ chromium-browser
[3945:3945:259412903:FATAL:/build/buildd/chromium-browser-3.0.190.0~svn20090619r18817/build-tree/src/app/gfx/font_skia.cc(90)] Check failed: tf. Could not find font: Bitstream Vera Sans
Trace/breakpoint trap

The fonts are definitely installed.

Does anyone have any ideas?

If it makes any difference I'm running compiz.

Thanks.

---

### Post by Derek3x on 2009-08-06
If you change your application font to something else it will load.  It's a bug, and I have the same problem.

---

### Post by fragos on 2009-08-06
Chromium works for me with the Dejavu fonts selected in Options.

---

