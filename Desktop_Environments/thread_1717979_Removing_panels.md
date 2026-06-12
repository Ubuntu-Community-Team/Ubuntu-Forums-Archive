---
title: "Removing panels"
date: 2011-03-30
forum: Desktop Environments
---

### Post by megabuffen on 2011-03-30
I noticed it is possible to add and remove panels from the Gnome desktop. However, the remove panel option also shows up when I right-click the two default panels for programs and open windows. What happens if I remove one of these panels? Will I be able to restore them?

---

### Post by ff-addict on 2011-03-30
yes, you can get them back by right clicking and then selecting "add to panel"

---

### Post by Krytarik on 2011-03-30
To restore *all* your panels to their defaults, you could run these commands:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```Of course, you could also right-click at the remaining panel, choose "New Panel", and then add the various applets and launchers you want.

Greetings.

---

### Post by Frogs Hair on 2011-03-30
Some users remove panels to use  one or more of the dock options available . Some dock options are  Awn , Docky , GLX dock , and Dockbar X .

---

### Post by Copper Bezel on 2011-03-30
And, of course, many people opt for a simple Windows-style taskbar with just the essentials, all on one panel.

You can always add a new panel or add applets to an existing one, and Gnome won't let you remove the last panel, so there's no worry that you might "accidentally the whole thing", as they say. = )

---

