---
title: "No workspaces with Gnome-Shell/Ubuntu 14.04"
date: 2014-07-25
forum: Desktop Environments
---

### Post by ryankrizan on 2014-07-25
Hello folks,

Fresh install of Ubuntu 14.04, with gnome-shell and all other packages installed. However, I don't have any workspaces, only one main desktop. Going to the workspace dock only shows one of course. I'm not sure how to add more. Any ideas on how to get my workspaces back?

Thank you for reading

---

### Post by deadflowr on 2014-07-25
Gnome Shell uses dynamic workspaces.
When you open an app then open activities, are any other workspaces showing?

---

### Post by ryankrizan on 2014-07-25
No, it doesn't create another workspace like it should. Just the one main workspace.

---

### Post by tea for one on 2014-07-25
> **ryankrizan said:**
> No, it doesn't create another workspace like it should. Just the one main workspace.

Do you have gnome-tweak-tool installed?

If so, have a look at the setting:-

gnome-tweak-tool > Workspaces > Workspace Creation

---

### Post by buzzingrobot on 2014-07-25
By default, Gnome Shell creates and deletes workspaces dynamically.  There is always one open, empty, workspace available.  Put something in it, and another empty workspace gets created. Users do not create and delete workspaces manually.

Move your mouse cursor into the top left hot corner, by the "Activities" label.  That should expose a column of the existing workspaces on the right of the display.

If that does not happen, then either something is, in fact, wrong, or dynamic workspaces have been disabled somehow.  Gnome Tweak Tool has an option to do this, so check the workspace settings with it.

Some Gnome extensions modify the default behavior of workspaces, too.

---

### Post by grahammechanical on 2014-07-25
Did you install 14.04 Ubuntu and then install Gnome 3 shell on top? Or did you install Ubuntu Gnome that has Gnome 3 shell by default.

In Ubuntu + Unity there is only one workspace by default. We go to System Settings>Appearance>Behaviour and we tick the box Enable Workspaces. And that will put a 4 x workspace grid icon on the Unity Launcher and we will have 4 workspaces. May be you need to do this to get the effect you are looking for in Gnome 3 Shell installed onto Ubuntu + Unity.

Regards.

---

