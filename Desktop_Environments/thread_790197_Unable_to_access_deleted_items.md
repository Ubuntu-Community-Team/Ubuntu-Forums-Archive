---
title: "Unable to access deleted items"
date: 2008-05-11
forum: Desktop Environments
---

### Post by marxian on 2008-05-11
I am currently unable to access the deleted items folder in Hardy. The icon has disappeared from the panel, and I cannot restore it. When I try to add it to the panel, nothing happens. I can add other items without any problems. Also, I cannot open the deleted items folder using the folder browser. Any suggestions will appreciated.

---

### Post by HJB on 2008-05-11
Try to:
cd ~/.local/share/Trash/files
they should all be there.

/usr/lib/kde4/bin/ktrash4 --restore <file>  should restore a trashed file to its original location and --empty will do the obvious.
Hope this helps in the mean time until someone can fix the trashcan on the Desktop...
Bye

---

