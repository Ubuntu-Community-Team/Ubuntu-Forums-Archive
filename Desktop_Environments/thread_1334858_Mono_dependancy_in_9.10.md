---
title: "Mono dependancy in 9.10?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by RX8volution on 2009-11-22
Hello, I'm trying to install a package I very much liked (gnomeartng v0.7) which apparently fails because it's dependent on "mono-common" ... so package manager throws an error "ERROR: Dependency is not satisfiable: mono-common" ...

Does anyone know if there's a way to fix this, or a work-around?

---

### Post by directhex on 2009-11-23
The "correct" solution would be for the package to be fixed to properly track dependencies (you should *never* manually depend on mono-common)

However, you might want to look into the "equivs" package for hints on building a dummy mono-common which doesn't do anything but satisfy the dependency

---

### Post by margazhang on 2009-12-07
How to build a dummy mono-common?

---

