---
title: "X11 Themes are partial with Compiz effects on."
date: 2010-05-14
forum: Desktop Environments
---

### Post by MasterNetra on 2010-05-14
Having that old problem with the mouse theme defaulting to the old fugly default when compiz effects are on and while over the desktop area. I tried following: [http://ubuntuforums.org/showthread.php?t=820245](http://ubuntuforums.org/showthread.php?t=820245) there is absolutely nothing like that in General>General Options in ccsm. Nothing in simple either.

---

### Post by mcduck on 2010-05-14
> **MasterNetra said:**
> Having that old problem with the mouse theme defaulting to the old fugly default when compiz effects are on and while over the desktop area. I tried following: [http://ubuntuforums.org/showthread.php?t=820245](http://ubuntuforums.org/showthread.php?t=820245) there is absolutely nothing like that in General>General Options in ccsm. Nothing in simple either.

Have you tried logging out and back again after switching the icon theme?

---

### Post by MasterNetra on 2010-05-14
> **mcduck said:**
> Have you tried logging out and back again after switching the icon theme?

Doesn't do a bit of good. Never did really. At least not for this type of situation 

```

sudo update-alternatives --config x-cursor-theme

```

and choosing the cursor does...now if I can only figure out how to get custom cursors into that list. I've tried moving the cursor folder into /usr/share/icons/ and adjusting its .theme to be like those that are already on the list, saving it as a cursor.theme, duplicating it and renaming the copy to be that of the folder (ex. Excliz_full.theme) and moving it to /etc/x11/cursors/ still don't show in the list...must be missing something...

Running UE 2.6 btw.

---

