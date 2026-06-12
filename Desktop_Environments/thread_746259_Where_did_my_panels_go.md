---
title: "Where did my panels go?"
date: 2008-04-05
forum: Desktop Environments
---

### Post by myonta on 2008-04-05
Hey all,

I'm sure this problem has come up before, but my panels have disappeared (my setup is Gutsy 64 using Gnome and NOT using compiz fusion).

I'm not sure where to start with this one. If I login using GNOME-Failsafe they are there. Also, if I login a secondary account they are there too. The problem is when I login my default-setup on my primary account they are completely absent.

I have noticed that, when starting up, the splash screen only shows the first icon loading (I believe it's nautilus) and then goes to my panel-less environment. When loading failsafe or the other account, at least two more show up.

So, I'm pretty sure that it's simply a startup issue and could easily be fixed by editing a script or two. Thing is, I don't know what to edit. Also, I have no idea what caused this problem. One day it was just like this.

Thanks,
~Jon

---

### Post by Vadi on 2008-04-05
Try doing "killall gnome-panel", and then "gnome-panel". Do they come back?

---

### Post by myonta on 2008-04-05
Brilliant! I wasn't sure if it was a temporary fix so I logged out and back in... voila! Back to normal (I'm pretty sure).

Turns out the hardest part was getting the terminal: I tried CTRL-ALT-F2 and got no-can-do type messages back about gnome-panel; so, I ended up creating a launcher finally figuring out that it's "gnome-terminal," not just "terminal."

Thanks very much. I just wish I knew what caused it.

---

### Post by Vadi on 2008-04-05
You're welcome :)

---

