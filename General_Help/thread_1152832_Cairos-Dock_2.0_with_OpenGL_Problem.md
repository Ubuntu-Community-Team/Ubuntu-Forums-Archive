---
title: "Cairos-Dock 2.0 with OpenGL Problem"
date: 2009-05-08
forum: General Help
---

### Post by t4ggs on 2009-05-08
Hi, I'm running Jauntry, ATI 4870 video card using the propietary drivers and the ATI Catalyst Control Center, I have no problems with compiz, but whenever I use Cairo-Dock 2.0 RC5 with OpenGL, thats how it looks

any ideas why??

---

### Post by t4ggs on 2009-05-08
I'm also having problems with Google Earth.. could that be the OpenGL. Should I install anything special??

---

### Post by t4ggs on 2009-05-10
...??

---

### Post by r5r4y on 2009-05-22
same problem here... i've the same card runing ubuntu 9.04.

---

### Post by t4ggs on 2009-05-22
the problem is with the driver...i guess we will have to wait till a new version

---

### Post by Nicodemus144 on 2009-05-22
i'm having the same problem on my MSi Wind, which has an Intel GMA950.  the 950 does support OGL as far as i know.

---

### Post by fabounet on 2009-05-22
no, they don't support it correctly yet.
but it's coming, you have to activate UXA in your xorg.conf

---

### Post by r5r4y on 2009-05-23
is there anyway around it? free drivers or something?

---

### Post by fabounet on 2009-05-23
for Intels, you can install the last xserver, and activate UXA in xorg.conf
or wait that it is available via Synaptic
for ATI, it seems they use monkeys to code their drivers :roll:

---

### Post by jonnykwest100 on 2009-12-06
I have the same problem but when i run :
```
cairo-dock -c
```

it run without problems, effects will not work and it will be slow because it load on CPU not GPU

reference:
[http://www.cairo-dock.org/ww_page.php?p=Recurrents%20problems&lang=en]("http://www.cairo-dock.org/ww_page.php?p=Recurrents%20problems&lang=en")

---

