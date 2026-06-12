---
title: "google earth e SiS630"
date: 2006-07-08
forum: Desktop Environments
---

### Post by perce on 2006-07-08
Hello,

I've just installed googleearth, but unfortunately it crashes immeidately with the error message: 

[sis_alloc.c:210]: Failure to allocate back buffer.

which of course I don't understand. My graphic card is a SiS630 older than five years. It should have 3D acceleration though (but I've never tested it).
Does anybody have an idea?

Perce

---

### Post by erichgamba on 2008-02-12
I had the same error. Increasing the shared memory size from 8MB to 32MB in the BIOS solved the problem for me.

---

