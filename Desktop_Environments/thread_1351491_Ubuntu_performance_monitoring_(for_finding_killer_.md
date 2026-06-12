---
title: "Ubuntu performance monitoring (for finding killer threads)"
date: 2009-12-10
forum: Desktop Environments
---

### Post by mewrei on 2009-12-10
Is there a way to profile running daemons and threads?

I'm having an issue where for some reason, my load count will SKYROCKET (going up to at least a 5 on a dual core machine but will sometimes go as high as 15) and causes every running desktop application to freeze.

If possible I'd like to search through all of these threads and see if I can find what's creating the bottleneck.

---

### Post by akashiraffee on 2009-12-10
> **mewrei said:**
> 
I'm having an issue where for some reason, my load count will SKYROCKET (going up to at least a 5 on a dual core machine but will sometimes go as high as 15)

What meanest thou by "load count"?

---

### Post by mewrei on 2009-12-10
Load Average

---

### Post by akashiraffee on 2009-12-10
> **mewrei said:**
> Load Average

Okay.  I've never had noticeable problems with this,  unless it was when the immediate processor usage was a distraction.

Which does isolating processes on the basis of CPU time or activity help?

---

### Post by mewrei on 2009-12-10
> **akashiraffee said:**
> Okay.  I've never had noticeable problems with this,  unless it was when the immediate processor usage was a distraction.

Which does isolating processes on the basis of CPU time or activity help?

Mostly in figuring out what the issue is.  Right now I'm suspecting of OpenSSL which is the common application between the applications that freeze.

---

