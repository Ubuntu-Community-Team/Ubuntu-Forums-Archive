---
title: "XUBUNTU cant hadle when java crashes"
date: 2013-12-01
forum: Desktop Environments
---

### Post by Capra on 2013-12-01
Everytime java crashes, xubuntu freezes, and I'm forced to long press shutdown.  I can't be absolutley sure if its java crashing the problem but it always happens when I use eclipse or I'm starting tomcats.
Does anyone else experienced this? Im using xubuntu 12.04 LTS, I'm 100% percent sure that its not faulty hardware issue or anything likeley because happends the same on another notebook I got, with the same version of xubuntu.

Thanks!

---

### Post by QIII on 2013-12-01
Hello!

Have you tried starting the Java app via a terminal and watching the output for clues?

---

### Post by Capra on 2013-12-01
Most of the times happends using eclipse, I'm not sure how starting the application would give me clues?. It randomly crashes, not on startup

Btw thanks for answering  :)

---

### Post by Capra on 2013-12-11
I fixed with this.  Used raring hardware enablement.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#A12.04.3_.2B-_13.04_Hardware_Enablement_Stack_Policies_and_Procedures](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#A12.04.3_.2B-_13.04_Hardware_Enablement_Stack_Policies_and_Procedures)

---

