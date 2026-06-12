---
title: "My screensavers have disappeared in KDE"
date: 2007-02-25
forum: Desktop Environments
---

### Post by c0rrupt on 2007-02-25
I'm not sure when this happened, but I was going to change my screensaver only to discover that they are all missing.  I don't think they were deleted because my old screensaver still works even though it isn't listed.  Has anyone else had this problem?

Edgy Eft 6.10
KDE 3.5.5

---

### Post by chavo on 2007-02-25
There is a known bug in KDE that causes this. It happens if you edit your KDE menu and put them menu categories into a submenu. I'm not sure if you have edited your KDE menu, but I have seen this happen here.

---

### Post by c0rrupt on 2007-02-25
I done that the other day to make my menu look cleaner.  I guess I will have to change it back to the way it was.

---

### Post by eyemeansit on 2007-07-22
I also have this trouble, and yes, I edited my kmenu to make it more sensible to my brain. Any workarounds for this issue?

Thanks!

---

### Post by ACGarland on 2008-04-16
I'm experiencing this problem too and would be interested in hearing about any work-arounds.

---

### Post by ACGarland on 2008-04-16
I's the work-around I followed to recover from this problem.  It really isn't a work-around, but a reasonable way to revert to the original settings and retain portions of your own customization work.

:arrow: **If you make mistakes in the process, you could lose your existing menu configuration, so be careful.**

[LIST=1]
[*]Backup and revert my customizations by renaming the local menu edit history file.
```

mv ~/.config/menus ~/.config/menus.0

```

[*]Use the KDE menu editor to create a new top-level menu containing at least one item. I used the names **0 My Menu** which contained **0 My Item**.  We add the dummy empty item so that the menu list will show our new top-level entry (it skips empty menus) and also to serve as a marker of the position in in the newly-generated *~/.config/menus/applications-kmenuedit.menu* file. Why the "0" prefix? It provides a quick and unique accelerator key to get to the custom menu. I have the <Windows> key set up to bring up the K Menu so I can get to my items with three keystrokes: <Windows><0><menu item key assigned>. (Used to be *two* keystrokes until this bug bit me. :-( )

[*]Using your favorite editor, edit the new *~/.config/menus/applications-kmenuedit.menu* file. Find the locations of  **0 My item.desktop**. There should be two: one between <Layout> ... </Layout> markers and another between <Include> ...</Include> markers.

[*]Using your editor, also open the older menu layout file *~/.config/menus.0/applications-kmenuedit.menu*.  Find the entries of your previously customized items and copy and paste them from the old file into the new position below the two **0 My Item** entries.

[*]Save the new *~/.config/menus/applications-kmenuedit.menu* file.

[*]Verify that the menu now contains your previously-added items under **0 My Menu** below **0 My Item**


[*]Use the KDE menu editor (or manually edit the new *applications-kmenuedit.menu* file to delete the temporary **0 My Menu** entries.

[/LIST]

That should do it. The original menu is restored, your customizations are restricted to being below **0 My Menu**, and the screen savers will now reappear under "Configure Desktop".

---

