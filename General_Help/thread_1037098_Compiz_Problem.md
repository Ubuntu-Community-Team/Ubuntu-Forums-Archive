---
title: "Compiz Problem"
date: 2009-01-11
forum: General Help
---

### Post by wasutton3 on 2009-01-11
I am running a fully up to date 8.10 64 bit installation. Whenever i enable compiz (using system -> preferences -> appearance -> desktop effects tab) i get a black border that surrounds my entire screen. not individual windows, but as if the computer is trying to display the screen on a smaller monitor. When i revert back to using metacity, or no desktop effects at all, the screen occupies the entire display. Does anyone have any ideas or should I contact my display manufacturer. I am running an ati radeon hd3850 over DVI. i have never had this problem before having to RMA my monitor because the DVI burnt out

---

### Post by gettinoriginal on 2009-01-11
Into terminal copy/paste this:  :p
```
compiz --replace
```

---

### Post by wasutton3 on 2009-01-11
Ok i have tried this and it isnt working. I however did lower the resolution from 1920*1080 to 1360*768 and that did the trick. The monitor is fully capable of displaying it at 1920*1080 because it has done it before.

---

### Post by gettinoriginal on 2009-01-11
Glad you found the solution, please go to thread tools and mark this as solved. :p

---

### Post by wasutton3 on 2009-01-11
its not actually the solution though. the problem simply disappears at a specific resolution. i would like to get this working at the higher resolution, but i cant seem to figure out how

---

### Post by gettinoriginal on 2009-01-12
Is the problem that your desired resolution is not listed, or that the desired resolution renders bad results, sorry, but I'm getting confused.  (its me, not you LOL, just the time of night here)  I did see in some threads that installing "envyng" will solve display problems.

---

### Post by wasutton3 on 2009-01-12
the resolution is displayed and can be selected. but when i select my desired resolution 1920*1080, i have this black boarder that appears around my desktop. the usable screen area does not fill the lcd panel itself.

---

### Post by wasutton3 on 2009-01-12
ok i just tried envyng and it installed the driver. i can use compiz and all the effects at the full resolution, however i still have this black border all the way around, using up my valuable pixels

---

### Post by gettinoriginal on 2009-01-12
Two suggestions left, and I am out of ideas.  Install Compiz Fusion Icon" from synaptic, once it is installed, you right click on it and it allows you to choose your window manager and window decorator.  I also advise installing emerald, also in synaptic.  Then  with the Fusion Icon select "emerald as your window decorator and compiz as your window manager.

---

### Post by wasutton3 on 2009-01-12
the problem of the black border on all 4 sides disappears when using a 1680*1050 resolution which i guess is ok

---

