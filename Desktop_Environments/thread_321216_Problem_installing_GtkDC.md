---
title: "Problem installing GtkDC"
date: 2006-12-18
forum: Desktop Environments
---

### Post by k3rmit on 2006-12-18
Hi,
I'm having a problem with compiling the GtkDC. When i run ./configure i get this error
```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8 gobject-2.0 gdk-x11-2.0 glib-2.0 gdk-pixbuf-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gdk-x11-2.0' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

However I cannot find anywhere the required packages, gtk+-2.0, gdk-x11-2.0, gdk-pixbuf-2.0, that is.
I also tried installing numerous weird *-dev packages with hope that they will help.

---

