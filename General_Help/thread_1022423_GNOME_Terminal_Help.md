---
title: "GNOME Terminal Help"
date: 2008-12-26
forum: General Help
---

### Post by aznium on 2008-12-26
Hi,

When I right click on the gnome-terminal (ie. the part where the shell is), a new shell is launched instead of displaying the context menu . how can i disable this and show the context menu instead?

Thanks

---

### Post by drs305 on 2008-12-26
One of your keybindings may have been reset to allow for opening a terminal in the manner you describe. Run the following command in terminal and check the key associations to see if they are set to open a new terminal. Specifically you could check the "new_window" setting but there are others in the same section you should take a look at. I didn't see one specifically for right click menus.

```
gconf-editor /apps/gnome-terminal/keybindings
```

Just a bit down are the settings for profiles. If you use a profile you might check those settings, if not, then the Default profile settings.

---

### Post by aznium on 2008-12-26
i dont see anything out of ordinary there - how can I reset the keybindings to default?

---

### Post by drs305 on 2008-12-26
> **aznium said:**
> i dont see anything out of ordinary there - how can I reset the keybindings to default?

Normally if the keybinding has been manually set you can right click and choose "Unset" to restore the default value. That restores an individual setting. 

If you want to reset all gnome-terminal values, you could delete or rename your ~/.gconf/apps/gnome-terminal folder, which I believe will contain the terminal settings. If you decide to try that, I would just rename it, quit the session and log back in and see if gnome-terminal is acting correctly again. If not, I would delete the new and restore the old folder if you have already set up individual profiles or made other changes you want to save regarding gnome-terminal.

---

