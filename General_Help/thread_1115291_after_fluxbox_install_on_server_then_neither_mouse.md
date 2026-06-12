---
title: "after fluxbox install on server then neither mouse nor keyboard work"
date: 2009-04-03
forum: General Help
---

### Post by linuxnovicefan on 2009-04-03
title says it all.....I have a ps2 keyboard which worked fine when there was no gui for the 8.10 server....and a usb logitech optical mouse - after booting the fluxbox gui using startx then neither the mouse nor the keyboard work........what the heck is happening here ?!

---

### Post by kerry_s on 2009-04-03
it seems now you need "hal" before you startx.
sudo apt-get install hal

---

### Post by linuxnovicefan on 2009-04-03
> **kerry_s said:**
> it seems now you need "hal" before you startx.
sudo apt-get install hal

solved my problem thanks !:popcorn:

---

