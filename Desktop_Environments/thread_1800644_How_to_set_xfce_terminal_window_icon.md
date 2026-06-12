---
title: "How to set xfce terminal window icon?"
date: 2011-07-09
forum: Desktop Environments
---

### Post by amn108 on 2011-07-09
I have an icon theme going, and when using 'gnome-terminal', the window of the terminal uses the icon from the theme. When using 'xfce4-terminal' however (which I prefer, given how I now run xfce), the window uses its own icon (that draws a large dollar sign in the middle of a black monitor) and simply ignores the terminal icon from the theme.

I would like to rectify this disturbing matter :-)

---

### Post by ajgreeny on 2011-07-09
Open the **exo-terminal-emulator.desktop** file on the desktop with mousepad, which will probably look like:-
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=exo-open --launch TerminalEmulator
[COLOR=Red]Icon=utilities-terminal[/COLOR]
StartupNotify=true
Terminal=false
Categories=Utility;X-XFCE;X-Xfce-Toplevel;
OnlyShowIn=XFCE;
Name=Terminal
```plus many more lines I have omitted, and change the line Icon=utilities-terminal to Icon=/path/to/icon/file

A bit clunky, I accept, but if the theme will not do it for you, I don't know any other way.

---

### Post by amn108 on 2011-07-11
Thanks for the help, but nope, that didn't do it. First of all, I don't have the exo-*.desktop file, second, even though I found the appropriate launcher desktop file, changing its icon (one can do so via the Main Menu GUI) doesn't affect the icon that the running window carries.

I don't have any more ideas, unfortunately.

---

