---
title: "Why isn't Evince integrated with the HUD in Ubuntu 13.10?"
date: 2013-12-03
forum: Desktop Environments
---

### Post by lads on 2013-12-03
With Evince running and on focus, if I press Alt and then type, for instance, "open" nothing comes up. Is this a bug? Something wrong with my system? Any suggestions on how to fix it?

Thanks.

---

### Post by newb85 on 2013-12-03
In 13.10, AppIndicator menus are no longer accessible from the HUD.  Please mark the bug as affecting you.
[https://bugs.launchpad.net/hud/+bug/1165420](https://bugs.launchpad.net/hud/+bug/1165420)

---

### Post by lads on 2013-12-04
> **newb85 said:**
> In 13.10, AppIndicator menus are no longer accessible from the HUD.

Hi newb85, Evince does not have an AppIndicator. I am speak of the regular menus of the application.

---

### Post by qamelian on 2013-12-04
Evince uses the new Gnome menu model rather than the old type that appear above the app. As a result, the HUD can't communicate with those menus.

---

### Post by lads on 2013-12-05
> **qamelian said:**
> Evince uses the new Gnome menu model rather than the old type that appear above the app. As a result, the HUD can't communicate with those menus.

Gnome is diverging too much from the desktop to continue being the basis of Unity for much longer. I hope that forks of once good Gnome applications, like Nemo, can still provide users with an appropriate desktop experience.

---

### Post by newb85 on 2013-12-05
> **lads said:**
> Hi newb85, Evince does not have an AppIndicator. I am speak of the regular menus of the application.

Oops! My mistake.  For some reason, I was thinking of Empathy, which integrates with the messaging menu.  Sorry!

---

### Post by qamelian on 2013-12-05
> **lads said:**
> Gnome is diverging too much from the desktop to continue being the basis of Unity for much longer. I hope that forks of once good Gnome applications, like Nemo, can still provide users with an appropriate desktop experience.

It's really a matter of taste. I only use Unity when I'm testing the next development version of Ubuntu. Otherwise, I won't touch it. Gnome-shell is a much more comfortable and efficient environment for my needs. Personally, I like the direction Gnome is going.

---

