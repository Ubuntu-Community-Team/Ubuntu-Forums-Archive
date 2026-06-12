---
title: "task manager problem"
date: 2011-08-12
forum: Desktop Environments
---

### Post by raunhar on 2011-08-12
Ubuntu 10.10

For the past few days, when I start my Laptop, the task bar , especially the Network Connections icon, does not show up properly. As a result, when I ckick on Evolution Mail icon, calender opend up, batteryicon will show something else.

What should be done to correct it.

Screen shot attached.

---

### Post by Frogs Hair on 2011-08-12
The command below will reset the panel to default , but I don't what is causing the problem to begin with.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by raunhar on 2011-08-13
I worked, but all the application launcjers 9added by me vanished). I redid it.
Will again check on restart.
Thanks

---

### Post by raunhar on 2011-08-16
On reboot, same problem.

---

