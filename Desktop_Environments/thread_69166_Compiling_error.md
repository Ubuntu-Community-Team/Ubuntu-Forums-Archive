---
title: "Compiling error"
date: 2005-09-26
forum: Desktop Environments
---

### Post by Tilex on 2005-09-26
I'm trying to compile a sotware from source under Kubuntu 5.04.  When I type ./configure in order to generate a "make" file, it stops at this error, thereby not yielding any make:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
```
I've googled it and apparently I would need X development libraries, so I updated my system through Synaptic Package Manager, install xorg-common (the only library I could find that would do something to my X windows) and nothing seems to have improved.
Any thought?

---

### Post by Knome_fan on 2005-09-26
I think you need libx11-dev.

---

### Post by Tilex on 2005-09-26
Thanks for the advice Knome_fan!  It worked well for my X-development problem...but now "./configure" stops elsewhere:
```
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!
```

What the *hell* is this?

---

### Post by mlomker on 2005-09-26
> What the **** is this?

Please watch your language...this is an international, family-friendly environment.

You need **kde-devel**.

---

### Post by Tilex on 2005-09-26
Sorry about that... 
I managed to make it through the "configure process" by installing kde-devel and qt3-devel...i don't know which one was required but it worked fine at the, which is good :)
Thanks for your great support guys!

---

