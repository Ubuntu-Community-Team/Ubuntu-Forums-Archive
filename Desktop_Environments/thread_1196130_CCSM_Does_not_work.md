---
title: "CCSM Does not work"
date: 2009-06-24
forum: Desktop Environments
---

### Post by Bart B on 2009-06-24
When i try starting it, i get:


(process:5224): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
bart@bart-desktop:~$

---

### Post by Bart B on 2009-06-24
Problem solved with adding

export LC_ALL=C

to .profile

---

### Post by theabraxas on 2010-08-08
Thanks friend, this worked for me too..

---

