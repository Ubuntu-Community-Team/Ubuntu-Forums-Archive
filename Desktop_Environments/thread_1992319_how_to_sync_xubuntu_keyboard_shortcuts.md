---
title: "how to sync xubuntu keyboard shortcuts"
date: 2012-05-31
forum: Desktop Environments
---

### Post by cedardoc on 2012-05-31
I've settled on xubuntu for most of my computers (home and work) and am starting to add many keyboard shortcuts (bash scripts + xdotool / wmctrl) instead of using autokey...

is there a single file somewhere that contains all the keyboard shortcuts I could sync (rsync) , or better yet, is there a way to point to a keyboard shortcut file in dropbox and any changes would sync automatically?

thanks,
Dave

---

### Post by LewisTM on 2012-05-31
The file is ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml

I tried to place it in Dropbox and then made a symlink but that didn't work. Pretty much all Xfce config files are kept in memory, any change will result in overwriting the file (or link). Maybe Ubuntu One might work. 

What could work would be to store the entire xfce-perchannel-xml directory on Dropbox and symlink it but that would mean sharing ALL settings between computers, not just shortcuts.

Cheers!

---

