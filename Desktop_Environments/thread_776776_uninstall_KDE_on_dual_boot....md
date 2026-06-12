---
title: "uninstall KDE on dual boot..."
date: 2008-04-30
forum: Desktop Environments
---

### Post by maxclimber1w on 2008-04-30
hello there! I run ubuntu 8.04 on my toshiba laptop, but I first installed Kubuntu on this machine and so log in from the KDE screen. I also use several KDE programs on my Gnome desktop, notably Amarok and Kaffeine. I would like to uninstall KDE, but I am afraid that I will lose all my meticulous Amarok playlists and data. Will this happen?

How should I go about this?

---

### Post by Zorael on 2008-05-01
It doesn't work quite as it does in Windows. :>

Your own settings are saved under your home directory, so while Amarok may be removed if you remove the kubuntu-desktop metapackage, your user-specific settings and saved playlists should remain.

Actually, if you make a backup of your /home/username, you could format the entire partition and then restore your settings by copying the old content into your new home directory. I keep my /home on a dedicated partition, so I'm free to toy around with the root partition without dangering my users' settings.

---

