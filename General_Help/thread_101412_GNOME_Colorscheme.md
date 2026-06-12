---
title: "GNOME Colorscheme"
date: 2005-12-09
forum: General Help
---

### Post by l.tambiah on 2005-12-09
I am trying to install [GNOME Colorscheme]("http://home.gna.org/colorscheme/") application from source as it doesn't exist in the repos. 

The compiler error i get can be shown below:

```

checking for COLORSCHEME... configure: error: Package requirements (
                                gtkmm-2.4 >= 2.6.0
                                libgnomeui-2.0 >= 2.0.0
                                gnome-vfsmm-2.6
                                ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the COLORSCHEME_CFLAGS and COLORSCHEME_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

``` 

Does anyone know how i could make this compile successfully?

---

### Post by l.tambiah on 2006-02-19
The issue has been resolved by installing the required dependencies asked for on the compile. See this thread:-
[http://www.ubuntuforums.org/showthread.php?t=118424&highlight=GNOME+Colorscheme]("http://www.ubuntuforums.org/showthread.php?t=118424&highlight=GNOME+Colorscheme")

---

