---
title: "Can't log out or shutdown from KDE"
date: 2012-06-29
forum: Desktop Environments
---

### Post by fixitdude on 2012-06-29
Sometimes if KDE didn't start fully the logout buttons won't work.

Open a terminal (to get to console, hold down Ctrl and Alt and hit F3) and do this (if all your work is saved):

sudo service kdm restart

If you hold down Alt (not Ctrl Alt at this point) and hit F7 or F8 the normal KDE login box should be there.

Done!

---

