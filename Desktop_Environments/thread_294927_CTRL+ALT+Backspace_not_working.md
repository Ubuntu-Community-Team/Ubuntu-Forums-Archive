---
title: "CTRL+ALT+Backspace not working"
date: 2006-11-07
forum: Desktop Environments
---

### Post by matt_b on 2006-11-07
On my Sony TR1MP laptop, CTRL+ALT+Backspace does not do anything at all. Is there somewhere I have to enable this or is there another keyboard shortcut to use? I've searched the forum but this doesn't seem a common problem. I need to keep restarting Gnome to test 915resolution.

I'm running Ubuntu 6.06.

Thanks
matt

---

### Post by fortran01 on 2006-11-07
You can manually restart gnome display manager (gdm) using the command line (as privileged user): /etc/init.d/gdm restart

---

