---
title: "Hiding servers on desktop"
date: 2006-06-12
forum: Desktop Environments
---

### Post by lean on 2006-06-12
Hello,
I was wondering if it is possible to hide the server icons on the desktop. I just connect to servers and use them as bookmarks from the places menu. But there is also an icon on the desktop. Is it possible to hide the icons on the desktop but keep them in the places menu?

---

### Post by mannheim on 2006-06-12
You can hide the servers **and** the other mounted volumes by setting on option in gconf. So if you don't mind hiding them all, launch gconf-editor (from the command-line, say). Then navigate in gconf-editor to apps-->nautilus-->desktop. Uncheck the item "volumes_visible".

---

