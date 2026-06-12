---
title: "burgertime"
date: 2012-08-21
forum: Gaming &amp; Leisure
---

### Post by TNAFan on 2012-08-21
I attempt to launch the game Burgertime from Ubuntu and I recieve the error:

burgerspace: server init error: No available video device

What could be happening here?  How do I fix this?

---

### Post by synaptix on 2012-08-21
What are your system specs and what Ubuntu versionare you running?

---

### Post by TNAFan on 2012-08-21
Running a Dell Inspiron N5050 with Ubuntu 12.04

---

### Post by thatguruguy on 2012-08-21
> **TNAFan said:**
> Running a Dell Inspiron N5050 with Ubuntu 12.04

For the record, those aren't your system specs.

Open a terminal, and type the following:
```
lspci | grep VGA
```
... and that will tell us the video card you have. That would at least give us somewhere to start.

---

### Post by TNAFan on 2012-08-21
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by thatguruguy on 2012-08-21
BTW, where did you find Burgertime for Linux?

---

### Post by MikeCyber on 2012-08-22
I only know of a MAME version. Which is like the real arcade machine...very cool. BT, Donkey Kong, Asteroids deluxe, space invaders etc. all huge fun.

---

### Post by TNAFan on 2012-08-22
Oh sorry, Burgerspace.  In the repositories.

---

### Post by TNAFan on 2012-08-29
Bump

---

