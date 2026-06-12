---
title: "Different colour schemes per GNOME workspace?"
date: 2009-05-31
forum: Desktop Environments
---

### Post by original_MikZ on 2009-05-31
G'day everyone,

To make them more distinctive, I'd like to have different colour schemes (window themes) for different workspaces. An (over)simple example: if the workspace I'm looking at has windows with red title bars, and I type Ctrl+Alt+right arrow, I'd like the next workspace to have blue title bars.

Is there a way to do this?

Different screen backgrounds would be nice, too.

Thanks,
MikZ.

---

### Post by geonik on 2011-10-02
Brilliant idea! I was looking for something similar this morning. 

Anyone knows if it is possible? If not, it would make a great feature request.

---

### Post by Copper Bezel on 2011-10-02
Well, you can't have different themes per workspace, although it would be architecturally possible for a Compiz plugin to change the title bars, if you want to make a feature request; the same is not true of the theme of the content area of the windows, and it's probably very unlikely to be implemented.

However, if you're using 11.04 or 10.04 LTS, you can have different wallpapers for different workspaces. (The feature is broken in 10.10.) There's a plugin in Compiz called "Wallpaper" that provides this, and you can activate it in compizconfig-settings-manager, which you'll need to install if you don't have it. 

You do also have to turn off the default Nautilus wallpaper to make this work, however, using gconf-editor. Run the command gconf-editor and navigate to apps/nautilus/preferences, and untick "show desktop." Notice that this means that you won't have desktop icons (but who uses those, anyway? = D)

---

