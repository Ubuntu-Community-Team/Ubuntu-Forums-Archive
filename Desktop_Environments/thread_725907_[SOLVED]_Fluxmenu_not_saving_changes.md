---
title: "[SOLVED] Fluxmenu not saving changes"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Patb on 2008-03-16
I am using Fluxbox window manager.  My gui menu editor, fluxmenu, worked flawlessly for ages then suddenly refused to update the menu when I click save.  I can manually edit ~/.fluxbox/menu and "force" the issue that way but I cannot understand why this sudden problem.  I cannot think of anything which precipitated this behaviour.  Any ideas would be appreciated.  

Thanks in advance. Cheers, Pat.

---

### Post by banewman on 2008-03-16
My guess would be that an ubuntu update included a newer version of menu and fluxmenu can't access it.
:)

---

### Post by Patb on 2008-03-17
> **banewman said:**
> My guess would be that an ubuntu update included a newer version of menu and fluxmenu can't access it.
:)
Thanks for the tip, Banewman.  A bit of an embarrasment - problem solved - Fluxmenu could not find the command I was writing because it was not in my path.  I didn't realise it checked before saving.  

Cheers, Pat.

---

