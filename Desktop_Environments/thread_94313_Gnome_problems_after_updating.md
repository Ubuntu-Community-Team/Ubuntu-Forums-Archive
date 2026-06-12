---
title: "Gnome problems after updating"
date: 2005-11-23
forum: Desktop Environments
---

### Post by mrt on 2005-11-23
The last batch of updates contained some kernel updates, and eventually I was suggested to restart.  After rebooting, I am no longer able to log into Gnome or Failsafe Gnome.  I can get to the Failsafe Terminal.  X is loading because my login screen is graphical.  FYI I do run nvidia 3d drivers.  I tried reverting back to the "nv" drivers to no avail. 

When I try to log into Gnome, a box pops up stating my session has lasted less than 10 seconds and that there might be problem.  The Details of the error says things like "unable to find transport: tcp" and that it can't read ~/home/mrt/.ICEauthority.

I can get more of the error message if necessary, but I can't copy and paste so it would be tedious.  Is anyone able to tell what my problem is?

---

### Post by fimbulvetr on 2005-11-23
rm $HOME/.ICEauthority

---

