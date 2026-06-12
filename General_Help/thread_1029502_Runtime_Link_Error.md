---
title: "Runtime Link Error"
date: 2009-01-03
forum: General Help
---

### Post by William_in_Kanata on 2009-01-03
Environment

Ubuntu 8.10 64 bit - patched to date.
java version "1.5.0_16"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_16-b02)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_16-b02, mixed mode)

When I try to install dbvisualizer on this machine, I am getting the following error:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.

Doing a find for libXm shows a number of libraries that begin libXm (libXmu, libXmuu, with various version numbers following), but nothing that is just libXm by it self. Should one of these be linked to libXm, and if so which one? May be I am missing an X package, and if so which one?

Thanks to all

---

