---
title: "Openbox 2-D Workspace Layout?"
date: 2009-01-01
forum: Desktop Environments
---

### Post by UanarchyK on 2009-01-01
I've recently switched from a full Ubuntu install to a minimal hardy install with openbox as a window manager, and I love it so far. The only thing I really miss from Gnome is having workspaces arranged vertically as well as horizontally. I liked operating in a 2x2 grid of workspaces.

Now, I know Openbox has the ability to switch to workspaces above and below the current one because it's in the default keybindings, but I have no idea how I could go about creating workspaces above or below the current ones. 

Any help would be greatly appreciated!

---

### Post by urukrama on 2009-01-01
Though Openbox supports arranging your desktops in that way, it doesn't do that. You'll need a pager to set the desktops in a grid.

From the [FAQ]("http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_put_my_desktops_into_a_grid_layout_instead_of_a_single_row.3F"):

> **How do I put my desktops into a grid layout instead of a single row? **

Your pager is responsible for doing this, and communicates with Openbox to make sure they agree on it. Any pager which complies with the EWMH specification should be able to do this. Examples are the gnome-panel pager and rox-pager. 

If your pager does not comply with the spec, or you don't use a pager, you can use [this small program]("http://icculus.org/openbox/tools/setlayout.c") to set the layout at startup, for example setlayout 0 2 2 0 for a 2x2 grid.

---

### Post by UanarchyK on 2009-01-01
Thanks a ton!

---

