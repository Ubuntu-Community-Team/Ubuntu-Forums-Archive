---
title: "Gnome, KDE and Yakuake --HELP--"
date: 2008-02-12
forum: Desktop Environments
---

### Post by cmlorentz on 2008-02-12
I don't know if this is the right forum to post on but I've not found any solution anywhere else, so here goes.  I have Yakuake installed on my system and it loads and drops down and closes as its supposed to in Gnome. But when I log out and switch desktops to log in using KDE, Yukuake still starts up like its supposed to, but it doesn't drop down when I hit the key sequence. I've tried removing it and reinstalling it under KDE, but I get the same results. I know it was written for KDE, so the fact that I can make it work flawlessly in Gnome and not in KDE just doesn't make sense. I would be grateful for any suggestions, ideas or solutions.

PEACE

---

### Post by jaygo on 2008-02-26
I'm having a similar issue. It worked fine in Xfce (xubuntu) for a few days, then I couldn't get it to drop down. It launches and shows that it's running but will not respond to the default key (which I never changed).

I've 'completely removed' and reinstalled it but that didn't help. I wonder if there are hidden config files for it somewhere ...

---

### Post by jaygo on 2008-02-26
okay, fixed it. Just had to fix the config file (it had lost its shortcut key) under ~/.kde/share/config/yakuakerc . Not sure why that config wasn't removed when I uninstalled yakuake from synaptic (perhaps because it's a KDE app? ). Found this in [http://ubuntuforums.org/showthread.php?t=448661&highlight=yakuake]("http://ubuntuforums.org/showthread.php?t=448661&highlight=yakuake")

If that doesn't help, you might check your saved sessions and see if clearing them out helps.

GLHF

---

