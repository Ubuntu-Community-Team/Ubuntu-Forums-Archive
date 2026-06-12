---
title: "Window decorations and dressings no longer show up after a reboot"
date: 2012-04-29
forum: Desktop Environments
---

### Post by sefs on 2012-04-29
Hi there,

Ubuntu: 12.04 with gnome-session-fallback.

Problem: After a reboot the window decorations no longer load.

Here is what I can remember doing.

I was editing the menus via right click "edit menus"  I saw (think it was in the other category) an item for metacity.  I deleted it from the menus.  I then ran metacity in terminal. I am sure this is related to my problem somehow.  But i did a bunch of other stuff like installing the apps i use back into 12.04.

After a reboot I have the problem as described above.

The only way to get back the windows dressing was to set up a startup entry that calls metacity.

How do i get it back to how it was where i did not need that startup entry?

Thanks.

---

### Post by Krytarik on 2012-04-29
> **sefs said:**
> I was editing the menus via right click "edit menus"  I saw (think it was in the other category) an item for metacity.  I deleted it from the menus.
Remove the now created custom "metacity.desktop" from your "~/.local/share/applications" directory - via command line:
```
rm ~/.local/share/applications/metacity.desktop
```Regards.

---

### Post by sefs on 2012-04-29
Hi thanks for your reply.

It didn't work.

---

