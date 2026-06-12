---
title: "Install/pkg-config help"
date: 2005-11-29
forum: Desktop Environments
---

### Post by painreliever on 2005-11-29
Hey,

I've been trying for about 2 hours to install Neutrino 0.8.4 so that I can transfer files to my MP3 player, and when I run ./configure, it keeps throwing up errors. The earlier ones were because I didn't have certain programs or modules it needed, but I've got  all those and now it says:

"checking for GNOME... configure: error: Package requirements (libgnome-2.0 >= 1.102.0                            libgnomeui-2.0 >= 1.102.0 gthread-2.0 >= 1.3.7                                     gtk+-2.0 >= 2.6.0 libxml-2.0 >= 2.4.3                                      libglade-2.0 >= 1.99.2 gconf-2.0 >= 1.1.1                                       gdk-pixbuf-2.0 >= 1.3.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GNOME_CFLAGS and GNOME_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details."

Just wondered if anyone knew how to get past this, or how to set the environment variables to 'disable' pkg-config ...

I'm at my wits end here!

Cheers

---

### Post by RAOF on 2005-11-29
You should make sure you have the -dev packages for those libs.  For example, libgtk2.0-dev is the package you want to satisfy the gtk+2.0 > 2.6.0 dependency.  These should set up the pkg-config when they're installed.

---

