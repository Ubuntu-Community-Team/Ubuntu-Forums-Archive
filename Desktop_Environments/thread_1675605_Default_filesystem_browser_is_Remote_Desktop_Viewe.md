---
title: "Default filesystem browser is Remote Desktop Viewer?"
date: 2011-01-25
forum: Desktop Environments
---

### Post by johan851 on 2011-01-25
I apologize if this is a bit of a noob question - I've tried searching around, and I can't really figure out why I'm having this issue.

Whenever I try to open a folder or some other location on disk through any program, I get the Remote Desktop Viewer.  For example, if I go to Places --> Home Folder, the RDV opens up and says "the connection to /home/<me>" is closed.  It's very odd.  I get the same behavior in Chromium if I select "Show in Folder" for a download.

If I go to the terminal and type 'xdg-open ~' or 'gnome-open ~' I also get the Remote Desktop Viewer, just like I do when I select home from the Places menu.

Any ideas on how to fix what got overridden?  Thanks!

---

### Post by johan851 on 2011-01-27
Bump.  No one has any ideas?

---

### Post by Krytarik on 2011-01-27
Open the file "~/.local/share/applications/mimeapps.list" ("~" is your home directory) and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

---

### Post by johan851 on 2011-01-28
Thanks!  I opened it up, and the only entry is this:

> inode/directory=vinagre.desktop;

I changed it to what you said, and now it's fixed.  There are way too many places for all these settings to live.  Thanks for the help!

---

