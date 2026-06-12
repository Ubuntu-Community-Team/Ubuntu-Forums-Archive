---
title: "gdesklets does not load"
date: 2004-12-03
forum: Desktop Environments
---

### Post by beeldings on 2004-12-03
I installed gdesklets and gdesklets-dats using apt-get, but gdesklets does not run:

```

$ spikentm@ubuntu: gdesklets
$ gDesklets 0.26.2
$ Copyright (C) 2003, 2004 The gDesklets Team

$ This software is licensed under the terms of GNU GPL.

$ /usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning:
$ gtk.mainloop is deprecated, use gtk.main instead
$ /usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning:
$ gtk.mainquit is deprecated, use gtk.main_quit instead
$ self_warn(message, DeprecationWarning)

```

So, any ideas why this is happening?

---

### Post by Jspired on 2004-12-03
You may want to try during a search for dgesklets.  This has been talked about quite a bit and many have posted ideas and suggestions.

---

### Post by beeldings on 2004-12-03
I upgraded gdesklets and gdesklets-data to the latest releases from Hoary, and everything works.

---

