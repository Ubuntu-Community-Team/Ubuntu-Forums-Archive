---
title: "[SOLVED] Non-existant package not found when compiling AWN."
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by sci-fi guy on 2007-10-19
I am getting an error when I try to run ./configure to compile avant-window-navigator:```
checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.8.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
If I understand this right, it is saying it cannot find pygtk-2.0. But the repositories don't have pygtk. They have python-gtk2.

---

### Post by hexion on 2007-11-07
Install python-gtk2-dev

---

