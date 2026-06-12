---
title: "Hide text for desktop icons"
date: 2008-10-20
forum: Desktop Environments
---

### Post by Meson on 2008-10-20
I think it's really unnecessary to have text under my desktop icons.  I only have a few and the icon itself just fine.  Is there a way to hide the text under my icons (gnome)?

---

### Post by Hangwire on 2008-10-20
#aptitude install -P gconf-editor

now go to Applications->System Tools->Configuration Editor. In the application appeared navigate through the tree to /apps/nautilus/preferences and check (or uncheck) the show desktop option. This will show (checked) or hide (unchecked) desktop icons.

---

### Post by Meson on 2008-10-20
Thanks.  Yeah I have the config editor.  I looked through it for a while.  What I want is to hide the icon text, not the entire icon.

---

### Post by benerivo on 2008-10-20
Open gconf-editor, and go to apps>nautilus>preferences and change the desktop font to 0 (eg. change it from Sans 10 to Sans 0), then there's no text visible.

---

### Post by Meson on 2008-10-20
Ah, nice hack

---

### Post by ghostbit on 2008-11-12
Nice hack... but it "removes" the text from all icons.
Another trick is to make a text executable file - a script, name it with "spaces" (this trick doesn't work anymore with *.desktop files for instance) and set the nautilus preference to run them when they are opened. In the end change the icon. Thats it :)

---

### Post by nufros on 2008-11-21
That's just what my desktop needed! :)

---

