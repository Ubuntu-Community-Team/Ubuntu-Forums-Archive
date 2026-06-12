---
title: "Update manager and gnome-app-install problems"
date: 2006-03-14
forum: Desktop Environments
---

### Post by Jay_Dogg on 2006-03-14
Neither of these programs start when I click their icons and when I try to start these programs via terminal I get the following messages:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in ?
    import gtk
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode

and

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 20, in ?
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 20, in ?
    import gtk
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode

Any ideas? Synaptic works fine.

---

