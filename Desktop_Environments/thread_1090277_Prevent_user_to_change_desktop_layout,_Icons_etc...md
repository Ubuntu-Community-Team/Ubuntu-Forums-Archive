---
title: "Prevent user to change desktop layout, Icons etc..."
date: 2009-03-08
forum: Desktop Environments
---

### Post by bbauto on 2009-03-08
I have a touchscreen where i have arranged 7 starters (icons) in order to execute 7 scripts nothing else should be permitted for that user. I have figured out how to lock the panels, but not the desktop itself.I have enabled "One click" but if you keep pressing the Icon a couple of seconds you will enter "Right click mode" properties etc... you can also move around the Icons... I simply want to prevent the user to do anything but execute those Icons(Starters).

I suppose schools have the same problems!?

On the left side i have a service panel (autohide) but it's only operational from remote desktop, so that's Ok!

---

### Post by wakojakop on 2009-03-08
i think it has something to do with permissions and other stuff like that, i will figure out in a minute

---

### Post by bbauto on 2009-03-08
PS! I have tried to change /home/user/desktop and /home/user/.nautilus/metafiles etc to "Read-only" but it's not working. I have also tried gconf but i only find setting for Panels, not the desktop itself!

---

### Post by scragar on 2009-03-08
> **bbauto said:**
> PS! I have tried to change /home/user/desktop and /home/user/.nautilus/metafiles etc to "Read-only" but it's not working. I have also tried gconf but i only find setting for Panels, not the desktop itself!

.gnome or .gnome2 ?

---

### Post by bbauto on 2009-03-08
Yeah maybe! but wich sub directories? I don't want to change keyrings etc to "Read-only", when it comes to Desktop settings they seems to be scattered allover??
=o!

---

### Post by bbauto on 2009-03-08
I wonder if it's possible to change the /home partition into a squashfs???

---

