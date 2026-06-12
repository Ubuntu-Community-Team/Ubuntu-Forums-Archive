---
title: "Jaunty: Window fail with decoration"
date: 2009-04-27
forum: Desktop Environments
---

### Post by antisho on 2009-04-27
I am using Jaunty with GNOME and Compiz. Often, windows will not load fully -- for example, an open-file dialog shows a gray window that still responds to keystrokes; the volume indicator will pop up if I press volume up/down but won't change if I continue pressing it; a context menu doesn't highlight on mouse-over, or just appears as an empty frame. This goes away if I minimize and restore the window, or if I turn off window decoration in Compiz, but changing between Emerald and gtk-window-decorator doesn't help, so it looks like a problem with Compiz. It seems like the window decorator is somehow grabbing the window right after it appears but before any of the controls load, and not updating it until it needs to. Has anyone else had a similar problem?

---

