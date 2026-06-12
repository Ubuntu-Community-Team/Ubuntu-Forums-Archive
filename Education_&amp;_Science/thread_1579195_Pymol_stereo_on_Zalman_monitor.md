---
title: "Pymol stereo on Zalman monitor"
date: 2010-09-21
forum: Education &amp; Science
---

### Post by superarthur on 2010-09-21
I am wondering if anyone here uses Pymol with a Zalman monitor.
I went Display->Stereo Mode->Quad-buffered stereo, but nothing changed on the screen.
The computer has a Quadro FX 580, and the latest Nvidia driver for Ubuntu installed, and I could get the stereo effect on Coot.
Can anyone give me advice on how to turn on the stereo effect on Pymol?

Many thanks in advance,
Arthur

---

### Post by yoyoq on 2010-10-01
hi,
start pymol like this:

/xtal/programs/pymol/pymol -S -t 6

-S is the stereo option
-t 6 is zalman value

you can then turn it off from the menu,
butnot back on.
apparently it requires more memory
allocation or something so pymol doesn't plan
to put it in the stereo menu

jpd

---

### Post by superarthur on 2010-10-05
Thank you very much, the stereo works now :D
You won't realise how much I appreciate your help (is it a secret that Pymol kept from non-subsciber? :P)
None of the website I searched on google talked about 6 being the value, and I thought the problem was with the graphics card (since Nvidia only supports 3D vision on windows only for Quadro FX 580)

---

### Post by yoyoq on 2010-10-05
i think i saw it on the ccp4 email list.
pymol and 3d viewing issues come up all the time.
(there was one today about how zalman monitors are always
out of stock)

---

