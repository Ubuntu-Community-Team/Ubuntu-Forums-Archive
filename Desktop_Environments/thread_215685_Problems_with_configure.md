---
title: "Problems with configure"
date: 2006-07-14
forum: Desktop Environments
---

### Post by albinoloverats on 2006-07-14
Recently I tried to build a GTK package with Anjuta, however when it came to compile there was a problem:

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 gdk-2.0) were not met:

Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

Having not knowingly changed anything (maybe a few upgraded packages) I'm not really sure what's happened or how to fix it.

Anybody seen this before?  ](*,)

---

