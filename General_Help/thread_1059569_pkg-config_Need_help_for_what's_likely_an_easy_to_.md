---
title: "pkg-config: Need help for what's likely an easy to fix error (glib version problem.)"
date: 2009-02-03
forum: General Help
---

### Post by sstecken on 2009-02-03
SOLVED

*** 'pkg-config --modversion glib-2.0' returned 2.18.4, but GLIB (2.18.2)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

---

