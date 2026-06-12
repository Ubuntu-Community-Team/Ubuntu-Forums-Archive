---
title: "[SOLVED] need to install dbus-glib-1"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by Phil420 on 2008-01-08
i want to get kiba-dock but every time I get to one of the last steps, it pops me that dbus-glib-1 package was not found, and was needed.
somebody can tell me where to get it?

```

bla bla bla...
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for PANGO... yes
checking for GTK... yes
checking for CAIRO... yes
checking for LIBXML... yes
checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

phil@Phil-Desktop:~/kiba-dock/kiba-dock$ 

```

thanks!

---

### Post by FuturePilot on 2008-01-08
```
sudo apt-get install libdbus-glib-1-dev
```
And try again. Should do the trick.

---

