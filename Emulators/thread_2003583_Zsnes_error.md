---
title: "Zsnes error"
date: 2012-06-14
forum: Emulators
---

### Post by jkrx on 2012-06-14
Sorry if this has been posted before, I didnt find a thread about it tho. When I try to run Zsnes I get this error. Do somebody know whats wrong and how to fix it? 

Kubuntu 12.04

> zsnes: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

---

### Post by Perfect Storm on 2012-06-14
Thread moved to Emulator forum.


The error means that the libGL is the wrong arch. Typical on 64-bit system and you want to run a 32-bit application. Install 32-bit libs will fix your problem.

---

### Post by jkrx on 2012-06-14
> **Artificial Intelligence said:**
> Thread moved to Emulator forum.


The error means that the libGL is the wrong arch. Typical on 64-bit system and you want to run a 32-bit application. Install 32-bit libs will fix your problem.

oh thank you :) sorry for putting the thread in the wrong place

still get the same error tho.. istalled ia32-libs

nevermind: downloaded snes9x instead and it seems to work :) Thanks for help tho.

---

