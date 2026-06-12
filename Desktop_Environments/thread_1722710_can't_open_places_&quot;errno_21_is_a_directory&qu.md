---
title: "can't open places: &quot;errno 21 is a directory&quot;"
date: 2011-04-06
forum: Desktop Environments
---

### Post by anelim on 2011-04-06
Hi guys, 

Does anyone know how to solve this? All of a sudden I can't open any directory in Places: I get an error message saying [errno 21] Is a directory" followed by the name of the directory that I'm trying to open
in Ubuntu 11.04

This error first popped up in one small subdirectory when I used Bazaar today; I recently installed it and it has been working OK until now.

(I can still access everything via desktop shortcuts)

Many thanks!

---

### Post by Krytarik on 2011-04-06
Check if this is related to this one:

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
If that's the case, see here about what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by anelim on 2011-04-09
Thanks!

The mimeinfo.cache file said exactly that.  The problem was fixed when I then followed the advice in the thread you linked to: click on "open with" on a random folder on the desktop, choose "File browser", tell it to "remember this application". Seems like it is a simple issue with file association which had puzzled me for a week!

I'm not closing this thread just yet in case things mess up again...

---

