---
title: "compiz problems with i965"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by jhs_s on 2007-07-18
Hi!

I tried to follow the howto which is sticky on the top. Installation went smooth and I also installed the latest intel-backport driver to feisty.

Anyway, I always get the following error message:

```
/usr/bin/compiz.real: Unknown option '--no-fbo'
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0

```

glxinfo reports direct rendering and reports the GLX_EXT_texture_from_pixmap is availible. Not even someone a GUADEC could help me by know so I am asking here.

I also tried several options in xorg.conf files but they really don't make any difference.

Thanks and regards,
Johannes

---

