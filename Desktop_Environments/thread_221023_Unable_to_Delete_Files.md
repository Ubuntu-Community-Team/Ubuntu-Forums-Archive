---
title: "Unable to Delete Files"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Magefire on 2006-07-22
I recently tried downloading the OGRE 3D engine for Linux since I wanted to see if I could start developing for Linux as well as Windows however, when it failed to build, I decided to delete it and try again later when I had more time.  I was able to move it into the trash and delete most of the files and folders but I couldn't delete all of it because I didn't have permission to delete one of the folders, "autom4te.cache".  The folder seems to be owned by root.  From my limited experience with Linux, it seems to do a good job of preventing users from deleting important files but since this undeletable folder appears in a folder I created in my home directory, I thought it would be OK to delete it.  Is there a way I can delete it or is this something I shouldn't delete?

Thank you for considering my question.

---

### Post by aysiu on 2006-07-22
If you're in Gnome, Alt-F2 ```
gksudo nautilus
``` and then delete the file.

If you're in KDE, use ```
kdesu konqueror
``` instead.

---

### Post by Magefire on 2006-07-22
Thank you for your help.  This solved my problem.

---

