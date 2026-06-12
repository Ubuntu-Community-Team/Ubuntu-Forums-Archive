---
title: "broken sidebar"
date: 2013-01-04
forum: Desktop Environments
---

### Post by feynmaniac on 2013-01-04
My sidebar is broken. The buttons are all misaligned and do not slide downwards. The following is a picture of my desktop. Also I was messing around with ls -la and messed dumped my home directory into my desktop :P 

[IMG]https://docs.google.com/file/d/0B1h2-wnNT9AVaWJvWlN6UmxRd1E/edit[/IMG]

---

### Post by feynmaniac on 2013-01-04
Actually it's a separate problem but when messing around in an attempt to fix this I seem to have "linked" my home directory to my desktop. So if I delete all of the folders on the desktop, that deletes all of the files in my home directory.

EDIT: Talked to a friend. Apparently I've set my desktop to display my home folder. Any idea how to change this? I solved my Unity problem by just switching to Ubuntu 2d.

---

### Post by zombifier25 on 2013-01-05
Open the file ~/.config/user-dirs.dirs for editing (press Ctrl + H in the file browser to show hidden files), look for this line:
```
XDG_DESKTOP_DIR="$HOME"
```
Change it to:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

