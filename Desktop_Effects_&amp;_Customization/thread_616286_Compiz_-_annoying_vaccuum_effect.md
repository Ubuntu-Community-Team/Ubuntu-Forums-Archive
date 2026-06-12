---
title: "Compiz - annoying vaccuum effect"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by lsutiger on 2007-11-18
I have the vacuum effect enabled for the close animation:
(type=Menu | DropdownMenu | Dialog | ModalDialog | Normal)

But it is being used for all tooltips?? It's pretty annoying!! Any ideas?

---

### Post by atomkarinca on 2007-11-18
open up compizconfig settings manager, under effects > animations you can change your close, focus, minimize, open and shade animations.

---

### Post by lsutiger on 2007-11-18
I understand what you just posted...The reason I posted the settings is to know why this is happening..how do you think I had access to those settings?
Thanx for the reply, but please READ before you reply!
No Offense, just please READ!

---

### Post by Forlong on 2007-11-18
Use this for window matching:

```
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

---

### Post by lsutiger on 2007-11-18
Thank you , Sir!

---

