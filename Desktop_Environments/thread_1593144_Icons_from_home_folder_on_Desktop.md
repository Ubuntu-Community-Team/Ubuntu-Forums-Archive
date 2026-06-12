---
title: "Icons from home folder on Desktop"
date: 2010-10-11
forum: Desktop Environments
---

### Post by mafitzpatrick on 2010-10-11
Hi folks

Just completed a full clean install of 10.10 while keeping my home folder intact (on a separate partition) from a previous Debian install. Now on the new system which is looking very nice, but for some reason all my home-folder folders and files are showing on the desktop.

Clicking on Places > Home brings up the home folder. Clicking Places > Desktop also brings up the home folder (i.e. nothing brings up the ~/Desktop folder)

Opening gconf-editor and checking Apps > Nautilus > Preferences shows desktop_is_home_dir is unchecked.

Checking in Apps > Nautilus > Desktop shows all icons unchecked except volumes visible. I can from here turn the correct desktop icons on and off on the desktop, but not get rid of the contents of Home.

Am I missing an obvious setting here? Happy to nuke bits of my home folder-config if necessary but would like pointers where to start.

Thanks

---

### Post by mcduck on 2010-10-11
Check the *~/.config/user-dirs.dirs* -file and make sure there's a line like this:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by mafitzpatrick on 2010-10-11
Thanks mcduck, that's just what I needed.

Much appreciated

---

