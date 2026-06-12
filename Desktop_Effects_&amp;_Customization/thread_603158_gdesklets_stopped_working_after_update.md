---
title: "gdesklets stopped working after update"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by henjenagin on 2007-11-04
Everything was working great. I had the starterbar, cpu monitor, goodweather, ram monitor, all configured just the way I liked it, then the update icon flashed in the top panel and I ran the system through the update. I clicked on the view details button and noticed that it removed one package and installed six. I restarted my session for whatever reason and the gdesklet daemon showed nothing but an empty shell. This is the log:

```
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version mismatch for module tiling: This Python has API version 1013, module tiling has version 1012.
  module = _old_imp(name, globs, locls, fromlist)
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version mismatch for module x11: This Python has API version 1013, module x11 has version 1012.
  module = _old_imp(name, globs, locls, fromlist)
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version mismatch for module systray: This Python has API version 1013, module systray has version 1012.
  module = _old_imp(name, globs, locls, fromlist)
/usr/lib/gdesklets/gdesklets-daemon:119: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: Warning: instance with invalid (NULL) class pointer
  module = _old_imp(name, globs, locls, fromlist)
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  module = _old_imp(name, globs, locls, fromlist)
```

Can anyone help?

Next round of updates installed some libs and now thy are working again.

---

### Post by quicksilver1024 on 2008-02-02
I have the same problem :(

---

### Post by punkybouy on 2008-02-02
Ditto for me.  I just updated today to Gutsy and gdesklets now disappear after a few minutes.

---

### Post by punkybouy on 2008-02-02
Ok, this is wierd.  If I click the button at the bottom left which hides all windows and shows the desktop they all come back.  Click it again and they all come back.  A bug???

---

