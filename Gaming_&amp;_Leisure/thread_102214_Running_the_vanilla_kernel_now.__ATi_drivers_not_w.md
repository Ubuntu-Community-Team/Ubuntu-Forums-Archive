---
title: "Running the vanilla kernel now.  ATi drivers not working"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by Kobra on 2005-12-11
Ok, my ATi drivers were working like a charm, then I built the vanilla kernel with the ck performance patch.  Now, whenever I run Quake 3, I get this:
```
***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```
I tried reinstalling the drivers through Synaptic, but to no avail

---

### Post by Kobra on 2005-12-11
Answer if you want, but I've decided it isn't worth it.  I'm deleting the kernel

---

### Post by vruum on 2005-12-11
the fglrx drivers from synaptic are dependant on a kernel module included in the restricted modules, and only work with the standard ubuntu kenel. so the best way to get the drivers to work with a different kernel would be to download the ones from ati.com.

---

