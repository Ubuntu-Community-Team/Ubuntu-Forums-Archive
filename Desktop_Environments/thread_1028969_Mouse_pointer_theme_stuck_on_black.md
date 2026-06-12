---
title: "Mouse pointer theme stuck on black"
date: 2009-01-02
forum: Desktop Environments
---

### Post by thaidog on 2009-01-02
For some reason the default mouse pointer theme is stuck on black. If I choose to change the mouse theme it will change over windows like firefox but as soon as I move the cursor over the desktop it changes color back to black.

This is very annoying... anybody know how to fix it?

---

### Post by Dareth on 2010-06-02
I have the same problem, but with the colors reversed.

---

### Post by xlv1000 on 2010-06-02
press: alt+F2 
type: ```
gconf-editor
```
go to: desktop> gnome>peripherals> mouse>
find the line:cursor_theme
right clik and press :edit key 
now you must write the name of the cursor key as it shows at: preferences> appearence> Pointer

If this dosn't work try this:

open terminal and write:
```
gksu nautilus
```

go to :usr> share> icons> default> index theme

open whith gedit 
the line must be:
Inherits=My_cursor_theme

where My_cursor_theme is the name of the cursor theme as it shows at preferences> appearence> Pointer

---

