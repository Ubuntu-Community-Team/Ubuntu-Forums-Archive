---
title: "Panel always runs Nautilus as root"
date: 2011-02-16
forum: Desktop Environments
---

### Post by gavofyork on 2011-02-16
Hello all,

I have a strange problem with GNOME Panel - using it to open a folder  (either via Alt-F2 or the Places menu) causes it to execute "gksu nautilus" rather than plain "nautilus". As such I get asked for my password and the folder is eventually opened as root.

Opening a folder via the Desktop or Nautilus itself has the normal effect.

What's going on and how can I fix the configuration?

Insights appreciated!

Gav.

---

### Post by Krytarik on 2011-02-17
Check the options for "inode/directory" in the file "~/.local/share/applications/mimeapps.list", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

---

### Post by pranavashok on 2011-07-19
Thanks Krytarik! I had the same problem for ages and finally it's a relief to get rid of it! :)

---

