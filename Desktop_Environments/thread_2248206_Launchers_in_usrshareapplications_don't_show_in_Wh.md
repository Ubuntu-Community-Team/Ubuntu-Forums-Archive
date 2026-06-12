---
title: "Launchers in /usr/share/applications don't show in Whisker Menu."
date: 2014-10-13
forum: Desktop Environments
---

### Post by junioredge1 on 2014-10-13
I'm having a slight problem in Xubuntu 14.04. Whenever I add a .desktop launcher to /usr/share/applications, it doesn't show up in the menu. For example, if I were to create thunar.desktop containing:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Thunar File Manager
Comment=The Thunar File Manager
Exec=thunar
Icon=thunar
Terminal=false

```
It won't show up. But if I were to add a launcher via Menulibre, it would create a launcher in ~/.local/share/applications/menulibre-thunar-file-manager.desktop. So what I want to do is just be able to add pre-created .desktop launchers to Whisker Menu.

---

### Post by ajgreeny on 2014-10-13
It shows in my Whisker menu, but not where I expected it to until I looked in detail; it shows in the "Other" group of applications at the moment.
Add the line ```
Categories=System;Utility;Core;GTK;FileTools;FileManager;
``` at the bottom of the desktop file and it will then appear in "System" where it ought to be.

---

### Post by Dennis N on 2014-10-14
> **junioredge1 said:**
> I'm having a slight problem in Xubuntu 14.04. Whenever I add a .desktop launcher to /usr/share/applications, it doesn't show up in the menu. For example, if I were to create thunar.desktop containing:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Thunar File Manager
Comment=The Thunar File Manager
Exec=thunar
Icon=thunar
Terminal=false

```
It won't show up. But if I were to add a launcher via Menulibre, it would create a launcher in ~/.local/share/applications/menulibre-thunar-file-manager.desktop. So what I want to do is just be able to add pre-created .desktop launchers to Whisker Menu.

You should include a **Categories=** key in your desktop file to specify where the entry appears in the Menu. For possible Categories, see:

[http://standards.freedesktop.org/menu-spec/1.0/apa.html](http://standards.freedesktop.org/menu-spec/1.0/apa.html)

---

