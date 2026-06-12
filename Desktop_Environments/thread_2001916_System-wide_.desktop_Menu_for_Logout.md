---
title: "System-wide .desktop Menu for Logout"
date: 2012-06-11
forum: Desktop Environments
---

### Post by dodle on 2012-06-11
I'm using Lubuntu but I have switched to gnome-panel. I'm trying to add a system-wide logout option to the menu. I created the following .desktop file:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=system-shutdown-panel
Name[en_US]=Log Out
Exec=lubuntu-logout
Name=Log Out
Icon=system-shutdown-panel
```

The file is /usr/share/applications/logout.desktop. But it does not show up in the main menu. Anybody know why or how I can create a system wide logout menu entry in the gnome-panel menu.

---

### Post by spikoley on 2012-06-13
I just tried this with Ubuntu.  To get the icon in the Unity Launcher I had to open Nautilus to drag and drop it onto the launcher.  Now I just need to find the right commands to make it function properly. 

```
gksudo nautilus
```

Then navigate to /usr/share/applications/.  Find logout.desktop then drag and drop it onto the launcher.

I have never seen Lubuntu, but it should be similar.

---

