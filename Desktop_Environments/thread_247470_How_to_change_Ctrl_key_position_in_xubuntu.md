---
title: "How to change Ctrl key position in xubuntu"
date: 2006-08-30
forum: Desktop Environments
---

### Post by michaelshiloh on 2006-08-30
In standard Ubuntu, it's easy enough:

System->Preferences->Keyboard->Layout Options

but in Xubuntu there is a reduced menu which allows for things like repeat key speed and layout, but is missing the "Ctrl key position" feature.

Can someone help me? I'm an old Unix hand, and keep hitting Caps Lock when I mean Ctrl.

Thanks,
Michael

---

### Post by Hal58 on 2006-08-31
> **michaelshiloh said:**
> In standard Ubuntu, it's easy enough:

System->Preferences->Keyboard->Layout Options

Can someone help me? I'm an old Unix hand, and keep hitting Caps Lock when I mean Ctrl.


Edit /etc/X11/xorg.conf (via sudo) and add to the keyboard section:

 Option  "XkbOptions"  "ctrl:swapcaps"

Then restart X.

---

