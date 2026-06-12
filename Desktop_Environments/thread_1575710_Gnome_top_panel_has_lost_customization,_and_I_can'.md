---
title: "Gnome top panel has lost customization, and I can't repair this"
date: 2010-09-16
forum: Desktop Environments
---

### Post by tw77 on 2010-09-16
I just logged onto Ubuntu, and my top panel looks like the screenshot attachment.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169626&stc=1&d=1284627417[/IMG]

I cannot seem to change the order of items in this panel, nor can I add or delete any.

Does anyone have any ideas?

Thanks


(ps. first post :) )

---

### Post by ajgreeny on 2010-09-16
Open up the file manager (nautilus) for your home folder, hit Ctrl + H to show hidden files and folders.

Now navigate to **.gconf/apps/** and in the right hand pane of nautilus, right click on **panel** and rename it to **panelbackup**.

Now logout and back in again, and you should find your panel is back to the default.  My only uncertainty is whether or not the netbook desktop follows the same path in .gconf as a standard gnome desktop.  Try it and come back again if needed.

---

