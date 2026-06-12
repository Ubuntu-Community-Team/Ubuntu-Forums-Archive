---
title: "Desktop icon won't change."
date: 2018-09-14
forum: Desktop Environments
---

### Post by mark199 on 2018-09-14
[COLOR=#000000]Firstly if I'm duplicating anything I apologise. I've tried searching and can't find anything so I don't think I am.[/COLOR]

[COLOR=#000000]I run UBUNTU 16.04 lts.
[/COLOR]I have a number of icons on the Gnome desktop, some of which have their icons changed by background scripts to give me status information on various systems.
[COLOR=#000000]I have a problem with the icon for one of my desktop launchers which refuses to change.[/COLOR]
[COLOR=#000000]I have edited the .desktop file and it won't change.[/COLOR]
[COLOR=#000000]I have gone into the properties and selected a totally different icon and it won't change.[/COLOR]
[COLOR=#000000]I have three background process which each automatically changes the icons for some of 15 desktop launchers and all work perfectly except for this one.[/COLOR]
[COLOR=#000000]I have deleted the .desktop file and re created it by copying and editing a working one but to no avail.[/COLOR]
[COLOR=#000000]I have rebooted the system several times (not just for this)[/COLOR]

[COLOR=#000000]It's starting to dive me mad. Can anyone advise what else I can do?[/COLOR]

---

### Post by ajgreeny on 2018-09-14
We might be able to help  more if you told us what changes you want to make and what the text content of the .desktop file is at the moment, otherwise we are just stabbing in the dark.

---

### Post by mark199 on 2018-09-17
Not a problem. The text of the file is 
#!/usr/bin/env xdg-open


[Desktop Entry]
Version=0.0
Encoding=UTF-8
Name=ONN7
Type=Application
Terminal=false
Exec=/usr/local/bin/onn7
Icon=/home/mark/Desktop/.onn_icons/nno8200.png

It is the name of the icon png file that is changed by the script. That is working but the desktop refuses to show the change.
As I said, it makes no difference how this line is changed, by script, by manual edit in vi or by selecting an icon in the preferences GUI. The file takes the change but the desktop refuses to show it.

---

