---
title: "[HOWTO]Disable trackerd globally(for all users)"
date: 2009-03-05
forum: Desktop Environments
---

### Post by hayalci on 2009-03-05
If you want to disable the indexer/searcher trackerd and tracker-applet, which are run for every user, follow the steps.

**1. Disabling tracker for globally (for all users)**

[LIST=a]
[*]Edit /etc/xdg/autostart/trackerd.desktop file with root priviledges (sudo vim, gksudo gedit ...)
[*]Add "Hidden=true" to the end of the file
[*]Do the same for /etc/xdg/autostart/tracker-applet.desktop if you want
[/LIST]

**1. Disabling tracker for your user only**
[LIST=a]
[*]Enter the directory "~/.config/autostart", create it if it does not exist
[*]Create a file named trackerd.desktop
[*]Paste the following into the file, save and exit
```
[Desktop Entry]
Encoding=UTF-8
Name=Tracker
Hidden=true

```
[/LIST]

When you logout and relogin, you will see that trackerd is not running.

---

