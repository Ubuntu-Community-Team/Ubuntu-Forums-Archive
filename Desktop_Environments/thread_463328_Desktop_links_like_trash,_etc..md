---
title: "Desktop links like trash, etc."
date: 2007-06-03
forum: Desktop Environments
---

### Post by linfidel on 2007-06-03
Before I reinstalled Ubuntu for my new motherboard, I had found a place where I could enable certain desktop links like the trashcan that's usually on the panel, the computer browser (like Window's "My Computer"), etc.  I thought it was in the Gnome configuration tool, but I've searched long, hard, deep, and continuously, but can't find it.  I think I may be going insane, and I'm hoping someone has a clue and can save me.  :)

---

### Post by WiFi Ed on 2007-06-03
From terminal: gconf-editor

Then, drill down through apps/nautilus/desktop and check the boxes for the desktop icons you want.

---

### Post by linfidel on 2007-06-04
That's it!  Thank you.  Now I know I'm not totally crazy.  I though I looked everywhere, but I guess I missed a few.

---

### Post by WiFi Ed on 2007-06-04
Glad to help!

You can add it to your System Tools menu too. Right-click on Applications/choose Edit Menus/click on System Tools and the check the Configuration Editor box in the right-hand pane...

---

### Post by linfidel on 2007-06-04
Thanks, I had already done that.  I was doing something else in the menu editor, and came across it.  It used to be enabled, I believe.  The manual refers to it on a menu, but that menu was missing when I first looked.

---

