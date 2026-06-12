---
title: "session emulator"
date: 2008-01-06
forum: Desktop Environments
---

### Post by kutlu on 2008-01-06
I am searching for an emulator so that I open a new session in a new window.
My aim is to capture screenshots in a script without interrupting my daily work. I prepared the script, but it does not take screenshots (screenshot is a black white dirty page) when session is in background.

---

### Post by adam.tropics on 2008-01-06
You need to install 'xnest'. You may (seem to remember) then need to right click on the menu bar, and edit so the menu shows 'New login in a window' under System.

edit: It would be a wise thing to add another user account to use with it as well.

---

### Post by PeterJS on 2008-01-06
Xnest has been replaced by Xephyr.

I run xfce, but I've got a couple of scripts that launch KDE and gnome nested.
```

#/bin/sh
Xephyr :1 -ac -screen 800x600 &
sleep 2
DISPLAY=:1 startkde &

``````

#/bin/sh
Xephyr :2 -ac -screen 800x600 &
sleep 2
DISPLAY=:2 gnome-settings-daemon &
DISPLAY=:2 nautilus -n &
DISPLAY=:2 gnome-panel &
DISPLAY=:2 metacity &

```

---

### Post by kutlu on 2008-01-06
Thank you all. I was using kde. I found my way to Xephyr by inspecting from Xnest. I set the system. It works now :)

---

