---
title: "CD-HIT and multithreading"
date: 2010-08-12
forum: Education &amp; Science
---

### Post by Rohan on 2010-08-12
Hi, 
Has anyone here have CD-HIT running and gotten multithreading to work? Can't seem to get any from the developer and I'm stuck using only one of four cores.

Rohan

---

### Post by hvbakel on 2010-11-12
I actually ran into the same problem. cd-hit compiles just fine with the openmp=yes option, but only uses a single thread no matter how I start it. Have you by any chance made any progress with this?

---

### Post by max127 on 2010-11-14
I am suffering the same problem like cd-hit compiles please tel how to solve it.

---

### Post by Rohan on 2010-11-17
Hi guys,
I just noticed you're replies and I have gotten to work under 10.04 using multithreading. There's an updated codebase that should work >> [http://code.google.com/p/cdhit/](http://code.google.com/p/cdhit/)

Rohan

---

### Post by jeenamenon on 2010-11-25
As far as I know it sounds like the operating system, the passage of the wires is usually cheaper than the transition between jobs. This is because the memory management information is not changed during the thread, only a stack and register set to do, which means less data to copy the context switches.

---

