---
title: "Compiz error"
date: 2010-05-31
forum: Desktop Environments
---

### Post by Husam on 2010-05-31
husam@ubuntu:~$ compiz setting manager
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1e000b4 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Now, if i close terminal, window's will be bugged .

---

### Post by Shazzam6999 on 2010-05-31
What is it you're trying to do, are you trying to use Compiz as a standalone wm? How did you install Compiz and did it work before? Just need some details :)

If you're just trying to alter settings then you want the compiz config settings manager. I'm not sure what you're trying to do but I think it's just the wrong package. Looks like compiz is trying to become the wm but I don't think that's what you want.

---

### Post by Husam on 2010-05-31
I want to edit compiz setting, i think its installed already in latest ubuntu, 10.4 or something. thats what i have.
btw, im newbie

---

### Post by Shazzam6999 on 2010-06-01
Here, this sticky does a way better job of explaining it than I possible could: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695). I'm fairly sure it isn't installed by default but if it is you'll find it under the system tab on the top menu.

---

