---
title: "compiz fusion 'unloads' itself..?!"
date: 2007-07-24
forum: Desktop Environments
---

### Post by Canesfan2020 on 2007-07-24
I have compiz fusion working but I have a weird problem where after a random amount of time.. usually inside of 2 minutes compiz will 'crash' and revert to metacity.. but I haven't seen any errors. Anyone have any idea what could be causing this?

edit - seems to do it especially after opening firefox

---

### Post by dreadlord_chris on 2007-07-24
> **Canesfan2020 said:**
> I have compiz fusion working but I have a weird problem where after a random amount of time.. usually inside of 2 minutes compiz will 'crash' and revert to metacity.. but I haven't seen any errors. Anyone have any idea what could be causing this?

edit - seems to do it especially after opening firefox

try starting compiz from a terminal and watch for any errors when it crashes...

---

### Post by Canesfan2020 on 2007-07-24
edit--

I get this in terminal

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1704

/usr/bin/compiz: line 777:   895 Segmentation fault      (core dumped) $*
/home/canesfan/.gtkrc-2.0:2: Unable to find include file: ".gtkrc-2.0-scrollbar_cog"

---

