---
title: "desktop shortcuts new from windows user"
date: 2016-04-01
forum: Desktop Environments
---

### Post by mike412 on 2016-04-01
I am trying to setup a spare computer as games server for dedicated game servers for my kids to play with. Had it running on windows 7 but crashed often, doesnt crash on ubuntu but am struggling to get things to work

I am trying to get steamcmd to run. Have got it installed but would like to create an executable shortcut with parameters set to run steamcmd and update server. This is easy on windows, create a shortcut and add the paramaeters at end of the target line.

Have tried unsuccesfully to achieve this on ubuntu and don't want to be typing everything into the terminal all the time as the servers will get updated. can some point me to a tutorial on how to create an executable shortcut with all the paramaters within the shortcut.

much appreciated
Thanks
Spikenaylor

---

### Post by montag dp on 2016-04-07
In Linux, "shortcuts" are called desktop entries.  They are files that end in .desktop and give various information about the executable to run, including the name, description, path, and icon.  If you want very detailed information, you can look at the specification here:

[https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)

However, the best way would be to copy an existing one and use it as a template.  All of the system entries should be located in /usr/share/applications, and user entries are in ~/.local/share/applications.  You can copy one of those, but be aware that they often have lots of extraneous lines that you won't need, like descriptions in different languages.  Here is an example desktop entry that I made for my own system:

```
[Desktop Entry]
Name=Display Switcher
GenericName=Turn external display on or off
Comment=Turn external display on or off
Exec=display_switcher
Type=Application
StartupNotify=true
Path=/usr/local/bin
StartupWMClass=display_switcher
Icon=preferences-desktop-display
Categories=System;Utility;
```

The Exec line is where you would enter the executable name with any command line arguments. You can save your file as whatever.desktop and place it in either /usr/share/applications or ~/.local/share/applications, and it should appear in your application menu/ Dash.  (You may need to log out and back in for that to happen.) You can also just place it in any old location (i.e., your desktop) and run it by double clicking.

---

