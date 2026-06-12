---
title: "xubuntu 14.04: launcher items are not updated?"
date: 2015-01-12
forum: Desktop Environments
---

### Post by edgue on 2015-01-12
Hello there,

I have some "handmade" launcher files, like

> cat /usr/share/applications/eclipse-trunk.desktop 
[I][Desktop Entry]
Version=1.0
Type=Application
Name=Eclipse [trunk]
Comment=Eclipse Luna R [trunk workspace]
Exec=/opt/eclipse-luna/eclipse -configuration /data/home/eclipse-work/configuration -data /data/home/eclipse-work/workspace-trunk
Icon=/opt/eclipse-luna/icon.xpm
Path=/data/home/eclipse-work/workspace-trunk
Terminal=false
StartupNotify=false
[/I]

Today I made some updates to this desktop file. Afterwards, I ran "sudo update-desktop-database".

When I now turn the "xfce launcher" (I click the little mouse icon, and type "eclipse" in the search field; 
"Eclipse [trunk]" shows up; and when clicking there, all right: it uses the updated .desktop file.)

But: i also have a panel with a number of launcher entries. One of the launchers is configured to run this "Eclipse [trunk]" program ...
but when I click on the icon in the panel ... it tries to invoke the "old" version of the desktop files.

So, long story short: it seems that "update-desktop-database" does not affect any xfce-panel launcher objects.
Do I really have to turn to each launcher object manually in order for the launcher to use the new .desktop file?

---

### Post by kerry_s on 2015-01-12
yeah, the panel launcher settings are kept in a different kind of settings file. just remove the old 1 & add the new 1.
the panel launcher doesn't do any searching, there pretty much a static file.

---

