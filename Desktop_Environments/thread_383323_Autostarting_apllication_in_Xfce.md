---
title: "Autostarting apllication in Xfce"
date: 2007-03-13
forum: Desktop Environments
---

### Post by TheForkOfJustice on 2007-03-13
I'm trying to get Tilda to start every time I start a new session and without clicking it in the menu.

How do I do this?

---

### Post by kerry_s on 2007-03-13
Menu>settings>autostart app

---

### Post by rudiz on 2007-03-13
And in Feisty Kubuntu ? How do you do this?

---

### Post by kerry_s on 2007-03-13
In kde/kubuntu you have to do it manually.

kwrite ~/.kde/autostart/tilda
put

#!/bin/sh
exec tilda &

make it executable

chmod +x ~/.kde/autostart/tilda

---

