---
title: "Gnome menu bar intermittently lagging or not responding"
date: 2013-11-09
forum: Desktop Environments
---

### Post by mcjohnalds45 on 2013-11-09
The contents of the menu bar (that's the one with the "File, Edit, View..." right?) often does not update until after a couple seconds. E.g I'll click one of the groups (e.g "File") and it will take a second to open, then clicking one of the items (e.g "Save) won't work until I've waited there for a while (usually about 2-10 seconds). Or I'll alt-tab from nautilus to Firefox and the menu bar will still only read "Files" for a couple seconds. Sometimes, I'll have to wait up to a minute to do something. Some programs are worse than others, Firefox is relatively snappy while gimp is a huge pain.

I'm not sure what caused this, It's a recent problem, but I've tried creating a new user account, no effect.

Specs:
Ubuntu 13.10, 32 bit
Intel core 2 duo E6600 (2x2.4GHz)
AMD ATI Radeon HD 4870
4GB RAM

---

### Post by vanadium on 2013-11-09
I had this experience, though less strongly, and mainly with the gimp. When switching windows, it took half to one second before the correct menu would become available. This seriously disrupts the work flow. Along with the fact that Alt+menu hotkeys still are not supported with LibreOffice (probably never will), this was a reason for me (again) to disable the global menu of Unity alltogether.

---

### Post by mcjohnalds45 on 2013-11-10
> **vanadium said:**
> I had this experience, though less strongly, and mainly with the gimp. When switching windows, it took half to one second before the correct menu would become available. This seriously disrupts the work flow. Along with the fact that Alt+menu hotkeys still are not supported with LibreOffice (probably never will), this was a reason for me (again) to disable the global menu of Unity alltogether.

Disabling the global menu bar with [FONT=courier new]sudo apt-get remove indicator-appmenu[/FONT] fixes everything. It's a shame the global menu bar is so buggy.

Thanks!

---

