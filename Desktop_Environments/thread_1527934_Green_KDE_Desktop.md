---
title: "Green KDE Desktop"
date: 2010-07-09
forum: Desktop Environments
---

### Post by Spids on 2010-07-09
Hi, I'm using Kubuntu 10.04, and I'm having a weird issue with one of the multiple virtual desktops. They all work fine, but one of them has a green tingle to it when I use the desktop cube effect. It also has a weird green effect when I use the slide effect to change to and from that certain desktop.

It doesn't happen until I have 5 or more virtual desktops, then one is chosen at random to be green. I'm also using KDE 4 (I believe).

This is what the desktop looks like when sliding to or from the green desktop, but when the sliding is done, it looks like any normal desktop.

It almost seems like I'm running GNOME while using KDE, but I really have no idea, as that guess may tell you.

Thanks for any help! :)

---

### Post by neoargon on 2010-07-10
from what I understood, the gnome's desktop(named nautilus) is also loaded . That's the problem. To solve , press alt+F2 and type ```
killall nautilus
``` .That would close gnome desktop(ei kill nautilus)

There is another way of closing gnome desktop . Open system monitor.For that,  Kmenu->system->system_monitor  click on process table. You can see nautilus . Right click on it, click on end process

---

### Post by Spids on 2010-07-10
Ah, yup that was it! Thanks a lot bud! ^^

---

### Post by neoargon on 2010-07-11
> **Spids said:**
> Ah, yup that was it! Thanks a lot bud! ^^

Hehe . That was a pleasure

---

