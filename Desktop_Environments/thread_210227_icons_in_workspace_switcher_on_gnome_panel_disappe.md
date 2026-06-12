---
title: "icons in workspace switcher on gnome panel disappear"
date: 2006-07-06
forum: Desktop Environments
---

### Post by nanotube on 2006-07-06
hey all
so, normally, there are icons shown on the workspace switcher for (most of) the programs that are open on that desktop. but after running for some time, those icons disappear. when i restart gnome-panel (killall gnome-panel), they reappear again.

representative screenshots are attached. (see the middle of the top panel for the workspace switcher)

is anyone else having the same problem, and therefore should we file a bug, or am i alone in this?

thanks in advance for all help and suggestions. :)

---

### Post by nanotube on 2006-07-09
anyone? :)

---

### Post by Wolki on 2006-07-09
Hmmm, try whether making the panel a few pixel larger will restore the icons for you. The workspace switcher will only show icons if the space provided by the window is large enough.

There does seem to be a problem though, sometimes they start to need a little more space (and your window size seems to stay the same, too)... might be a bug.

---

### Post by nanotube on 2006-07-10
> **Wolki said:**
> Hmmm, try whether making the panel a few pixel larger will restore the icons for you. The workspace switcher will only show icons if the space provided by the window is large enough.

There does seem to be a problem though, sometimes they start to need a little more space (and your window size seems to stay the same, too)... might be a bug.

well, my panel was 24 px wide, i set it to 26, and the icons "reappeared" without having to killall gnome-panel. so... i guess that solves it. but still seems like a bit of a bug, since it starts up showing the icons, but later decides to stop showing them, without any changes to its size. (though i hope now that it's 26 px, it won't be doing that again. :))

so anyway, thanks for your help!

---

