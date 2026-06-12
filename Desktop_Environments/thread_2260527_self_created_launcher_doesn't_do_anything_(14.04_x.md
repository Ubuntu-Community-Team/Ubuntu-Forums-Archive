---
title: "self created launcher doesn't do anything (14.04 x64)"
date: 2015-01-12
forum: Desktop Environments
---

### Post by legendbb on 2015-01-12
Hi, all, 

New to 14.04.1, created a desktop launcher at ~/Desktop (tried ~/.local/share/applications) as:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name[en_US]=my_gui
Exec=/bin/run_my_gui.sh
StartupNotify=true

```

Right-click the launcher icons and set properties > Permissions > Execute as "Allow executing file as program"

While I can run /bin/run_my_gui.sh from termianl without any issue (it's a gui executable), double clicking the launcher from desktop or from unity search brings a busy cursor but the application doesn't run at all.

I've tried "gnome-desktop-item-edit" utility, launcher created by such behaves the same.

Thanks for reading

---

### Post by monkeybrain20122 on 2015-01-12
Try 

```
Exec=sh /bin/run_my_gui.sh
```

---

### Post by legendbb on 2015-01-12
Thanks for quick reply. Tried your code, no luck.
I've cat some examples from /usr/share/applications/
no syntax error I made. Anyone, please share a method in debugging .desktop launcher?

Thanks,

---

### Post by legendbb on 2015-01-12
Although I don't know what exactly cause the trouble, I got it working with the following settings:
moved .desktop from ~/Desktop to /usr/share/applications and chagned .desktop to:
> [Desktop Entry]
Version=3.0
Type=Application
Name=my_gui
Terminal=false
Exec=run_my_gui
StartupNotify=true



run_my_gui is a bash script wrapper file which calls the GUI to start.

---

