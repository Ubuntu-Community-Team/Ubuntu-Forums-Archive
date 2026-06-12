---
title: "Problem copying/moving files or directories"
date: 2009-05-14
forum: General Help
---

### Post by KWhistle on 2009-05-14
I'm trying to copy/move/extract some files into VLC player skins directory and keep on getting a permission denied any time I try to drag-and-drop.  Don't really want to use the terminal for this, and I'm not that proficient with commands.  Is there some way to get "admin" access so I can just drag and drop?

K

---

### Post by kanikilu on 2009-05-14
If you are using Ubuntu and not one of the other variants, you can use ```
gksu nautilus
``` to start nautilus with root access. You can also install the **nautilus-gksu** package which adds an "open as administrator" option to Nautilus' context menu.

Either way, be mindful when using sudo as you can mess your system up pretty good if you don't know what you are doing...

---

### Post by KWhistle on 2009-05-14
Tried it, but it doesn't have Open as Admin option.

---

### Post by KWhistle on 2009-05-14
ok, nevermind ... just had to restart

ty!

K

---

