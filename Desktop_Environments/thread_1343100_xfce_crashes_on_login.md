---
title: "xfce crashes on login"
date: 2009-12-01
forum: Desktop Environments
---

### Post by kungfu_action_jesus on 2009-12-01
I installed xubuntu-desktop on top of ubuntu 9.04. It was running fine for about a week but now when I log in the panel and the desktop icons crash. If i open a terminal from gnome-do and restart the xfce4-panel (I think that's what its called) it all runs fine. I tried reinstalling and then completely purging it and installing it, but it still crashes on login. Any ideas? thanks.

---

### Post by kungfu_action_jesus on 2009-12-01
anyone?

---

### Post by Simian Man on 2009-12-01
Try:
```

rm -rf ~/.config/xfce4/panel/

```

Which will remove all of your panel configurations.  Then log out and back in.

---

