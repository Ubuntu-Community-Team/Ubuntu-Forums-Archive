---
title: "Beryl Settings Manager"
date: 2007-04-01
forum: Desktop Effects &amp; Customization
---

### Post by naerae on 2007-04-01
Hello. The Beryl Setting Manager neither works from Aplications Menu nor from system tray. On terminal, **beryl-settings** command outputs;

> (beryl-settings:6094): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 35, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


Could you help me to solve the problem,please?
Thanks in advance.

---

