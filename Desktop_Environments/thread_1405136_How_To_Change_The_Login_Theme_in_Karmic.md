---
title: "How To Change The Login Theme in Karmic"
date: 2010-02-12
forum: Desktop Environments
---

### Post by skykooler on 2010-02-12
I have been trying for a while to find out how to easily change the login window's theme in Karmic. Most instructions I found had me log out and type commands in a terminal - which is a lot of rigamarole as you can't copy and paste. However, I just found the way to edit from *within* an administrator's account:

```
# gksudo -u gdm dbus-launch gnome-appearance-properties
```

This launches what looks like the standard appearance properties window, but with a the login theme as default. You can change the theme, icons, wallpaper, fonts, even desktop effects! (I don't know how useful desktop cube and wobbly windows would be for the login screen though.)

---

