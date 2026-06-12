---
title: "image magick dps support"
date: 2005-12-10
forum: General Help
---

### Post by wouterla on 2005-12-10
Hi,

I'm running into some problems with ImageMagick. It seems to have been built with dps (display postscript) support, which doesn't seem to be available anymore in the new X versions.
Which means that I'm getting the following error:

```
error while loading shared libraries: libdpstk.so.1: cannot open shared object file: No such file or directory
```

compiling ImageMagick with '--without-dps' should fix this (the compile is still running...) 

Wouter

---

