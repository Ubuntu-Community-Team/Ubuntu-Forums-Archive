---
title: "Strange Problem With Desktop"
date: 2011-04-05
forum: Desktop Environments
---

### Post by shaquille on 2011-04-05
I am using Ubuntu 10.10. I am facing a strange problem with my desktop. In my desktop there are not any file or folder though there I put some folder. The Mouse button also don't work in my desktop. But when I Go to Place > Desktop there shows my previous folders. I can't put any of my files in my desktop. 
What to do? Plz help!!!

---

### Post by Krytarik on 2011-04-05
Check this:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/nautilus/preferences/show_desktop"
- make sure it is ticked

After fixing this issue, the mouse buttons should have an effect when clicking at the desktop.

Greetings.

---

### Post by shaquille on 2011-04-05
> **Krytarik said:**
> Check this:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/nautilus/preferences/show_desktop"
- make sure it is ticked

After fixing this issue, the mouse buttons should have an effect when clicking at the desktop.

Greetings.

Thanks a lot!!!
It worked!!!!!!!!!

---

