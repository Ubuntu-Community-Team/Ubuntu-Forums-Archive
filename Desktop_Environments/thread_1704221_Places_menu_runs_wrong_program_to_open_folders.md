---
title: "Places menu runs wrong program to open folders"
date: 2011-03-10
forum: Desktop Environments
---

### Post by JohnE1 on 2011-03-10
When I try to open a folder or bookmark from the Places menu, instead of Nautilus opening the folder, the vlc media player is run and then it tries to open the folder. Where is this setting stored? I could not find the problem using gconf-editor.

---

### Post by howefield on 2011-03-10
Try the solution in this thread...

[http://ubuntuforums.org/showthread.php?p=10540863](http://ubuntuforums.org/showthread.php?p=10540863)

---

### Post by Krytarik on 2011-03-10
A more direct solution:

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by JohnE1 on 2011-03-11
> **howefield said:**
> Try the solution in this thread...

[http://ubuntuforums.org/showthread.php?p=10540863](http://ubuntuforums.org/showthread.php?p=10540863)

Thank you!

I was looking in the applications list for Nautilus and it wasn't there. I never noticed, File Browswer, in the list.

---

### Post by JohnE1 on 2011-03-11
> **Krytarik said:**
> A more direct solution:

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

Thank you for pointing out where the setting is stored!

---

