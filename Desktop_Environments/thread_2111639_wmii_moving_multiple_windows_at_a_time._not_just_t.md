---
title: "wmii moving multiple windows at a time. not just the highlighted one."
date: 2013-02-02
forum: Desktop Environments
---

### Post by benkaiser on 2013-02-02
I am trying out some tiling window managers and I am loving wmii however it sometimes moves multiple windows (two or more) between views when I use the Mod+Shift+<number> shortcut. Is this the default behavior? Another problem is when I launch a new instance of google-chome, it doesn't open in the current view it opens in the same view as another already open session.

---

### Post by benkaiser on 2013-02-02
I manage to solve it. I was editing the wimm configuration file and kept refreshing the environment which was tying the binding multiple times so if I had logged in and refreshed once and went to move a window to a new view, the command would fire twice. The solution is to log out and back in after making modifications to your configuration.

---

