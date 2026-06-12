---
title: "Installing RealPlayer, what libstdc++ do I need?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by erik-the-red on 2005-11-10
I have downloaded the RealPlayer binary for Linux from real.

What libstdc++ do I need from aptitude?

The error was libstdc++.so.5 cannot open shared object file.

---

### Post by RAOF on 2005-11-10
libstdc++5

> libstdc++.so.5 cannot open shared object file.
The number after the .so is the major version of the library, so if something is after libfoo.x.y.z, it's after libfoo, version x, minor version y, revision z, and you should search synaptic for libfoo version x.

---

