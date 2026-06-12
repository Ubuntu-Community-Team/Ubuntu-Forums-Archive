---
title: "matlab segmentation fault"
date: 2006-02-03
forum: Desktop Environments
---

### Post by augifili on 2006-02-03
I have installed matlab without any problems, but very frequently it crashes and says: segmentation fault. Other times it also crashes and complaints about java errors. I have the same version of Matlab (7.0.0.19901 (R14) ) installed on my laptop with Mandriva 2005 LE and I have no problems. Is there something I can do to fix this? My PC is a P4 2.4 GHz, 1GB RAM, no dual boot windows :-)

---

### Post by sfabel on 2006-02-04
Per default, Matlab uses it's own pre-shipped java version (don't know exaclty what version that is). You can specifiy the environment variable MATLAB_JAVA to point to another JVM and Matlab will then use that one.

I've had bad experiences with Sun's JRE 1.5, though, so you might want to try blackdown or ibm.

If you don't really need pretty windows, just start matlab with the "-nojvm" option and it will simply start in the xterm Window. You can still use Simulink but it will be the X libraries, not Java, that draws them. I've found that mode of operation way more stable and satisfactory than the other one.

Cheers,
Stephan

---

### Post by rwmcgwier on 2007-09-08
Sun's JRE 1.6 works beautifully

---

