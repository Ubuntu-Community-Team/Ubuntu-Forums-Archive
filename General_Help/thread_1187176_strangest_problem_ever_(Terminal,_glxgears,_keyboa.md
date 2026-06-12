---
title: "strangest problem ever (Terminal, glxgears, keyboard shortcuts)"
date: 2009-06-14
forum: General Help
---

### Post by UJean on 2009-06-14
I am testing Ubuntu 9.04 on my laptop with an ATI Radeon Mobility 9700. 

Encountering the following problem:
Fresh install
Applications/Accessories/Terminal
glxgears
gives me a nice animation and aproximately 1900fps

------------ everything is fine untill here ------------

now I go to Keyboard shortcuts and tell Ubuntu to start terminal if i press "Super R" (The right windows key)
press key "Super R" -> terminal starts
glxgears
the animation is flickering and I get approx. 800fps

testing the Applications/Accessories/Terminal way again - everything is fine

this is 100% reproducible 
can somebody elaborate what went wrong?
I believe that this is one of the reasons that some users complain about flickering with the Radeon driver.

---

### Post by Tony Flury on 2009-06-14
do you get any warning messages when you run glxgears either time ?

---

### Post by UJean on 2009-06-14
Nope, just the usual message when I close glxgears
"XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 31999 requests (31786 known processed) with 0 events remaining."

---

### Post by UJean on 2009-06-14
Can someone using the free-radeon driver confirm this issue?

---

