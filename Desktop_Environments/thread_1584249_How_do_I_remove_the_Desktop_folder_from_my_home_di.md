---
title: "How do I remove the Desktop folder from my home directory?"
date: 2010-09-28
forum: Desktop Environments
---

### Post by mcbiff on 2010-09-28
I don't have anything on the desktop but it won't let me delete this folder, and if I sudo rmdir it it just comes back.

---

### Post by kerry_s on 2010-09-28
in gnome the Desktop folder is actually the "Desktop" & the file manager draws the desktop.

---

### Post by mcbiff on 2010-09-28
Yeah, I know, and Nautilus isn't drawing the desktop. So how can I delete the folder? It's just cluttering up my home directory.

---

### Post by hhh on 2010-09-28
What about changing the line in ~/.config/user-dirs.dirs from ```
XDG_DESKTOP_DIR="$HOME/Desktop"
``` to ```
XDG_DESKTOP_DIR="$HOME/"
``` and then deleting the Desktop folder?

---

### Post by mcbiff on 2010-09-28
Thanks hhh, that seems do have done the trick.

---

### Post by hhh on 2010-09-28
Cool, np.

---

