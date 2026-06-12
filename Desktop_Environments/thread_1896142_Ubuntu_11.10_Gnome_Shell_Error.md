---
title: "Ubuntu 11.10 Gnome Shell Error"
date: 2011-12-16
forum: Desktop Environments
---

### Post by rak_freak on 2011-12-16
Hi, 

I have a DELL 1510 Studio Laptop with ATI Radeon graphic card. Its running on Ubuntu 11.10. 

However, when I try to load gnome-shell --replace. Following error is thrown. 

I have removed fglrx driver and  installed open source ATI driver. 

Error Log 


 gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Failed to throw exception 'Object 0xad7065b0 proto 0xad702078 doesn't have a dynamically-registered class, it has DD	´'
    JS ERROR: !!!     lineNumber = '243'
    JS ERROR: !!!     fileName = '"/usr/share/gjs-1.0/overrides/GLib.js"'
    JS ERROR: !!!     stack = '"_init()@/usr/share/gjs-1.0/overrides/GLib.js:243
@/usr/share/gnome-shell/js/ui/environment.js:3
"'
    JS ERROR: !!!     message = '"  'Object 0xad7065b0 proto 0xad702078 doesn't have a dynamically-registered class, it has D	D	´'"'
Can't init class Variant

Aborted



Any help is highly appreciated.

---

### Post by GalmWing on 2012-02-18
That is just exactly the same that happends to me.

And I have removed, purged, installed, reinstalled the open source driver so many times ...

A simple purge of fglrx and a reinstall of the open drivers was usually all that was needed, but now I stuck with this same error.

---

