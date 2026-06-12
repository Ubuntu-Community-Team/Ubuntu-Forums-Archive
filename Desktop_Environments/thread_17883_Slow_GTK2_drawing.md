---
title: "Slow GTK2 drawing"
date: 2005-03-03
forum: Desktop Environments
---

### Post by Cossins on 2005-03-03
Hi!
I just installed Ubuntu (Hoary). Coming from Gentoo, I'm quite happy with the system, it seems to be working well. But there is one thing that annoys me terribly. GTK2 is horribly slow. I can see the menus draw themselves before my eyes, and it's the same with practically every widget. gnome-terminal is also painfully slow when scrolling.

I'm using the latest NVIDIA driver, RenderAccel is turned on, so is the Composite extension.

Tips?

- Simon

---

### Post by p!=f on 2005-03-03
What's top saying? Any resource hungry process there?
Try to comment composite extension and restart X.

---

### Post by HungSquirrel on 2005-03-03
Seems others are having the same problem.

[http://ubuntuforums.org/showthread.php?t=17701](http://ubuntuforums.org/showthread.php?t=17701)

---

### Post by Cossins on 2005-03-03
[QUOTE=p!=f]What's top saying? Any resource hungry process there?
Try to comment composite extension and restart X.[/QUOTE]
 top, when widgets are redrawing, reports heavy activity with the Xorg process.

- Simon

---

### Post by p!=f on 2005-03-03
[QUOTE=Cossins]top, when widgets are redrawing, reports heavy activity with the Xorg process.

- Simon[/QUOTE]
Do you have gnome-terminal running?

---

