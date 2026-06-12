---
title: "Switching back to metacity"
date: 2011-04-23
forum: Desktop Environments
---

### Post by ThomasJ02 on 2011-04-23
So in a failed experiment, I tried out xmonad for a couple months. I would now like to switch back to metacity for my default window manager. How can I do this?

---

### Post by Krytarik on 2011-04-23
I don't know how you set 'xmonad', but these commands should bring you back to Metacity:
```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set metacity
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/bin/metacity
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/bin/metacity
```
Of course, you need to relogin after running those.

Greetings.

---

