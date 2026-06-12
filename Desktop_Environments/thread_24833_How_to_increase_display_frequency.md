---
title: "How to increase display frequency"
date: 2005-04-08
forum: Desktop Environments
---

### Post by aluisiuz on 2005-04-08
It seems that Ubuntu didn't properly recognize my 21" CRT-Monitor (Interpraph TX-D2151W). In System->Preferences->Screen Resolution (translated from german) I can only choose 55Hz. 

I tried to increase the frequency values in xorg.conf step by step (I don't have the manual) but either it worked with only 55Hz or it didn't work (flickering due to wrong/high frequency I think).

What should I do to increase the frequency properly?

ciao,
aluisiuz

Edit: Ubuntu uses the nv-Driver if this is important.

---

### Post by jdodson on 2005-04-08
[QUOTE=aluisiuz]It seems that Ubuntu didn't properly recognize my 21" CRT-Monitor (Interpraph TX-D2151W). In System->Preferences->Screen Resolution (translated from german) I can only choose 55Hz. 

I tried to increase the frequency values in xorg.conf step by step (I don't have the manual) but either it worked with only 55Hz or it didn't work (flickering due to wrong/high frequency I think).

What should I do to increase the frequency properly?

ciao,
aluisiuz

Edit: Ubuntu uses the nv-Driver if this is important.[/QUOTE]

something that "might" help is installing the binary nvidia drivers.  its the only thing i can think of off the top of my head.  at times it has allow me more monitor refresh rates.

directions are here: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by aluisiuz on 2005-04-08
Thanks for the advice. It works fine :)

> directions are here: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Great page  :-D

---

