---
title: "How to disable Compiz's desktop switcher with mouse scroll at edge of screen?"
date: 2009-04-23
forum: General Help
---

### Post by ShadowTek on 2009-04-23
I just activated Compiz and I'm getting irritated that whenever I scroll the mousewheel up or down near the edge of the screen it causes the desktop to switch. I would like to disable this, but I'm not sure which setting I need to modify.

Does anybody know where to disable this function?

---

### Post by nandemonai on 2009-04-23
Install the compizconfig settings manager:

```
sudo apt-get install compizconfig-settings-manager
```

You can find it under System -> Preferences once installed.

Edit the settings for 'Viewport switcher' -> 'Desktop-based Viewport Switching'.

---

### Post by ShadowTek on 2009-04-24
That seemed to do it.

Thanks

---

