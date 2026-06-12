---
title: "resolution issue"
date: 2009-02-15
forum: General Help
---

### Post by Scrix on 2009-02-15
I just set my screen resolution wayyy too low... i have to go on a guest account just to see anything
anybody know how to fix this?

---

### Post by AlexBellisBrown on 2009-02-15
system-preferences-screen resolution. Perhaps changing it to what it should be in the guest account will fix the others... i dont know, failing that you could try booting a different kernel, or in safe mode. And fix it from there.

---

### Post by AlexBellisBrown on 2009-02-15
Failing that... it gets technical, but i have fixed screen res. this way before, its scary, but dont worry, it works :)

Terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Scrix on 2009-02-15
thanks

---

### Post by Scrix on 2009-02-15
that did work, but my graphics drivers are now disables and i canont use compiz and when i try and enable them it goes to the low resolution

---

### Post by Scrix on 2009-02-16
still looking for help

---

