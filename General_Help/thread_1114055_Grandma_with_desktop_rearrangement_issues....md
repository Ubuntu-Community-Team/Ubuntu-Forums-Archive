---
title: "Grandma with desktop rearrangement issues..."
date: 2009-04-02
forum: General Help
---

### Post by onesojourner on 2009-04-02
My Grandma-in-law has been using ubuntu for about 6 months now.The only problem is when the great grand kids come over they start dragging and messing with stuff. What can I do to totally lock down the top and bottom bar so they can't do that any more?

---

### Post by FraggedLocust on 2009-04-02
If you right click the things you want to lock you can do so by clicking the checkbox (lock to Panel). I believe you can also lock the panels to the desktop (possibly through properties).

---

### Post by philinux on 2009-04-02
> **onesojourner said:**
> My Grandma-in-law has been using ubuntu for about 6 months now.The only problem is when the great grand kids come over they start dragging and messing with stuff. What can I do to totally lock down the top and bottom bar so they can't do that any more?

Set up a user for the kids.

---

### Post by Sef on 2009-04-02
> Set up a user for the kids. 	

System > Administration > Users and Groups to set up a desktop for the kids with their own password.

---

### Post by mb_webguy on 2009-04-02
Open the Run dialog with Alt-F2 and type "gconf-editor".

Navigate to apps->panel->global, and check the box next to lock_down.  This will prevent any modification of the panels.  Of course, the downside to this is grandma won't be able to change it either, without changing this setting.

And of course, the best solution is probably to create a separate user account for the kids.

---

### Post by onesojourner on 2009-04-03
> **mb_webguy said:**
> Open the Run dialog with Alt-F2 and type "gconf-editor".

Navigate to apps->panel->global, and check the box next to lock_down.  This will prevent any modification of the panels.  Of course, the downside to this is grandma won't be able to change it either, without changing this setting.

that's perfect. She does not know how and does not need to know how to change anything.

---

