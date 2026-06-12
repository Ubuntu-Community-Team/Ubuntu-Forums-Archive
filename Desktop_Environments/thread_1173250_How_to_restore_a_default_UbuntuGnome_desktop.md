---
title: "How to restore a default Ubuntu/Gnome desktop?"
date: 2009-05-29
forum: Desktop Environments
---

### Post by Brian Vaughan on 2009-05-29
Is there a straightforward way to restore the Gnome desktop to the state it would have in a freshly created account?

From time to time, I find that some panel icon is missing or out-of-place, because of some mistake I've made or some program crash, and I've wondered if I could restore the entire desktop to its out-of-the-box condition. Also, I know my twelve-year-old stepson enjoys tinkering with his desktop, which I certainly don't want to discourage, but I worry he'll tinker with it to the point where it becomes difficult to use.

Of course, I don't want to do anything overbearing like deleting and recreating a user account -- that'd create more problems than it would solve, with respect to user IDs, group IDs, and the like. And I don't want to reset any customizations that aren't directly related to the Gnome desktop -- for instance, my .vimrc. I just want to know how to reset the theme, panel icons, and similar parts of the user interface.

---

### Post by Gen2ly on 2009-05-29
```
mv ~/.gconf ~/.gconf.bck
mv ~/.gnome ~/.gnome.bck
mv ~/.gnome2 ~/.gnome2.bck
```

This willrename you gnome preferences folders so that new ones will be created.  Logout and back in to have new ones spawned.  Know too that doing this will also reset all your preferences for your gnome apps.

---

