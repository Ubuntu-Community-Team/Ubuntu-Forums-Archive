---
title: "How to replace window manager in Gnome?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by thor on 2005-10-17
Hi, everybody!

I'm wondering, is there a correct way of replacing default Gnome's window manager (metacity?) with other one - ion3 in my case?  In Configuration Editor I have found a key /desktop/gnome/applications/window_manager/default, but description of that key says it's deprecated.

I mean, I want to have full Gnome environment just with other window manager - ion3.  If I choose ion3 at GDM login page, all gnome apps look ugly..

Thanks!

---

### Post by Knome_fan on 2005-10-17
Hi, I don't know if this is the correct way, but it works for me:
1. Open gnome-terminal
2. Remove metacity from the gnome-session:
gnome-session-remove metacity
3. Start your windowmanager in the background:
nohup ion3 &
4. Save your new gnome-session:
gnome-session-save

That should be it.

P.S.:
I never used ion3, let alone with Gnome, so I don't know how good it works, or if it is even possible to use ion3 with Gnome.
You could however try to make your Gnome apps less ugly with ion3 by autostarting /usr/lib/control-center/gnome-settings-daemon with your ion3 session. (I guess that this should solve your problem with the ugly gnome apps)

---

