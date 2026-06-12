---
title: "apt-source and ld problems"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Remmelas on 2005-11-17
Compiling packages via apt-build and compiling fails with the following error message

collect2: cannot find 'ld'

thoughts?

---

### Post by harrison3001 on 2005-11-28
Hi,
i've had the same problem:
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++

I hope you win !

Andrea

---

### Post by Remmelas on 2005-11-30
Thanks, seems to work so long as i do this in a root shell, but after it installs whatever package it seems to segfault... seems to be doing it's job, just segfaulting on exit... wierd.

---

