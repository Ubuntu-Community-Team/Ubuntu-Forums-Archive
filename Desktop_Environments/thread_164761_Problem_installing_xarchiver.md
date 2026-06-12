---
title: "Problem installing xarchiver"
date: 2006-04-23
forum: Desktop Environments
---

### Post by (S)aint on 2006-04-23
I'm on Xfce4 and wanted a gtk based archive manager
so when i did a ./configure --prefix=/usr for Xarchiver
this is what i get
```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

now its not possible that ubuntu doesn't have gtk... but the gtk...pc file is not present in the pkg config file....:confused: 
help

---

### Post by croak77 on 2006-04-23
Dou you have libgtk2.0-dev installed?

---

### Post by (S)aint on 2006-04-23
well i didnt have libgtk2.0-dev, i did install it...and everything went fine in the installation

Thanks....a lot

---

