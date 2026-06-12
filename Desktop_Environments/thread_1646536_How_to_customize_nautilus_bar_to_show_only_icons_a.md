---
title: "How to customize nautilus bar to show only icons and no texts"
date: 2010-12-16
forum: Desktop Environments
---

### Post by manmath on 2010-12-16
Please somebody help me how to customize nautilus toolbar to show only icons and no text.

For example, currently my nautilus toolbar looks like the attached Screenshot.png
I want to remove those "Back" and "Forward" text strings to make it look like the attached Screenshot2.png

---

### Post by mcduck on 2010-12-16
I'm not sure if there's a way to change this only for Nautilus, but if you are OK with changing the toolbar style for all applications, here's how to do it:

* Press Alt-F2 and run "gconf-editor" (or run it from terminal, whatever you prefer)

* Browse to desktop/gnome/interface

* change the "toolbar_style"-key's value to "icons"

---

### Post by manmath on 2010-12-16
Thanks mcduck! Your tips worked.

---

