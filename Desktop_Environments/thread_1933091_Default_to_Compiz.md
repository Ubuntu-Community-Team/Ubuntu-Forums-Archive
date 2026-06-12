---
title: "Default to Compiz"
date: 2012-02-28
forum: Desktop Environments
---

### Post by LanceHaverkamp on 2012-02-28
I have compiz installed & working on Lubuntu 11.10, but I have to manually restart the WM to get compiz active.  Everything I've tried does not get compiz running at boot:

~/.config/lxsession/lubuntu/desktop.conf &
~/.config/lxsession/LXDE/desktop.conf **both** say:

```
window_manager=compiz ccp

```
But it still boots into the default openbox.

What's the trick?

Thanks,
Lance

---

### Post by ajgreeny on 2012-02-28
Try adding an extra entry ```
@compiz --replace
``` to the autostart file (plain text) in /etc/xdg/lxsession/Lubuntu.

---

