---
title: "Main Menu&gt;Places&gt;*  doesn't open"
date: 2010-11-06
forum: Desktop Environments
---

### Post by fester225 on 2010-11-06
When I go to Main Menu>Places, nothing but Computer and Network works correctly. Choosing Main Menu>Places>Downloads, for instance, generates a little disk activity, but never displays a window with the contents of the Downloads directory.

In an effort to fix the problem, I just upgraded from 10.4 to 1.10, but the same thing still happens.

How do I get the Main Menu>Places icons to display the appropriate windows?

---

### Post by different_guy on 2010-11-06
Try to use terminal. If your desired folder is, for example, under home directory, type: cd/home/folder_name.

Hope it helps.

---

### Post by wojox on 2010-11-06
Reset the panel

```
rm -rf ~/.gconf/apps/panel
```

---

### Post by fester225 on 2010-11-06
> **wojox said:**
> Reset the panel

```
rm -rf ~/.gconf/apps/panel
```


I just tried that. Most of my Place icons still don't work, and all my Gnome Panel displays are gone. Oh well...

It was worth the try!

---

### Post by wojox on 2010-11-06
Open your /home folder and go to /.config/user-dirs.dirs

It should look something like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
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

Gnome Panel displays are gone log out and back in.

---

### Post by fester225 on 2010-11-06
The file you posted is identical to the one I have.

The problem remains. Any ideas?

---

### Post by wojox on 2010-11-07
Open Nautilus and then go to Bookmarks-> Edit Bookmarks. See if that does anything. Anything in Places is a bookmark and is dynamic.

---

