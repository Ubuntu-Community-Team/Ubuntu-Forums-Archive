---
title: "Cannot always shutdown using keyboard"
date: 2017-01-02
forum: Desktop Environments
---

### Post by buisteric on 2017-01-02
Hi,

This is an inconsistent behavior that becomes more and more annoying. Usually it works, sometimes it fails. To shut down Ubuntu running MATE, I used to hit ALT-F1 to pop up the menu, arrow key to select the shutdown item, then enter twice. But sometimes, the system sticks in the Shutdown dialog and absolutely no keyboard actions responds. I cannot hit enter to shutdown, Alt-R to reboot, Escape to cancel, nothing. Any reason why sometimes it works, sometimes not? The only workaround is to use the mouse or open a terminal window, type sudo poweroff and once again repeat my password.

---

### Post by buisteric on 2017-01-11
The problem also happens on CentOS 7 running MATE, so this is not an Ubuntu-specific issue. It could be caused by MATE or GTK+. Any way to make poweroff work without sudo, without running as root all the times?

---

### Post by geeksmith on 2017-01-11
You could set the sticky bit on the poweroff binary. You'd have to do this again if it were replaced again during a package upgrade.

```
sudo chmod +s $(which poweroff)
```

---

