---
title: "suspend problem"
date: 2005-04-09
forum: Desktop Environments
---

### Post by coldsalmon on 2005-04-09
Hi,

I'm running a Gateway 450ROG laptop.  Every time I try to come out of suspend, my computer shuts down (goes to runlevel 0, system halt).  This is very annoying, I suppose there must be something somewhere executing a command to shut my computer down, does anyone know where this might be?

Thanks,

--C

---

### Post by soul_rebel on 2005-04-10
Probably this is what happes:
You press the power button
The pc wakes up an restores linux
Linux knows you pressed the power button
Linux powers the pc off.

Can you verify this? Can you try restoring closing and opening the lid?

---

### Post by coldsalmon on 2005-04-10
Good thinking, it works when I suspend by using the lid.  Should I report this as a bug (I'm a noob, so not sure about what counts as a "bug" and what doesn't)?

Thanks again,

--C

---

### Post by soul_rebel on 2005-04-11
If you are using the latest packages available, yes you should report this.

---

