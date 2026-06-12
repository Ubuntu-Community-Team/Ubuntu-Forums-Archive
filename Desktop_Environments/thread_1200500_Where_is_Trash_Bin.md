---
title: "Where is Trash Bin"
date: 2009-06-30
forum: Desktop Environments
---

### Post by raunhar on 2009-06-30
Ubuntu 9.04
Unable to locate the Trash Bin on the Desktop.

---

### Post by masux594 on 2009-06-30
=| On the bottom-right corner of the screen?

Sysc, A

---

### Post by raunhar on 2009-06-30
Not visible. I have checked the whole screen.

---

### Post by Sigurd Suhm on 2009-06-30
If you open Places->Computer it should be on the list on the left side of the screen. If not the files should be in the ~/.local/share/Trash/ subfolders.

---

### Post by raunhar on 2009-06-30
Got it.
Can it be brought to its regular position. Right down corner

---

### Post by mcduck on 2009-06-30
Yes, just right-click in empty spot in your panel, select "Add to Panel", find the "Trash"-applet and drag&drop it into your panel.

Or, if you prefer having it on the desktop, press Alt-F2 and run "gconf-editor", browse to apps/nautilus/desktop and enable "trash_icon_visible"

---

