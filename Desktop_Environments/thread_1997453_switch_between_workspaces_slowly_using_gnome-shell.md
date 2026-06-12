---
title: "switch between workspaces slowly using gnome-shell"
date: 2012-06-05
forum: Desktop Environments
---

### Post by chehsunliu on 2012-06-05
Recently I use gnome-shell instead of Unity. Everything is fine except that the transition of workspace switching is not very smooth. By the way, the same action taken under Unity is smooth. Is there any solution to improve the performance?

---

### Post by markbl on 2012-06-05
> **chehsunliu said:**
> Recently I use gnome-shell instead of Unity. Everything is fine except that the transition of workspace switching is not very smooth. By the way, the same action taken under Unity is smooth. Is there any solution to improve the performance?

I use both Unity and Gnome-shell (still can't decide which one I prefer - both are excellent) and find workspace transition (ctrl+alt+down/up)is the same speed and smoothness. So sorry, doesn't help you much except that there must be something wrong with your system.

---

### Post by chehsunliu on 2012-06-05
After searching several websites, I found a solution. Add the following line in [FONT="Courier New"]/etc/environment[/FONT]

```
CLUTTER_VBLANK=none
```

Although the performance is not smooth as Unity, it is enhanced. Thanks for your reply.

---

