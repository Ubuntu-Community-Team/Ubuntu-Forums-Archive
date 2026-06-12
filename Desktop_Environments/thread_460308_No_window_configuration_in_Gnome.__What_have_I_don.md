---
title: "No window configuration in Gnome.  What have I done!?"
date: 2007-05-31
forum: Desktop Environments
---

### Post by busgeek on 2007-05-31
I've broken something in Gnome!

The symptoms are:
1) All windows are piled into the top left-hand corner - with no borders and no chance to move or drag them.
2) I've also lost my multiple desktops from the bottom panel.
3) When I go to System->Administration->Windows, I get an error saying that no windows configuration tool is registered (something like that anyway.)

The first two symptoms effectively seems to stop me running more than one application at a time.

It's NOT because I've installed Beryl either.  (I haven't!)

The exact text of the error is:

     "Cannot start the preferences application for your window manager

       Window manager "unknown" has not registered a configuration tool"

Thanks
__________________
Howard Dickins

"Relentlessly combatting evil since 1981"
Dell Latitude D600 (Dual-boot XP + Ubuntu 7.04)

---

### Post by busgeek on 2007-05-31
Ok.  I learnt a new lesson today...

$  metacity &

Et voila!  All fixed!
Thanks for watching.

---

### Post by Jimbob17 on 2007-06-10
> **busgeek said:**
> Ok.  I learnt a new lesson today...

$  metacity &

Et voila!  All fixed!
Thanks for watching.

Thank you! I had this problem today after updating my Ubuntu installation on an old iMac.

Cheers!

---

