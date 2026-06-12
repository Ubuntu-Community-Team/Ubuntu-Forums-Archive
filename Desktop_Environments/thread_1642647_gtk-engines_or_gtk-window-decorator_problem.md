---
title: "gtk-engines or gtk-window-decorator problem?"
date: 2010-12-10
forum: Desktop Environments
---

### Post by kitkat12012 on 2010-12-10
i'm getting this problem with either gtk-engines or gtk-window-decorator and i'm not sure what's causing it

I know how to fix them, but since it happened twice already in 2 days I thought maybe I should find out about the cause.


gtk-engines problem:
not sure why but twice already after a reboot, my desktop is "stuck" on the clearlooks.  Changing it via the appearance preferences window does nothing.  changing the theme actually causes it to become a "Custom theme" which still uses clearlooks

the only way I could get this fixed is by removing (purge) and reinstalling gtk-engines


gtk-window-decorator problem:
happened a few times, after a reboot, my desktop does not have a running window decorator (no title bars on windows)



any clues on why this is happening?  I'm guessing something is making them crash on startup but i'm not really sure what


Thanks

---

### Post by kerry_s on 2010-12-10
try putting "gnome-settings-daemon" in the startup.

---

### Post by netro_grant on 2011-04-30
yeah i have a similar problem, not the first one but since I upgraded to 11.04 I am getting no window borders :|.

Compiz is running fine, but theres no windows decorators running. so i run gtk-window-decorator and boom my borders appear. What i need to know, is how to get gtk-window-decorator running automatically on start-up?

Thanks in advance,

Grant

---

### Post by Krytarik on 2011-04-30
@netro_grant: Check the setting "CompizConfig Settings Manager -> Window Decoration", it should be "/usr/bin/compiz-decorator", you could also set it to "gtk-window-decorator --replace". Also make sure that those plugin is enabled.

Hope it helps!

---

