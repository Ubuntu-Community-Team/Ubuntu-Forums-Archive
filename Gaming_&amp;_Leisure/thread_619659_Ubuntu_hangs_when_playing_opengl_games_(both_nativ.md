---
title: "Ubuntu hangs when playing opengl games (both native and wine)"
date: 2007-11-21
forum: Gaming &amp; Leisure
---

### Post by silfer on 2007-11-21
Hi!
Im using ubuntu 7.10 gutsy gibbon (32 bit), my specs are: 
Abit kn9 (i think) motherboard
AMD Athlon 4200+
ATI x1950 pro 256mb pci-xpress

the problem are following:
when i play opengl games such as neverwinter nights 1 (native) or counterstrike with wine the computer hangs after a while, it is not the app itself but the whole system (i have tried ctrl+alt+backspace)... i have tried to install the drivers with envy and from ati website... can anyone help me? it would be really nice

---

### Post by aoanla on 2007-11-21
Which drivers are you using?
The OpenGL render path used in the 8.41, 8.42 and new Catalyst 7.11 fglrx drivers for R500 GPUs (including the X1950 Pro) is known to have a severe memory leak, which can consume up to a 1Gb of memory in less than an hour. 
It is quite possible that using these drivers would cause precisely your problem. Unfortunately, ATI's monthly driver release process means that (since the problem isn't fixed in the new driver released today), it will be some time in December, at the earliest, that you can expect a fix.

---

### Post by silfer on 2007-11-21
im using 8.42.3, is it possible that older drivers work better? im going to test the driver realesed today and se if it works better. thank you for taking the time...

---

