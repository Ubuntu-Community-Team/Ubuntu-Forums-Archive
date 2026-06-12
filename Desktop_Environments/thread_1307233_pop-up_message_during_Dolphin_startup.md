---
title: "pop-up message during Dolphin startup"
date: 2009-10-30
forum: Desktop Environments
---

### Post by xuCGC002 on 2009-10-30
> Configuration file "/home/collin/.kde/share/config/dolphinrc" not writable.
Please contact your system administrator.

Is what a message displays each time I open Dolphin. Which is annoying. Clicking OK usually lets me do what i need to do, but... I just wanna know how to remove it. And I'm using Karmic.

---

### Post by Old *ix Geek on 2009-10-31
> **xuCGC002 said:**
> Configuration file "/home/collin/.kde/share/config/dolphinrc" not writable.
Please contact your system administrator.The permissions need to be changed so the file is writeable.

Depending on who the owner of the file is, you may or may not need to do this with *sudo*. In a terminal, type this:

**chmod 666 ~/.kde/share/config/dolphinrc**

and press [enter]. That should do it. If you're still having problems, post again!

---

### Post by SirPecanGum on 2010-01-23
Thank you!

---

### Post by a6equj5 on 2010-08-11
I'm pretty new to Ubuntu. I had installed regular Ubuntu but decided to try Kububtu. The original install didn't do this when I launched Nautilus, but I get the same error as the original poster. Why isn't this configured by default? I'm kind of curious about things like this and why I'd need to chmod a file that should be writable by default. 

Did I do something wrong during installation? I'm wondering if I need to re-install. Hopefully I don't run in to additional issues. 

So far, loving Kubuntu! :D

---

### Post by hellnest on 2010-10-30
it's like a bug... sometimes when you change profile picture also it's didn't change ^^

---

### Post by Zorael on 2010-11-02
This is the kind of thing that can happen if you open graphical applications with **sudo** instead of with **kdesudo** (or **gksudo**). Then the program gets started as root but using your user's home directory for its settings, so root may assume ownership of files.

**sudo** for terminal, **kdesudo** for graphical. Never ever '**sudo dolphin**' or '**sudo systemsettings**'.

---

