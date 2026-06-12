---
title: "Gnome desktop shows home-folder"
date: 2008-02-11
forum: Desktop Environments
---

### Post by knj on 2008-02-11
Hi everyone.

After a failed mount, my desktop now shows the content of my home-folder. "/home/knj/Desktop" is available for both writing and reading, but the desktop wont use that folder anymore.

How can I change this, so I shows the content of "/home/knj/Desktop" again?

-- 
Regards
Kasper Johansen

---

### Post by knj on 2008-02-11
SOLVED:

Do this:
gedit ~/.config/user-dirs.dirs


Look for the line:
XDG_DESKTOP_DIR="$HOME"

Change it to:
XDG_DESKTOP_DIR="$HOME/Desktop"


Found it right after I posted :-)

---

