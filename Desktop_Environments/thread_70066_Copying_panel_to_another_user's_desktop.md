---
title: "Copying panel to another user's desktop?"
date: 2005-09-28
forum: Desktop Environments
---

### Post by CubanCorona on 2005-09-28
I have created a GNOME panel that I would like to give to a new user.  Is there a way to do this?

---

### Post by mlomker on 2005-09-28
Have you looked in the /home/username/.gnome2 directory?  I haven't tried that, but I imagine you could just copy the files.

---

### Post by tomchuk on 2005-09-28
Copy your ~/.gconf/apps/panel and ~/.gconf/apps/gnome-settings/gnome-panel and ~/.gnome2/panel2.d to the new users home directory, maintaining the directory structure.

---

