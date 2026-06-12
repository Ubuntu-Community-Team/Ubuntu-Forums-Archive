---
title: "What to do when Ubuntu locks up?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Wheelman on 2006-09-28
Is there a function similar to CTRL ALT DELETE in windows that will open the task manager to identify a hanging process even if ubuntu doesn't seem to be responding?

---

### Post by ingo on 2006-09-28
in kde CTRL ALT ESC

---

### Post by andypaxo on 2006-09-28
One way to open the task manager in GNOME would be to press alt+F2 and then type gnome-system-monitor

In dior circumstances, pressing ctrl+alt+backspace will kill GNOME and take you back to a login screen - but this will close any open applications without saving

---

### Post by blackened on 2006-09-28
If you kill the x server (ctrl+alt+backspace) repeatedly, then gdm sometimes fails to restart. This can often be solved with a good ole **/etc/init.d/gdm restart**, or if that fails, a good ole **sudo reboot**.

---

### Post by whizbaby on 2006-09-28
I recommend
ctrl-alt-F1 (to console)
ps aux
(look for the process and remember it's ID)
kill -9 *process_id_remembered*

If X hangs restart it like the other people said.
(switch back to graphics console with ctrl-alt-f7)

---

### Post by Ramses de Norre on 2006-09-28
Mostly if ubuntu freezes I can't do none of the above things, the safe way to hard reboot than is this:
```
alt + SysRq + s    (Sync the harddrive caches)
alt + SysRq + u    (Remount filesystems read-only)
alt + SysRq + b    (Reboot)
```
SysRq is the same key as PrintScreen, above Home.

---

### Post by kabads on 2006-09-28
I like to SSH into the box and find out what's gone on. However, this doesn't always solve the problem, but it does allow for a little more diagnostics allowing a long term solution to prevent the lock-ups again.

---

