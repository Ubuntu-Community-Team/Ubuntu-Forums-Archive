---
title: "Changing Wm without rebooting?"
date: 2010-07-05
forum: Desktop Environments
---

### Post by tenchu77491 on 2010-07-05
I am on a live flash drive, and I want to change the WM. How can I do this? 

I tried to kill X with control+alt+backspace but it didn't work. I also tried to alt+f1 and control c, then delete the x lock and 'start x' but it wouldn't work. 

How can I 'exec newwindow manager' and restart x without a reboot? 
:icon_frown:

Care to share any cli that can kill x so I can restart it?

---

### Post by tenchu77491 on 2010-07-06
Solved with 

sudo pkill x
restart x

---

### Post by dzon65 on 2010-07-06
depending on what wm you wanna use,you can always install compiz fusion icon.Once clicked,it'll appear on your panel,allowing you to swith wm's.
My bad,live flash drive.Ignore.

---

### Post by mcduck on 2010-07-06
The keyboard shortcut to kill X (or the current TTY session actually, so it works for text consoles as well) is SysRq+k (or Alt+PrtScr+k if you like it that way).

Replacing window managers is usually done simply by executing the new window manager with the "--replace" parameter. For example "metacity --replace", "compiz --replace" and so on. This doesn't require restarting X.

---

