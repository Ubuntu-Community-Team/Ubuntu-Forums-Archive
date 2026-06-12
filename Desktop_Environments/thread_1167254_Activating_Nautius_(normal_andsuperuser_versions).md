---
title: "Activating Nautius (normal andsuperuser versions)"
date: 2009-05-22
forum: Desktop Environments
---

### Post by swerdna on 2009-05-22
Hello, new user here, so a couple of elementary questions:
Is there in the menu's an icon to activate a superuser version of Nautilus?
and
I would like icons on my desktop to activate Nautilus (normal user version). How would I accomplish that?

Thanks
Swerdna

---

### Post by nyk on 2009-05-22
If you want to create a new menu item, go into System > Preferences > Main Menu, then choose the location where you wish to add it, and do so using the options on the right. If you want to create a root nautilus shortcut, try using:
```

gksudo nautilus

```

By a similar approach, right click on the desktop and choose "Add Launcher" to create links to the desired locations with:
```

nautilus ***

```

replacing *** with a path.

---

