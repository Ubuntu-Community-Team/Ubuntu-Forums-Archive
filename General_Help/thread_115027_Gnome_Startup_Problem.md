---
title: "Gnome Startup Problem"
date: 2006-01-09
forum: General Help
---

### Post by OlineSixtyOne on 2006-01-09
I think one of the programs in gnome startup (in the session's thing where you can add startup programs) is preventing me from getting to the desktop in gnome. I need a way to remove something from the session startup thing without a gui. Can I use nano? Which file do I need to edit?

---

### Post by OlineSixtyOne on 2006-01-09
Bump. Come on, 11 views and no help?

---

### Post by aysiu on 2006-01-09
[QUOTE=OlineSixtyOne]Bump. Come on, 11 views and no help?[/QUOTE] It usually means no one knows the answer. People aren't deliberately ignoring you.

**Edit**: You can try ```
cp ~/.gconf/apps/gnome-session/options/%gconf.xml ~/.gconf/apps/gnome-session/options/%gconf_backup.xml
nano ~/.gconf/apps/gnome-session/options/%gconf.xml
```

---

### Post by OlineSixtyOne on 2006-01-09
Thank you. I think I found the problem and fixed it. At least I can log into Gnome now.

---

