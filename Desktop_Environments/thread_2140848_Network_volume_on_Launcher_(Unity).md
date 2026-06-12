---
title: "Network volume on Launcher (Unity)"
date: 2013-04-30
forum: Desktop Environments
---

### Post by Cammy on 2013-04-30
I have two network drives that I wanted pinned to the launcher in Unity.  When I first mounted them, they both automatically appeared, but soon after, one of them vanished.

In .local/share, I created two .desktop files (mediashare.desktop and mediadata.desktop), edited them in gedit, then dragged them to the launcher.  Problem solved.

Well, not quite.

Whenever I click any nautilus icon on the launcher, whether it's mediadata, mediashared, or the stock "Files" icon, the icon that gets highlighted as the active icon is the mediadata one.

The contents of the .desktop file are:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Network (Data)
Comment=Network (Data)
Exec=nautilus /media/data
Icon=folder-remote
X-Ubuntu-Gettext-Domain=mediadata
```

Is there anything in here that could cause this icon to be the one that's ALWAYS highlighted as the active item?

---

