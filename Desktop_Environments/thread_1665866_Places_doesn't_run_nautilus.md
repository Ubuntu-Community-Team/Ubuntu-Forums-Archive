---
title: "Places doesn't run nautilus"
date: 2011-01-12
forum: Desktop Environments
---

### Post by akxiii on 2011-01-12
Weird problem.
The first set of links under Places in the menu bar applet open Picasa instead of nautilus and their associated folders.

List of items that aren't linking properly
[LIST]
[*]Home Folder
[*]Desktop
[*]Bookmarks
[LIST]
[*]Pictures
[*]Music
[*]Documents
[/LIST]
[/LIST]

I tried reapplying the applet from the "add to panel" menu. No go. Also when I get into nautilus (using "computer" below the separation line in the places menu) I can access the bookmarks just fine.

Any thoughts?

notes:
ubuntu 10.04
wine 1.2
picasa 3.8

---

### Post by oldos2er on 2011-01-12
Right-click on a folder (if none exist on the desktop, create one), Open with, Other application, scroll down, choose Open folder.

Or, run *nano .local/share/applications/mimeapps.list*, look for the inode/directory entry and make sure it references only nautilus-folder-handler.desktop, or has the nautilus-folder-handler.desktop listed first.

Both methods accomplish the same task.

---

### Post by akxiii on 2011-01-13
awesome, thanks mate. I wouldn't have guessed that solution. Worked like a charm

---

