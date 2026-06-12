---
title: "window dragging in openbox"
date: 2008-05-28
forum: Desktop Environments
---

### Post by supersonicdarky on 2008-05-28
You can drag windows in any place (not just the decoration) if you hold alt and drag with left mouse button. Is it possible to change alt to super (don't want to disable it)? It makes it impossible to use photoshop properly.

I looked in rc.xml but didn't find anything of interest.

---

### Post by jviscosi on 2008-05-29
I think you would want to change (or add) a mousebind entry to the Mouse section of rc.xml with a different binding.  Mine currently says this:

>       
<mousebind button="A-Left" action="Drag">
    <action name="Move"/>
</mousebind>


If you change the button to "Windows-Left" (or whatever you have your super key mapped as) then that might do it.

---

### Post by urukrama on 2008-05-29
To use the super (windows) key, change jviscosi's settings as follows:

> <mousebind button="**W**-Left" action="Drag">
<action name="Move"/>
</mousebind>

---

