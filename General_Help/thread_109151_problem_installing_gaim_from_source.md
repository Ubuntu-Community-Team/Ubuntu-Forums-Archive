---
title: "problem installing gaim from source"
date: 2005-12-27
forum: General Help
---

### Post by eyebrowman92 on 2005-12-27
im trying to install gaim2.0.0beta1 from source and when i ./configure, i get an error saying "configure: error: no acceptable C compiler found in $PATH
". whats this mean and how do i fix it?

---

### Post by kingsidy on 2005-12-27
install the build essential package from the terminal or from synaptics. on the terminal do > sudo apt-get install build-essential then redo the ./configure

---

### Post by eyebrowman92 on 2005-12-27
alright thanks. problem solved.

---

### Post by eyebrowman92 on 2005-12-27
haha im having some trouble. got past the first part of ./configure then it says i need glib installed. well when i try to get glib from source it says i need gettext. whats going on.

---

### Post by eyebrowman92 on 2005-12-27
anyone...

---

### Post by eyebrowman92 on 2005-12-28
someone please im determined

---

### Post by Zelut on 2005-12-28
I wrote a wiki for this.. give it a try.  [http://wiki.ubuntu.com/CompileGaim](http://wiki.ubuntu.com/CompileGaim)

---

### Post by eyebrowman92 on 2005-12-28
well it was working but then i got this error:

checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.8.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).



how can i fix it? i thought i had glib installed, so how do i remove the old version?

---

### Post by eyebrowman92 on 2005-12-28
someone...i really need help with this.

---

### Post by MighMoS on 2005-12-28
Woah, mate.  You need to calm down.  Do you have the glib-dev and gtk+-dev packages installed?

---

