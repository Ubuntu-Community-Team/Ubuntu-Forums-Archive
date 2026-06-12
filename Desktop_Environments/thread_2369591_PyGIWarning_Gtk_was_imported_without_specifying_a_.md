---
title: "PyGIWarning: Gtk was imported without specifying a version first"
date: 2017-08-24
forum: Desktop Environments
---

### Post by 7-webmaster on 2017-08-24
I do not understand the following message:

PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk

---

### Post by jbicha on 2017-08-24
It's just a harmless warning. It's more of a message to whoever developed the app that they need to change their code in preparation for future library releases (like gtk4).

Most of those warnings have been cleaned up in the releases after Ubuntu 16.04 LTS.

---

