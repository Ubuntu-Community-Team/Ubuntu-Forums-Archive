---
title: "Smeg Menu Editor doesn't show some files"
date: 2005-09-02
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2005-09-02
When I open Smeg Menu Editor, it doesn't show some of the files that are in the menu. Does anybody know what I should do to fix it?
Thank you.

---

### Post by buldir on 2005-09-03
Which programs aren't listed?  You can always look in /usr/share/applications and, using sudo, edit/add/delete those *.desktop entries all you like.  Make backups first! ;-)

When I install k3b from the KDE packages, I create a file called /usr/share/applications/k3b.desktop using sudo, which contains:

```
[Desktop Entry]
Name=CD/DVD Burner
Comment=
Exec=k3b
Icon=gnome-dvd.png
Terminal=false
Type=Application
Categories=Application;AudioVideo;
```
k3b is now visible in the Audio/Video menu list.

---

