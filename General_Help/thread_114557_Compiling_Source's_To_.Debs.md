---
title: "Compiling Source's To .Debs"
date: 2006-01-08
forum: General Help
---

### Post by Drunken Pirate on 2006-01-08
Is it possible to compile source files into .deb packages? I would like to do this for some applications, for myself, and the community.

---

### Post by 23meg on 2006-01-08
Doing it the proper Debian way is quite complicated; take a look at the Debian new maintainers' guide (it comes in the package maint-guide). An easier way is to use [checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/"), which again is in the repositories, but it's best reserved for personal use except for quick and dirty distributions of simple software that has no dependencies, since debs created with it don't check for dependencies.

---

