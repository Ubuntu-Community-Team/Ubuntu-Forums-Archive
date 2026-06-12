---
title: "Synaptic gives segmentation fault"
date: 2005-10-18
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-10-18
Trying to start *synaptic* just gives me a **segmentation fault**. If i start it from the menu it doesn't start. I tried kdesu synaptic and it doesn't start, then I tried sudo synaptic and it gives a segmentation fault.

Is there a SUPER HIGH priority on this or does anyone know of a workaround. I will have to use the other package mgr's in the meantime but they are not to my likeing(Adept is slow when one is browsing for things).

---

### Post by Takis on 2005-10-19
Have you tried removing it and reinstalling it? I'm not aware (as yet) of anyone else's Synaptic being broken.

---

### Post by GoldBuggie on 2005-10-20
It seems to work now....don't know exactly what caused it but what has changed is that after a reboot kynaptic complained and said maybe restart dcopserver. It was running so i delelted .DCOPserver_XXX__0 and restarted the server. Now I can enter synaptic again.

Thanks for responding!

---

