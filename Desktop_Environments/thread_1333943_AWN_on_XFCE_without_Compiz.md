---
title: "AWN on XFCE without Compiz??"
date: 2009-11-21
forum: Desktop Environments
---

### Post by Cammy on 2009-11-21
I recently installed Xubunto Jaunty on my laptop, and have been really happy with it so far.  One of the things I wanted to install was Avant Window Navigator (AWN) because I've gotten used to it on my main desktop PC.

When I installed AWN, it told me I needed a composited window manager, like Compiz.  Since this is an old, low-end laptop (Dell Inspiron 5100), I don't really want to install Compiz because I think it'll drag things down.  Besides, the AWN Wiki entry claims that XFCE is already composited.

Is there any way to get AWN to run on XFCE without Compiz?

---

### Post by Cammy on 2009-11-22
Figured it out.  When I uinstalled Compiz, it somehow remained selected as the default window decorator, so all the xfwm4 stuff for enabling compositing wasn't available.

I ended up doing: xfwm4 --replace and getting the proper decorator back, which allowed me to enable compositing.

---

