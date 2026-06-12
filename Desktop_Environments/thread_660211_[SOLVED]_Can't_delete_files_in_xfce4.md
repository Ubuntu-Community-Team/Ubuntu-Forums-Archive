---
title: "[SOLVED] Can't delete files in xfce4"
date: 2008-01-06
forum: Desktop Environments
---

### Post by PurposeOfReason on 2008-01-06
For example, in xfce4, when I  try to delete a file, I get:

Failed to copy "/home/shawn/2008-01-06-113905_1280x800_scrot.png" to "trash:///2008-01-06-113905_1280x800_scrot.png".
Failed to open "/home/shawn/.local/share/Trash/info/2008-01-06-113905_1280x800_scrot.png.trashinfo" for writing.

Do you want to skip it?


I didn't have this problem when I still had gnome installed.

---

### Post by urukrama on 2008-01-06
Perhaps the folder permissions are set wrongly? Do you have read/write permission for that folder?

---

### Post by PurposeOfReason on 2008-01-06
I wouldn't see why but I did a chown -R to ~/.local and it fixed it. Thread solved.

---

