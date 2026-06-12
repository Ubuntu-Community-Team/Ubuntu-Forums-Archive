---
title: "Glib Anoying problem"
date: 2006-01-12
forum: General Help
---

### Post by vbmaster on 2006-01-12
I already made a search, and tried all the solutions given. But I'm still having this problem when I'm configuring something:

```

checking for GLIB - version >= 2.0.3...
*** 'pkg-config --modversion glib-2.0' returned 2.9.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: "Cannot find glib"

```


And I have all this packages installed:

```

libglib2.0-0 - The GLib library of C routines
libglib2.0-data - Common files for GLib library
libglib-perl
libglib1.2 - The GLib library of C routines
libglib1.2-dev - Development files for GLib library
libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-dev - Development files for the GLib library

```

With this problem I can't configure sucessfuly almost nothing, and I get errors in "dpkg -i" too, that I know that came from the glib.

I need urgent help. :'(

Thanks to all.

---

