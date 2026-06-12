---
title: "amarokapp libGL.so.1: wrong ELF class: ELFCLASS32"
date: 2009-01-09
forum: General Help
---

### Post by _sluimers_ on 2009-01-09
When I start Amarok I get he following error:

```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32

```

I use Ubuntu 8.10 64-bit.

---

### Post by Yellow Pasque on 2009-01-09
libGL.so.1 is provided by your video driver, so this would be a problem with your video driver. What video card do you have? If you're unsure:
```
sudo update-pciids
lspci | grep VGA
```

---

### Post by _sluimers_ on 2009-01-10
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

---

### Post by _sluimers_ on 2009-01-19
Anyone?

---

