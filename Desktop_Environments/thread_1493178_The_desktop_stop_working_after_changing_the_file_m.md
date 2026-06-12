---
title: "The desktop stop working after changing the file manager"
date: 2010-05-25
forum: Desktop Environments
---

### Post by He3aBuCuM on 2010-05-25
Hi all. Well, i wanted to change my default file browser, but my desktop stoped working(except the panels).
I did backup files of the ones which i modify, but when i backup the files, the desktop don't work again.

The files, which i modify were:
/usr/share/applications/nautilus-computer.desktop
and
/usr/share/applications/nautilus-folder-handler.desktop

But now, these files are default.
Well, there are the files:
nautilus-computer.desktop:
```
[Desktop Entry]
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this comp$
TryExec=nautilus
Exec=nautilus --no-desktop computer:
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus
```nautilus-folder-handler.desktop:
```
[Desktop Entry]
Name=Open Folder
TryExec=nautilus
Exec=nautilus --no-desktop %U
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;a$
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus

```

---

