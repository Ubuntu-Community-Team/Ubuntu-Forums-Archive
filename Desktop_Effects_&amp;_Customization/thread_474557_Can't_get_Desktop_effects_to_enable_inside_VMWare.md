---
title: "Can't get Desktop effects to enable inside VMWare"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by applegrew on 2007-06-15
I installed Ubuntu Fiesty inside VMWare on my Windows XP Home. I tried starting Desktop Effects but as soon as I click enable Desktop Effects X server restarts and I am brought back to  login window. When I login I find it is still not enabled.

What's going on? and from where can I see the log what went wrong since I get no error messages?

---

### Post by eentonig on 2007-06-15
I think this is quite normal. Vmware does not support the graphical powers of 3D rendering that well.

---

### Post by AndyCooll on 2007-06-15
That might be because VMware doesn't use your graphics card settings. It uses it's own "built-in" bog-standard graphics card drivers.

:cool:

---

### Post by applegrew on 2007-06-15
That means I will have to setup dual boot system?

---

### Post by tanelt on 2007-06-15
Yes, but if you have an ATI graphics card like I do, it will most likely not work. It's a piece of cake to install Beryl, though.

---

### Post by applegrew on 2007-06-15
> **tanelt said:**
> Yes, but if you have an ATI graphics card like I do, it will most likely not work. It's a piece of cake to install Beryl, though.
I have NVidia Geforce Go 7400

---

### Post by tanelt on 2007-06-15
Lucky you. The support for nVidia cards is 10 times better than it is for ATI cards.

It should work straight out of the box without any problems at all.

---

