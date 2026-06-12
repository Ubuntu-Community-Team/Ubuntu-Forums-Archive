---
title: "Windows without upper part"
date: 2010-06-03
forum: Desktop Environments
---

### Post by jorgecachoh on 2010-06-03
Hi all,

My Kubuntu crashed yesterdary, and after reboot all my windows don't have the upper part (where the title appears and the minimize-maximize icons, ....) You can see the picture attached.

[IMG]http://img163.imageshack.us/img163/3884/instantnea1d.png[/IMG]

On the same way task don't appear on the botton bar.

Is there a way I can "restore", "fix" the environment without deleting/installing from scratch?

Thanks

        Jorge

---

### Post by dtfinch on 2010-06-03
I don't use KDE, but what happens if you run "kwin --replace &" from a terminal? That should start or restart KWin, the window manager that's supposed to draw the window titles, borders, and such. The equivalent on Gnome is Metacity, which would probably work too, but it might be weird in some unforeseen ways.

---

### Post by jorgecachoh on 2010-06-03
Perfect fix!! Now it works!!

THANKS!

---

