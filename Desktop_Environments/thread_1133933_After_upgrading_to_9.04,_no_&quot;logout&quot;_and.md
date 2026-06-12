---
title: "After upgrading to 9.04, no &quot;logout&quot; and &quot;shutdown&quot; options in &quot;System&quot; menu."
date: 2009-04-23
forum: Desktop Environments
---

### Post by wisam on 2009-04-23
The title says it all.
After upgrading to Jaunty, the logout and shutdown entries in the System menu disappeared.

More annoyingly is that Alt+F2 doesn't work anymore.

Any ideas?

---

### Post by El Zoido on 2009-04-23
Jaunty is so good, you just don't want to stop using it...



Sorry, had to say it ;)

---

### Post by StuartN on 2009-04-23
Add these to your menu:

gnome-session-save --shutdown-dialog
gnome-session-save --logout-dialog

---

### Post by zaomaster on 2009-04-23
Perhaps did it install the Fast-User-Switcher to the gnome-panel? Because if it did, the power options move to its menu rather than the System menu.

---

### Post by Jimmynemo2 on 2009-04-23
If you have the logout menu with the little man in your upper right corner, it takes it out of the system menu. If you remove the one from the upper right, it adds it back in automatically. if you want them both, follow the directions already given.

Hope this helps.

---

### Post by itsjustarumour on 2009-04-26
> **Jimmynemo2 said:**
> If you have the logout menu with the little man in your upper right corner, it takes it out of the system menu. If you remove the one from the upper right, it adds it back in automatically. if you want them both, follow the directions already given.

Hope this helps.

Ah, so it does.  Top tip - thanks for that!  :-)

---

### Post by itsjustarumour on 2009-04-26
> **wisam said:**
> More annoyingly is that Alt+F2 doesn't work anymore.

Any ideas?

I'm sure theres a "proper" way of doing this, but the way I (accidentally) discovered was by installing Ubuntu Tweak 0.4.7 - go to System>Security and theres a check-box there to enable/disable it.

---

