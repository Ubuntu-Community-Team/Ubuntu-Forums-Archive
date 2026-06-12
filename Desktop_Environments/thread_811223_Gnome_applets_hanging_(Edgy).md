---
title: "Gnome applets hanging (Edgy)"
date: 2008-05-28
forum: Desktop Environments
---

### Post by MST3Kakalina on 2008-05-28
Quite out of the blue, my gtk/gnome stuff has started to hang (calculator and gnome-terminal, basically).   When I run "gnome-terminal" from konsole, I get this:

```
(gnome-terminal:10206): Gdk-CRITICAL **: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
The application 'gnome-terminal' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

 The gdk_gc_get_colormap part makes me think that it has something to do with the custom color scheme I have for gnome-terminal, but I'm really at a loss. Plus, it doesn't explain why gcalctool hangs (running gcalctool from konsole reveals no error message; it just takes forever to load). This happened rather suddenly, after a year(ish) of nothing but stability.


I will be upgrading to 8.04 in a while, but this is just TOO annoying and I want to fix it NOW. Any idea what I can do about it?

---

