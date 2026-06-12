---
title: "Sound"
date: 2009-02-18
forum: General Help
---

### Post by RedSingularity on 2009-02-18
Does anyone know how i can get the mic working on my headset?  It is analog not USB.  I can hear things through the headset but i cant record anything with the mic.

---

### Post by mikewu on 2009-02-18
This worked for me, but not for some other people, but give it a try.

alsamixer -V all

Scroll over to mic and turn it down to 0 to prevent feedback.

Go over to Capture or Mic Capt and turn that up all the way.

Hope this helps!

---

### Post by RedSingularity on 2009-02-18
Ahhh got it!  Thanks A LOT!!!!!

---

