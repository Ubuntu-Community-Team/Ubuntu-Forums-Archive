---
title: "unity 2d workspaces switcher"
date: 2011-11-05
forum: Desktop Environments
---

### Post by andrea000 on 2011-11-05
I'M running Ubuntu 11.04 with unity 2-d and compiz I was wondering if there is a way to replace the workplace switcher with the expo in compiz or maybe make a launcher icon to use it.
Thanks

---

### Post by stinkeye on 2011-11-05
Firstly, how come your using unity 2d with compiz?

You will need to change your expo key in ccsm to ctrl+shift+e and install
xdotool for this to work.
```
sudo apt-get install xdotool
```

To use compiz expo as the switcher you can save this file as 
**compiz_expo.desktop** in **~/.local/share/applications**
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/usr/share/icons/unity-icon-theme/apps/48/workspace-switcher.png
Name[en_US]=compiz_expo
Exec=xdotool key ctrl+shift+e
Name=compiz_expo
Icon=/usr/share/icons/unity-icon-theme/apps/48/workspace-switcher.png
```

Just drag it to the unity launcher.

You can disable the old switcher from showing with...
```
gksudo gedit /usr/share/unity-2d/launcher/Launcher.qml
```

and changing line #106
```
items.appendModel(workspaces);
```

to read
```
//items.appendModel(workspaces);
```

May have to log out/in.

---

### Post by andrea000 on 2011-11-05
Thank you works great

---

