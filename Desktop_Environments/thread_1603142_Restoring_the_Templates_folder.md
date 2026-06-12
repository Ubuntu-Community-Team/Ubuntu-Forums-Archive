---
title: "Restoring the Templates folder"
date: 2010-10-22
forum: Desktop Environments
---

### Post by sidewalkcynic on 2010-10-22
As usual, when I install the new version of UBUNTU I throw those folders out that come with it. Well, I didn't throw them all out this time, but I did trash the Templates, and now I thought of an experiment to try with it, but it doesn't restore by just creating a folder - so, how do I restore it?

---

### Post by Morbius1 on 2010-10-22
See if the following line exists in **/home/username/.config/user-dirs.dirs** :

```
XDG_TEMPLATES_DIR="$HOME/Templates"
```If it's not there then add it and logoff and on again.

---

### Post by sidewalkcynic on 2010-10-22
Looks like it's there - thanks

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/2. Desktop"
XDG_DOWNLOAD_DIR="$HOME/0. Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/3. Personal/Pictures"
XDG_VIDEOS_DIR="$HOME/3. Personal/Videos"
```

---

### Post by Morbius1 on 2010-10-22
But:
>  XDG_TEMPLATES_DIR="$HOME/"
Isn't pointing to the "Templates" folder.

---

### Post by tiznom on 2012-01-13
> **Morbius1 said:**
> See if the following line exists in **/home/username/.config/user-dirs.dirs** :

```
XDG_TEMPLATES_DIR="$HOME/Templates"
```If it's not there then add it and logoff and on again.

Worked perfectly, thanks. I didn't even have to log out, it took effect right away.

---

