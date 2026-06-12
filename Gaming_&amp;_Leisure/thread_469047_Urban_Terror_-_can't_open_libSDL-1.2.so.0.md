---
title: "Urban Terror - can't open libSDL-1.2.so.0"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by hocmin on 2007-06-09
I've got got the latest version of Ubuntu on an AMD64 processor system.  After installing and extracting ioUrbanTerror and UrbanTerror I try to run ioUrbanTerror.i386 and get the following error:

> ./ioUrbanTerror.i386: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I've checked my system through Synaptic and I have libsdl1.2debian and libsdl1.2debian-alsa installed.  I've got an NVIDIA video card and I'm pretty sure I followed the binary driver instructions properly (if anyone can tell me how to check this, that'd be great).

How can I fix this?

Thanks.

---

### Post by noerrorsfound on 2007-06-09
(well that was unhelpful)

---

### Post by Cappy on 2007-06-09
Run this:
```

sudo apt-get install ia32-libs* lib32asound2

```

The problem is that i386 games need i386 libraries. A similar error to this is "WRONG ELF CLASS: ELFCLASS64 or something.

---

### Post by hocmin on 2007-06-10
That worked perfectly.  Thanks.

---

