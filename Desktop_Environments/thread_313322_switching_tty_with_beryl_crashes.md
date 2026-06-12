---
title: "switching tty with beryl crashes"
date: 2006-12-05
forum: Desktop Environments
---

### Post by ridetheteapot on 2006-12-05
with beryl running my pc crashes when i switch back to tty7 (ctrl alt + f7) from another one like tty2. the screen goes blank and i get my mouse pointer, thats it. it will usually freeze up, where i cant even mess with caps locks, but sometimes i can get to tty2 and kill beryl, then i can get back onto gnome.

i have beryl running on gnome with the beta nvidia drivers.

---

### Post by Syock on 2007-04-02
Confirmed bug: [http://bugs.beryl-project.org/ticket/1513](http://bugs.beryl-project.org/ticket/1513)

Workaround : Disable sync to vblank in Beryl Settings Manager->General Options
(side-effect: tearing, high-cpu load)

---

