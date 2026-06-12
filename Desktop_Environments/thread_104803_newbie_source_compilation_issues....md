---
title: "newbie source compilation issues..."
date: 2005-12-16
forum: Desktop Environments
---

### Post by dylanknightrogers on 2005-12-16
hi everyone.  i just installed build-essential and gcc 3.4 from Synaptic, downloaded and installed the GNOME Power Manager from GNOMEFiles.org and tried to compile it  i did ./configure.  At the end of everything (it was not successful, mind you), I got the following message:

checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.6.0 gobject-2.0) were not met:

Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

What do I do to compile correctly?  Thanks.

---

### Post by HermanAB on 2005-12-16
Well, as you are finding, in order to compile some random package, you usually have to install a few libraries, which means visiting the library web sites, get the latest copy and compile and install that.  

However, the said library may depend on something else...  it is an iterative process.  Eventually, things should start to unwind and you can finally compile the package you really want to install.

Here is some general purpose help:
[http://www.aerospacesoftware.com/compile-howto.html](http://www.aerospacesoftware.com/compile-howto.html)

Cheers,

Herman

---

