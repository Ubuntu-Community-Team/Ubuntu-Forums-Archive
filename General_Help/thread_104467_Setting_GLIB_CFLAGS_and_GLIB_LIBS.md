---
title: "Setting GLIB_CFLAGS and GLIB_LIBS"
date: 2005-12-16
forum: General Help
---

### Post by Blackie_Chan on 2005-12-16
I am in the process of installing workrave 1.8.1 from source, but when I try to configure the package. I get:

[HTML]...
checking for GLIB... configure: error: Package requirements (glib-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GLIB_CFLAGS and GLIB_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.[/HTML]

How can I set the variables? Where is GLIB_CFLAGS and GLIB_LIBS so I can set it using the 'export' command?

Thanks in advance

---

### Post by ranf on 2005-12-16
Most likely you will only have to install `libglib2.0-dev'.

---

### Post by Blackie_Chan on 2005-12-17
[QUOTE=ranf]Most likely you will only have to install `libglib2.0-dev'.[/QUOTE]
That didn't solve my problem.

---

