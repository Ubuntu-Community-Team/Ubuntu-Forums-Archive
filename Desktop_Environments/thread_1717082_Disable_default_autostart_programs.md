---
title: "Disable default autostart programs"
date: 2011-03-29
forum: Desktop Environments
---

### Post by cccc on 2011-03-29
hi

I've Xubuntu with XFCE 4.6 installed.
In the autostart I have these programs by default:```

polkit-gnome-authentication-agent-1
xfce4-settings-helper-autostart.desktop
xfconf-migration-4.6

xfce4-tips-autostart -> I've already disabled
```

What they do exactly and which of them can be disabled without getting any problems?

---

### Post by hhh on 2011-03-29
Leave them, running all 3 uses only 10M of RAM. xconf and xfce4-settings-helper handle settings and polkit helps handle passwords. Disabling tips is the first thing I do on Xfce.

---

