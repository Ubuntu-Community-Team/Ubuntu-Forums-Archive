---
title: "BMPx 0.20pre1 wants gstreamer0.10-plugins-base"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Kimm on 2006-06-19
Well... what the title says.

I'm trying to build BMPx 0.20pre1, but it complains that gstreamer0.10-plugins-base is missing, when it is, in fact, not.

I cant seem to find any developement packages for it eighter... (and yes, I have the correct version)

checking for LIBNOTIFY... yes
checking for GST... yes
checking for **GST_PLUGINS_BASE... configure: error: Package requirements (gstreamer-plugins-base-0.10 >= 0.10.7) were not met.**
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GST_PLUGINS_BASE_CFLAGS and GST_PLUGINS_BASE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

Any help apretiated...

---

### Post by flargen on 2006-06-19
Have you got libgstreamer0.10-dev installed?

---

