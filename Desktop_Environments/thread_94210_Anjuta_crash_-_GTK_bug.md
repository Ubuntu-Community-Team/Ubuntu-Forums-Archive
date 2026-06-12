---
title: "Anjuta crash - GTK bug?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by ijanos on 2005-11-23
I think i find a nasty gtk bug. Anjuta crash when I turn on any toolbar which is floating. If i detach a toolbar and close anjuta and then open it, it cannot stand up again, it crash while loading. I thougt its an anjuta bug, but after a total reinstall, and deleting ~/.anjuta the program still cannot stand up! Then i noticed in gtk apps (eg: gedit) when i detach a toolbar with dragndrop and release the mousebutton, i cannot grab it again, only with holding down ALT, but I still cannot dock it in its place again. 
At this point, I have no idea.

---

### Post by ijanos on 2005-11-25
Could somebody try detach the toolbar of anjuta or gedit, release the mousebutton and then try to dock it again in its original place?

---

### Post by ijanos on 2006-01-07
OK. I found it:
~/.gnome2/Anjuta 
Delete this file and the toolbars take their default place.
Thanks for the help... :D

---

### Post by cro.smiley on 2006-04-08
Thank you for posting answer, you helped me a lot :)

---

