---
title: "Creating shortcuts for my games"
date: 2012-04-26
forum: Gaming &amp; Leisure
---

### Post by maurodi on 2012-04-26
Many times when I download a game I have to run it using a .sh file. I'd like to know how to create a shortcut to put in the Unity Launcher. Also, I'd like to know how to set an icon for such shortcut (the games usually come with a .png).

Thanks in advance!

---

### Post by 8Kuula on 2012-04-26
Maybe this helps.
Create a file ~/.local/share/applications/somename.desktop
Template:
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupNotify=true
Terminal=false
Name=
Comment=
Path=
Exec=
Icon=
X-Ayatana-Desktop-Shortcuts=
```

Should apear in Dash, where you can move it to launcher.

Example: ~/.local/share/applications/Diablo3Beta.desktop
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Name=Diablo III Beta
Comment=Play Diablo III Beta
Exec=/home/bunbun/scripts/wine-launch
Path=/home/bunbun/Games/Diablo III Beta
Icon=Diablo III Beta Launcher
Terminal=false
Categories=Game;
StartupNotify=false
```

---

### Post by maurodi on 2012-04-27
Thanks a lot! I will try it.

Anyway, isn't there an easier way? I mean, this should be a common feature. Right click on the Launcher, Create New Launcher.

---

