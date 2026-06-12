---
title: "HELP xlg using alot of cpu"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by Drumminea on 2008-01-27
i installed emeral awhile ago 

well after i installed it and ran the first theme things started going down hill from there..

my cpu just started being used all up

i thought it was cuz of compiz and that  awn dock

sence my comp has really low specs..

celeron m 2.6 ghz 512mb ram on board video

but i set my effects back to none and uninstalled Emerald 

but every time i move a window or minimize or use fire fox Xlg uses all my cpu

i used to have highest effects be able to have 10-15 apps open moving them from desktop to desktop and never go over 80%
WHAT DID I BREAK!!

i need help

---

### Post by Ub1476 on 2008-01-27
Hi, are you sure you need to run XGL to have run Compiz?

Post the output of:

```
lspci | grep VGA
```

You can view all processes which are runnning by opening System>Administration>System Monitor

---

### Post by Drumminea on 2008-01-27
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by Ub1476 on 2008-01-28
Intel controllers doesn't need XGL. You can probably remove it:

```
sudo apt-get remove xserver-xgl
```

---

