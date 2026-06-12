---
title: "Dual monitors on two different graphics cards."
date: 2009-06-14
forum: General Help
---

### Post by Blackcamaro8 on 2009-06-14
Okay, i am currently using a system that has two graphics cards, one is built-in to the motherboard, and one is aftermarket.  I have the aftermarket graphics card's monitor displaying the words i'm typing right now, and the other one is acting as though there is no signal from anything.  I was wondering if there was something i could do to my xorg.conf file to set it up for two graphics cards.

---

### Post by loomsen on 2009-06-14
Hi.

You may add 
BusID "$BUSID"
to the devices config.

You may find out which card is on which bus using common tools like 
lspci, dmesg, lshw ...

Then simply configure your xorg defining for each device

A device section
A monitor section
A screen section where you join them together.


Template:
```

Device0
BusID

Monitor0

Screen0
  Device0
  Monitor0

Device1
BusID

Monitor1

Screen 1
  Device1
  Monitor1

Serverlayout

Screen0 
Screen1 <alignment relative to Screen0>

```
alignment either such as RightOf, LeftOf, or by pixels

Screen0  (where:) 0 0
Screen1  (where:) X(-resolution of Screen0) Y(-resolution of Screen0)

for instance, if Screen0 is 1024x768 and you wanna place Screen1 to the right of Screen0

Screen0 0 0
Screen1 1024 0

```
man xorg.conf
```

---

