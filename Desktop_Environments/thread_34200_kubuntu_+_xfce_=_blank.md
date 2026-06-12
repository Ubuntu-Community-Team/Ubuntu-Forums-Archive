---
title: "kubuntu + xfce = blank"
date: 2005-05-13
forum: Desktop Environments
---

### Post by Tezkah on 2005-05-13
Hi, I just installed XFCE using kynaptic, and when I log out and go into an XFCE session, all I get is the wallpaper.  I can right click on the background for the XFCE menu, but I have no panels at all.  

I cannot open any XFCE settings programs, nothing comes up, and I haven't been able to find any terminal commands to open them.


Right now I'm installing GNOME in case its just a case of missing libraries.


Any help is appreciated.

---

### Post by Xian on 2005-05-13
Right-click on the desktop.

Goto Settings > Xfce4 Panel Settings

This is your main panel which should be visible.

Make sure "Autohide" is unticked.
Try adjusting the panel size and orientation.

---

### Post by harryc on 2005-05-13
Boot into kubuntu and run the following command from console, post the results here;

```
dpkg -l '*xfce*'
```

---

