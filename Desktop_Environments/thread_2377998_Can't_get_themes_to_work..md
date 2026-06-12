---
title: "Can't get themes to work."
date: 2017-11-18
forum: Desktop Environments
---

### Post by Hewjr100 on 2017-11-18
Having problems with Ubuntu 17.10 and themes.  I have no problem extracting and copying icon themes to .icons.  The problem is with gnome-shell and gtk 3 themes.  I have extracted these themes to .themes and even to usr*/s*hare/themes, but they just do not show up in tweaks.  Default show nothing and none just opens up folders like it’s looking for something.  All Google results say the same thing.  What am I doing wrong.
 
 
 Henry

---

### Post by Frogs Hair on 2017-11-18
Try  restarting if you haven't since the themes were installed . Other reasons themes may not show up in the tweak tool include  themes not being fully extracted from the parent folder and also GTK compatibility .  For example, a GTK 3.16 theme may not work at all with a Gnome 3.24 based OS. Also be sure you have the user themes extension installed and enabled in the tweak tool. Restart after installing these extensions.

```
sudo apt install gnome-shell-extensions 
```

---

### Post by Hewjr100 on 2017-11-18
Working on it now, just gotta wait till my movies over.  Let you know in about an hour.

Henry

---

