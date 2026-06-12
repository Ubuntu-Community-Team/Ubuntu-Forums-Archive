---
title: "Apricots Compile"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by 3dmaker on 2005-10-27
I have all packages to compile this game called Apricots. But I get this error.

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables

What should I do to make it work? Any ideas? It worked on Fedora Core 4

---

### Post by Xian on 2005-10-27
1. Make sure you have binutils installed.
2. Set the CC vble

# export CC=gcc

---

