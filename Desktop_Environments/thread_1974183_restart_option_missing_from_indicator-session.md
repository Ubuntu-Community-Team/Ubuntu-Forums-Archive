---
title: "restart option missing from indicator-session"
date: 2012-05-05
forum: Desktop Environments
---

### Post by el_baby on 2012-05-05
Hi,

a few days ago I installed Precise on a new Dell Precision m4600 (it seems quite reasonable to put Precise on a Precision). I had a couple of problems I solved googling around (one of them beeing its inability to reboot, solved as explained [here](http://askubuntu.com/questions/111807/dell-precision-m4600-stuck-at-last-stage-of-reboot).

However, at some point after installation but before solving the above problem, the *Restart* option disappeared from the **indicator-session** menu.

I installed dconf-editor and made sure that **supress-restart-menuitem** and **supress-logout-restart-shutdown** be off, however, the **Restart** option still doesn't appear ('sudo reboot' works fine within a terminal window, though).

Any ideas?

---

### Post by el_baby on 2012-05-09
BUMP...
anyone?

---

### Post by kansasnoob on 2012-05-10
So if you click on Shut Down as shown below you don't get the other window to open offering to either shut down or restart?

[ATTACH]217623[/ATTACH]

---

### Post by el_baby on 2012-05-10
You're right. Thanx, kansasnoob.

However, I am most certain (though not 100% sure) there was a 'Restart' option there just after I installed it.

Regards.

---

### Post by kansasnoob on 2012-05-10
> **el_baby said:**
> You're right. Thanx, kansasnoob.

However, I am most certain (though not 100% sure) there was a 'Restart' option there just after I installed it.

Regards.

Actually the Gnome devs axed that, but the Ubuntu/Canonical devs added it back in the most sensible way :)

A lot of people have complained about that so it may change as we transition to using clutter/mutter :)

---

