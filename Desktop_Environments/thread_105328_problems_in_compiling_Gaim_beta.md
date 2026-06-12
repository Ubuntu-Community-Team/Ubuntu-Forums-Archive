---
title: "problems in compiling Gaim beta"
date: 2005-12-18
forum: Desktop Environments
---

### Post by var on 2005-12-18
Hi all,

I've just downloaded this file and now I must compile it.
when I type ./compile I obtain this error:

```
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.configure: error:
*** GTK+ 2.0 is required to build Gaim; please make sure you have the GTK+
*** development headers installed. The latest version of GTK+ is
*** always available at http://www.gtk.org/.
```

how can I fix it?
thanks. :)

---

### Post by Peter76 on 2005-12-18
You need to install the GTK-dev files ( and probably the dev files for all the libraries Gaim needs... ). Chevk in synaptic under gtk for gtk-dev and install that. Also install pkgconfig ( if not part of build-essential ). Good luck

---

### Post by var on 2005-12-18
[QUOTE=Peter76]You need to install the GTK-dev files ( and probably the dev files for all the libraries Gaim needs... ). Chevk in synaptic under gtk for gtk-dev and install that. Also install pkgconfig ( if not part of build-essential ). Good luck[/QUOTE]

thank you, I've just compiled successfully. :)

---

