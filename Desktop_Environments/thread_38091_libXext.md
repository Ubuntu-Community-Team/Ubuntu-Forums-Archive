---
title: "libXext?"
date: 2005-05-29
forum: Desktop Environments
---

### Post by Nego on 2005-05-29
While trying to install taskbarv2 for kde, I run into this problem:

configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.

I installed libXext and the dev package with kynaptic, but it still gives me the same error. Anyone know how I can fix this?

---

### Post by AnythingBut on 2005-08-15
The libXext test fails if libX11.a is absent.  Try install the dev package of libX11 as well.

---

