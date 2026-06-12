---
title: "Gnome-panel error - won't start"
date: 2007-03-29
forum: Desktop Environments
---

### Post by mysticrider92 on 2007-03-29
Hi, I am having an annoying problem with my gnome panel. I recently changed around my gnome desktop (icons, gtk theme), then ran update manager because it was showing the icon. After restarting my computer, I logged into Gnome and get this error: > I've detected a panel already running and will now exit. This pops up about five times then I am left with an empty desktop. Between each popup, the panel with show for about a second. I also noticed that on the usplash screen the first program to load loads about three times. Can anyone help? I assume it is some configuration file, but I don't know which one. 

[edit] Also, I am running Edgy with Beryl if that helps.

[edit x2] I got a new error trying to start the panel from a terminal.
> Gtk-ERROR **: file gtkrecentmanager.c: line 2248 (get_uri_shortname_for_display): assertion failed: (name != NULL)
aborting...
This seems to be a problem with gnome-session. I tried reinstalling both gnome-session and gnome-panel and neither helped.

---

### Post by mysticrider92 on 2007-03-29
I solved this by using a solution on the gnome support forum (delete the $HOME/.gnome2 and $HOME/.gnome folders).

---

