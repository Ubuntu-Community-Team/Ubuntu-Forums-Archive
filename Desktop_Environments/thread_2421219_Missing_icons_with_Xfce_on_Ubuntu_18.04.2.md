---
title: "Missing icons with Xfce on Ubuntu 18.04.2"
date: 2019-06-18
forum: Desktop Environments
---

### Post by plaidshirtakos on 2019-06-18
I use Ubuntu with VNC connection from Windows. I see most of the icons as follows:

[IMG]https://i.stack.imgur.com/kLImO.png[/IMG]


System information:


    Linux vps568 4.15.0-52-generic #56-Ubuntu SMP Tue Jun 4 22:49:08 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Output of ```
xfconf-query -c xsettings -lv
``` command:


    ```
/Gtk/ButtonImages               true
    /Gtk/CanChangeAccels            false
    /Gtk/ColorPalette               black:white:gray50:red:purple:blue:light blue:geen:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10gray30:gray75:gray90
    /Gtk/CursorThemeName
    /Gtk/CursorThemeSize            0
    /Gtk/DecorationLayout           menu:minimize,maximize,close
    /Gtk/FontName                   Sans 10
    /Gtk/IconSizes
    /Gtk/KeyThemeName
    /Gtk/MenuBarAccel               F10
    /Gtk/MenuImages                 true
    /Gtk/MonospaceFontName          Monospace 10
    /Gtk/ToolbarIconSize            3
    /Gtk/ToolbarStyle               icons
    /Net/CursorBlink                true
    /Net/CursorBlinkTime            1200
    /Net/DndDragThreshold           8
    /Net/DoubleClickDistance        5
    /Net/DoubleClickTime            400
    /Net/EnableEventSounds          false
    /Net/EnableInputFeedbackSounds  false
    /Net/IconThemeName              elementary-xfce-dark
    /Net/SoundThemeName             default
    /Net/ThemeName                  Greybird
    /Xft/Antialias                  -1
    /Xft/Hinting                    -1
    /Xft/HintStyle                  hintnone
    /Xft/RGBA                       none

```


I already tried this command too, but hasn't any visible changes: 


    ```
xfdesktop --replace
```

---

### Post by aidatejedor on 2019-06-18
missing icons

---

