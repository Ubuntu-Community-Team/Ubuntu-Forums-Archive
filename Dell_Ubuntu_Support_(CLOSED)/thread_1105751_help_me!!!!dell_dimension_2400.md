---
title: "help me!!!!dell dimension 2400"
date: 2009-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seraiah on 2009-03-25
i love ubuntu but am a noob cant even run from live cd. sceen goes blank and only leaves cursor. tried changing bios graphics 1 to 8 still nada.

---

### Post by pHreaksYcle on 2009-04-05
upgrade RAM and graphics card. Worked for me.

---

### Post by abn91c on 2009-04-07
> **seraiah said:**
> i love ubuntu but am a noob cant even run from live cd. sceen goes blank and only leaves cursor. tried changing bios graphics 1 to 8 still nada.
leave BIOS alone do ctr+alt+f1 when a the prompt do```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then reboot, the problem is the i845 video card drive in the 2400, compiz wont run with ubuntu 8.10 due to a driver bug

---

### Post by billyboy1995 on 2009-06-20
i have not done anything to my 2400 and i got 9.04 to work without problems other than speed...so try 9.04

---

