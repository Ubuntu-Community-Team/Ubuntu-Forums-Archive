---
title: "[SOLVED] Module update"
date: 2008-12-28
forum: General Help
---

### Post by kryos on 2008-12-28
I am being offered the "linux-ubuntu-modules-2.6.24.22-generic" through the update notifier.  Under the update description tab it states
"This package contains modules supplied by Ubuntu for Linux kernel 2.6.24 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."
So, should this be installed or???
BTW 8.04/Dell

---

### Post by randallecook on 2008-12-28
I would trust the automatic updater and just apply it, but perhaps someone more experienced could offer insight.

Within the package system there are "meta" packages which have generic names that can be redefined to install (through dependencies) the actual software you need. For example, there are several versions of g++ (a C++ compiler) available, but if you just want "the current one", you can install the g++ meta package and it will work. You don't have to read version numbers and release notes.

The meta packages also form a way of grouping software together so it all gets installed at once. You can of course install the things that the meta packages link to (i.e. depend on) individually, but installing the meta package is easier.

Since this is coming from the automatic updater, I am guessing that the meta package is already installed, and one of its components needs to be updated. This sounds harmless. I say go for it.

Randall

---

