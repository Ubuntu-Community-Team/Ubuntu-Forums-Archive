---
title: "frets on fire crash"
date: 2007-02-14
forum: Gaming &amp; Leisure
---

### Post by hellfeuer on 2007-02-14
Hey

I downloaded [Frets on Fire]("http://www.fretsonfire.net/"), unfortunately it crashes.. 
The game looks like its about to start, i.e. the screen goes black (fullscreen), but then it crashes..
here's the error i get:
```
libGL warning: 3D driver claims to not support visual 0x5b
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted (core dumped)
```

This happens if i execute the FretsOnFire file, which is basicaly this shell script:
```
#!/bin/sh
export LD_LIBRARY_PATH=$(dirname $0)
exec ./FretsOnFire.bin $@
```

If I run ./FretsOnFire.bin $@ i get the same crash

how do i fix this? I have an intel 915gm..

thnx

---

### Post by thoughtcriminall on 2007-02-22
I have the exact same problem. Same card and everything.

---

### Post by wakingrufus on 2007-03-11
same here :-/

---

### Post by hikaricore on 2007-03-12
FoF always seg faulted on my intel card.  It runs on my nvidia card just fine on the same system.  I'm guessing this is an issue with the intel driver.

---

### Post by llc1985 on 2007-03-17
If you install the Python-pygame package it will fix that problem.

---

### Post by shaolinchamp on 2009-01-02
> **llc1985 said:**
> If you install the Python-pygame package it will fix that problem.

yea i have th python package installed and its still crashing for me

im using ubuntu 8.04 64 bit

---

### Post by efexD on 2009-01-03
Same here ](*,)

---

