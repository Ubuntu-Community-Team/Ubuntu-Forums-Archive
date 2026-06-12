---
title: "xorg cpu always 10-30%"
date: 2010-11-24
forum: Desktop Environments
---

### Post by vsespb on 2010-11-24
Hello.

After removing KDE and installing GNOME I found that it's slower than KDE + CPU usage of XOrg is ~ 10% when idle, and 30% when doing something.

How to fix that or find a reason ?

CPU is core2quad 8200, 8Gb ram.
KDE's xorg CPU usage was ~ 3 times less.

---

### Post by vsespb on 2010-11-26
btw 10-30 % means CPU 50%-100% of one CORE
how to fix debug that ?

---

### Post by sikander3786 on 2010-11-26
Gnome System Monitor uses up a bit of resources itself for all those graphical stuff. Run **top** in a terminal and see how much process xorg is using.

```
top
```

If it is still more than it should be, we need to know more about your graphics card, graphics drivers and RAM.

And which version of Ubuntu is this?

---

### Post by vsespb on 2010-11-26
Thank you for reply !

Of course I was using "top". As Gnome System Monitor uses 100% cpu (or less if increase delay between refresh)


Ubuntu 10.04 Linux  2.6.32-26-generic

nvidia 9400 GT, nvidia driver 173.14.22 (installed with apt-get install nvidia-173)

Core 2 Quad 8200, 8Gb RAM DDR-II

Compositing manager enabled. However if I disable desktop effects and disable compositing CPU usage is still high (maybe just a bit lower)

---

### Post by vsespb on 2010-11-26
Fixed!

Problem was that when I boot with ACPI disabled in BIOS linux x64 thinks that there is only one CPU core (i found that it's known issue) ! 

And I disabled ACPI trying to fix my videocard problem.

Sorry - my fault !

---

