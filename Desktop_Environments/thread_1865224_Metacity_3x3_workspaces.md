---
title: "Metacity 3x3 workspaces"
date: 2011-10-19
forum: Desktop Environments
---

### Post by acunningham on 2011-10-19
I've just upgraded to 11.10, and am using Unity 2D due to graphics corruption problems with Unity.

I've set 9 workspaces using the num_workspaces, but they're in a single row, i.e. 9x1. Is there a way to change to 3x3?

---

### Post by crdlb on 2011-10-19
The layout of virtual desktops is traditionally owned by the pager, which [sends a message]("http://developer.gnome.org/wm-spec/#id2550891") to the window manager.

This is [https://bugs.launchpad.net/unity-2d/+bug/715587](https://bugs.launchpad.net/unity-2d/+bug/715587). Comment #9 on that bug contains a python script that can work around the problem.

---

### Post by acunningham on 2011-10-19
Thanks, that works! I'm surprised Ubuntu doesn't have a facility to set this out of the box, but never mind...

I don't suppose there's a way to move to the center workspace in the 3x3 automatically on login?

---

### Post by crdlb on 2011-10-19
Well, this is a bug due to the different implementations of workspaces in Compiz and metacity.

To jump to the center workspace, you could make a small modification to that script before line 58 (Gtk.main_quit()):```

        self.screen.get_workspace(4).activate(0)
```
Make sure there are exactly 8 spaces.

---

### Post by acunningham on 2011-10-19
That's great, thanks! Last question for now: Is there a way to show a pager in the notification area, like Gnome classic mode in 11.04?

---

### Post by acunningham on 2011-10-20
Maybe not...

---

