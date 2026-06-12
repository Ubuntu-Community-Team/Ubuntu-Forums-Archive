---
title: "Geany can't find GCC"
date: 2009-05-10
forum: General Help
---

### Post by brianfast on 2009-05-10
Hello - I am using 64 bit ubuntu - a bit buggy but much better then previous ubuntus...

Anyway I installed geany, but when I give it a valid C++ file and say "compile"... I get "G++ not found"

How do I configure Geany to actually compile stuff?

---

### Post by StuartN on 2009-05-10
> **brianfast said:**
> How do I configure Geany to actually compile stuff?

As far as I know, Geany uses the commands gcc, g++, make etc without any path, so it does not need configuring. My installation just worked as installed. You should have /usr/bin/gcc and /usr/bin/g++ installed and in your path.

If you run gcc / g++ in a terminal, can you compile the same code?

---

