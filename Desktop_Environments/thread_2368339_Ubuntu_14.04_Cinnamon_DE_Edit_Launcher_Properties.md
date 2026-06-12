---
title: "Ubuntu 14.04 Cinnamon DE Edit Launcher Properties"
date: 2017-08-09
forum: Desktop Environments
---

### Post by Redalien0304 on 2017-08-09
Trying edit a Launcher Properties of Gparted 25 Launcher in the Cinnamon Menu. Or change the Name of Gparted 25 to Gparted 29. Had Gparted 25 Installed, Installed Gparted 29 from Source code.
I know i can add it to the Panel easy & Change the Name to Gparted 29, but not in the Cinnamon menu.

Thanks in Advance.

---

### Post by ajgreeny on 2017-08-09
Look for the .desktop file for gparted, probably in /usr/share/applications or possibly also in ~/.local/share/applications and edit them.

Mine in /usr/share/applications contains
```
[Desktop Entry]
Name=[COLOR="#FF0000"]GParted[/COLOR]
GenericName=Partition Editor
X-GNOME-FullName=GParted Partition Editor
Comment=Create, reorganize, and delete partitions
Exec=gparted-pkexec
Icon=gparted
Terminal=false
Type=Application
Categories=GNOME;System;Filesystem;Settings
Keywords=Partition;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gparted
``` and just edit the title (in red) to whatever you wish it to show.

---

### Post by Redalien0304 on 2017-08-09
k worked thanks

---

