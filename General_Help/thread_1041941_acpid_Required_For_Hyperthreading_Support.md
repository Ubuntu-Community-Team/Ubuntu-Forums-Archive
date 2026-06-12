---
title: "acpid Required For Hyperthreading Support?"
date: 2009-01-17
forum: General Help
---

### Post by adamlau on 2009-01-17
Or is it like Gentoo where the service and daemon is not required for Hyperthreading support.

---

### Post by 3rdalbum on 2009-01-17
I believe Hyperthreading is something the CPU is solely responsible for; it presents each core as being actually 2 cores. Ubuntu will automatically recognise and use as many cores as you've got in your desktop computer, so hyperthreading should be no different.

---

### Post by sdennie on 2009-01-17
The only thing you will need to make sure of is that it's enabled in your BIOS.  The Ubuntu kernel has hyperthreading support.

---

