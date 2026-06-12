---
title: "Locking items on desktop in place"
date: 2012-09-18
forum: Desktop Environments
---

### Post by synaptix on 2012-09-18
Is there any way, if anyone knows, to make items on the desktop stay in place? I'm having a problem where the items I have on my desktop move out of their position and cluster into the top left corner whenever exiting a fullscreen app.

---

### Post by vasa1 on 2012-09-18
I can't recall seeing such an option. BTW, does this happen will any app that runs full screen or just a particular one?

---

### Post by synaptix on 2012-09-18
> **vasa1 said:**
> I can't recall seeing such an option. BTW, does this happen will any app that runs full screen or just a particular one?

Issue seems to only pertain to fullscreen games, as it does not effect fullscreen flash video in Firefox.

---

### Post by synaptix on 2012-09-18
Issue solved, thanks to GridCube on #xubuntu channel. ;)

---

### Post by gridcube on 2012-09-18
The solution i suggested was to lock ~/.config/xfce4/desktop/icons.[something].rc as read only.

This workaround makes the desktop locked to a fixed design and no changes can be made to it, no items can be added and they cant be moved around.

All the dynamic icons, like drives and stuff like that would still work.

---

### Post by vasa1 on 2012-09-18
@gridcube, thanks for posting. Otherwise the solution would have evaded quite a few people :)
However, isn't it a bit drastic? Ideally, going back to normal from full-screen shouldn't have such an effect, correct?

---

