---
title: "How to erase &quot;Desktop&quot; entry in Nautilus?"
date: 2007-11-18
forum: Desktop Environments
---

### Post by kr0n1x on 2007-11-18
Hi, i use my Home folder as my desktop.
Then i don't need *~/Desktop* folder (i deleted it)

But i can't delete Scrivania link in Nautilus :( (Scrivania, in italian means Desktop)

look the attached image please.

I can delete *discarica*, *documenti* and *musica* links... (made by me), but can i delete others?

*pasquale* is my home folder, and also my desktop :)

---

### Post by markusf21 on 2007-11-18
what happens when you try

---

### Post by kr0n1x on 2007-11-19
in Nautilus, the link works well.
when i click *Scrivania*, nautilus get me to my home folder.

but... when i save a file from firefox or other web browser...there are 2 links in *Resources*(on the left of file browser):
[I]pasquale
Desktop[/I]

_pasquale_ get me to my home folder. (good)
_Desktop_ doesn't work. when i click it, the selection pass to pasquale. i can't select _Desktop_ then :( neither right click on it. maybe because i deleted my ~/Desktop folder?

---

### Post by Linteg on 2007-11-19
If you have changed the key to use home as desktop in gconf-editor (/apps/nautilus/preferences/desktop_is_home_dir), try looking at ~/.config/user-dirs.dirs, and especially at XDG_DESKTOP_DIR in that file.

---

### Post by kr0n1x on 2007-11-19
this is my file:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/documenti"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
```

i think is all correct :( or not?

---

