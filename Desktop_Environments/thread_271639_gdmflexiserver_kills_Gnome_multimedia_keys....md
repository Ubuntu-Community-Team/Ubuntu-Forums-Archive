---
title: "gdmflexiserver kills Gnome multimedia keys...?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by aysiu on 2006-10-05
I run *gnome-settings-daemon* as part of my IceWM startup so that I can get things like a bearable GTK theme and multimedia key functionality.

Funny thing, though, if I run *gdmflexiserver --xnest*, suddenly my multimedia keys die. My other peripheral keys work fine (the ones to launch email, the internet, my calculator, etc.). Heck, even the volume and mute buttons still work.

It's just play/pause, next, and previous die. If I log out and log back in again, everything's fine again. I tried *killall gnome-settings-daemon* and then *gnome-settings-daemon* to see if that'd make a difference. I also tried to Restart IceWM, but nothing short of a full logout makes a difference.

Anyone else had this happen in IceWM (or any other window manager or desktop environment for that matter)? Is there an easy solution? Should I just not run *gdmflexiserver*? Should I file a bug report?

---

### Post by aysiu on 2006-10-10
Bump.

---

