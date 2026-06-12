---
title: "Changing renderer through terminal"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by lockdown571 on 2007-06-15
I've been having trouble emerald, so I started messing with the beryl settings.  I changed the renderer from 'automatic' to 'xgl' and the system froze up.  I restarted gnome, and it froze up immediately.  I ended up reconfiguring xorg via 'dpkg-reconfigure xserver-xorg'.  When I reinstalled beryl, though, I froze up again (much in the same way it did before).  It appears it is still trying to select xgl as the default renderer, even though I reinstalled beryl entirely.  Is there someway I can change this with a command via the terminal?

---

### Post by lockdown571 on 2007-06-15
Nm, I fixed it.  Emerald magically fixed itself too.

---

### Post by disturbedite on 2007-06-15
i had a very similar problem, i solved it by editing .beryl-managerrc.

---

