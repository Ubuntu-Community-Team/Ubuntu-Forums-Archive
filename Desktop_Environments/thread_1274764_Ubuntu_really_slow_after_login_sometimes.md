---
title: "Ubuntu really slow after login sometimes"
date: 2009-09-24
forum: Desktop Environments
---

### Post by mfernando on 2009-09-24
**Problem**
Sometimes after I login to Ubuntu the system responds very slowly. Not all of the system tray icons load up either. Even the icons in the applications menu take about 10 seconds to appear. The system is so slow it is unusable. I have to shut down then restart the system. And try again.

**Frequency**
This happens about 30% of the time. The rest of the time everything boots up properly, and the system responds very quickly.

I tried to Google this problem but was unable to find anything like it.

[B]My System
[/B]Ubuntu 9.04
Gnome 2.26.1
Kernel 2.6.28-15
CPU AMD Turion 64 X2 TL-56
RAM 3824 MiB
Video NVIDIA GeForce Go 6150

Has anyone encountered this problem? Does anyone know how to fix this?

---

### Post by tuxxy on 2009-09-24
Maybe its just your startup apps loading like compiz, docks, sys monitors etc I know compiz can take a few seconds on its own.

---

### Post by earthpigg on 2009-09-24
> **tuxxy said:**
> Maybe its just your startup apps loading like compiz, docks, sys monitors etc I know compiz can take a few seconds on its own.

+1

system -> admin -> startup applications

start disabling things that you have added one or two at a time. log out and back in to test.

if the problem persists, what you disabled was not it. re-enable it, disable another, log out and back in.

do the same with panel applets, widgets, etc etc

---

