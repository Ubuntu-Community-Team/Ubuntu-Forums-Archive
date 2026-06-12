---
title: "Cedega Help"
date: 2006-04-27
forum: Gaming &amp; Leisure
---

### Post by sunrex on 2006-04-27
(Point2Play_gui.py:8796): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/local/games/transgaming_cedega_timedemo/usr/lib/transgaming_cedega_timedemo/Point2Play_gui.py", line 40, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/local/games/transgaming_cedega_timedemo/usr/lib/transgaming_cedega_timedemo/lib/python2.3/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: locale setting not supported


any ideas? i was having issues with LANG=en_US before i fixed that.. this was working fine yesterday

---

### Post by croak77 on 2006-04-28
What is set in  /etc/environment? Mine is:

LANG="en_US.UTF-8"
LANGUAGE="en_US:en_GB:en"

---

