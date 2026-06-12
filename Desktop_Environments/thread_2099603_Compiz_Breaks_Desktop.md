---
title: "Compiz Breaks Desktop"
date: 2012-12-29
forum: Desktop Environments
---

### Post by CupOfItalian on 2012-12-29
Hello, So every time I try to change the compiz profile, it crashes and breaks my desktop. I then have to either unity --reset, or compiz --replace for it to work again.

I have ubuntu 12.04 with kernal 35, and compiz 0.9.7.9
Video Card is a ATI Radeon HD5000 series, using the ATI Radeon driver for ubuntu.

Does anyone know how to fix the bugs in compiz? Or have a different solution?

---

### Post by TOMBSTONEV2 on 2012-12-29
What are you trying to change with compiz?

---

### Post by zombifier25 on 2012-12-30
That happens, and usually it resets itself, but in some cases you will have to restart Compiz with compiz --replace.

(And unity --reset wipes out your configuration :| )

---

### Post by CupOfItalian on 2012-12-30
It happens when i try and change the profile. 
 
  -- So I am not the only one then. zombifier, do you know of an alternative or a way to fix that?

---

### Post by vanadium on 2012-12-30
Touching the compiz settings can (easily) break your desktop. That is known and advertised (see for example askubuntu). Either you take the risk, or you stay away from it.

---

### Post by zombifier25 on 2012-12-30
> **CupOfItalian said:**
> It happens when i try and change the profile. 
 
  -- So I am not the only one then. zombifier, do you know of an alternative or a way to fix that?

You can run ```
metacity --replace
``` in a terminal which will give you a minimal window manager for you while you tweak Compiz safely. When you're done, ```
compiz --replace
```

---

### Post by CupOfItalian on 2012-12-30
Ok. Thanks everyone.

---

