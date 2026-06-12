---
title: "Removing icon from desktop"
date: 2009-05-19
forum: General Help
---

### Post by MikeA36 on 2009-05-19
Hi folks, probably a simple question here but be danged if I can figure it out. :) What I have is an external HD attached to my computer, and naturally when Ubuntu mounts it, it not only appears under the "Places" menu, which is fine and where I want it, but also puts an icon and such for it on the desktop, which I don't want.  I like a clean and icon free desktop if possible.  Does anyone know how to remove the icon representing the drive, without un-mounting it?  

Thanks. :)

---

### Post by bhishan on 2009-05-19
Open up gconf-editor and go to: Apps -> Nautilus -> Desktop

Untick volumes_visible, home_icon_visible and computer_icon_visible. You desktop should be empty after that.

---

### Post by MikeA36 on 2009-05-19
Excellent!  Thank you very much!

---

### Post by lindsay7 on 2009-05-19
Where do I find the gconf-editor?

---

### Post by asmoore82 on 2009-05-20
> **lindsay7 said:**
> Where do I find the gconf-editor?

You have to run it from a terminal or Alt+F2 "Run Dialog"

Technically, you could right click and Edit menus and
unhide its entry "Configuration Editor" under "Applications -> System Tools"

But Alt+F2 is much faster as rare as it is need,
not to mention more Hacker Elite :wink:

---

### Post by lindsay7 on 2009-05-20
Thank you!

---

