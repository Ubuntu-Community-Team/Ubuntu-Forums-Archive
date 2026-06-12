---
title: "Gnome ticks (Dock &amp; Files icons)"
date: 2024-05-26
forum: Desktop Environments
---

### Post by currentshaft on 2024-05-26
1

---

### Post by tea for one on 2024-05-26
> **currentshaft said:**
> The Files/Nautalis sidebar can't be modified. I can't rearrange the list, remove unused folders like "Music" and "Videos", nor add my own shortcut for Desktop, for example.
Surely I'm just missing some hidden config?
Is this the file you wish to edit?
```
~/.config/user-dirs.dirs
```
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```
Edit: I've just tried to edit this file and failed miserably.
Apologies for misleading you

---

### Post by tea for one on 2024-05-26
Have a look at post 8 option 1 here [https://forums.linuxmint.com/viewtopic.php?t=364944](https://forums.linuxmint.com/viewtopic.php?t=364944)
I played around with the suggestion and seems OK.
The beauty is that it's quite easy to revert to defaults by re-editing /etc/xdg/user-dirs.conf
Anyway, see what you think.

---

### Post by Dennis N on 2024-05-26
> 1. The dock has two permanent "SSD" icons for "zpool" and "rpool". They cannot be removed (the only options are to "mount" them). Why can't I have control over what is in my own dock?

If these zpool and rpool things are considered by the system to be "volumes" or "devices" you can hide them with a setting in: 

Settings > Ubuntu Desktop > Dock > Configure Dock Behavior

---

### Post by currentshaft on 2024-05-26
l

---

### Post by currentshaft on 2024-05-28
1! !

---

