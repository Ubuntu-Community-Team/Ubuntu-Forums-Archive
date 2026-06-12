---
title: "Gajim in 9.04"
date: 2009-03-27
forum: General Help
---

### Post by W0T4N on 2009-03-27
Please help gajim does no work, jabbim too. when I type gajim in console : 
laufem@laufem-laptop:~$ gajim
Traceback (most recent call last):
  File "gajim.py", line 157, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8


and when i type  jabbim  : 
laufem@laufem-laptop:~$ jabbim
PyQt4 is not installed.
Traceback (most recent call last):
  File "jabbim.py", line 31, in <module>
    import qt4reactor
  File "/usr/share/jabbim/qt4reactor.py", line 25, in <module>
    from PyQt4.QtCore import QSocketNotifier, QObject, SIGNAL, QTimer
ImportError: /usr/lib/python2.6/dist-packages/PyQt4/QtCore.so: undefined symbol: PyUnicodeUCS4_FromUnicode



Please help

---

