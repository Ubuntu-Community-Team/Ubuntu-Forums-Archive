---
title: "PCSX help..."
date: 2012-02-22
forum: Emulators
---

### Post by timobis on 2012-02-22
I'm having some problems with PCSX, when I try and run a game that I downloaded off of torrents, the follwing is output by the terminal:


(pcsx:4286): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pcsx:4286): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pcsx:4286): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pcsx:4286): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Tungsten Graphics, Inc
Mesa DRI Intel(R) Sandybridge Mobile 
Segmentation fault


does anyone know what this means?

---

### Post by amodra on 2012-02-28
It indicates a packaging dependency problem somewhere.

sudo apt-get install gtk2-engines-pixbuf

---

