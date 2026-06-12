---
title: "Nautilus Toolbar Buttons?"
date: 2010-08-08
forum: Desktop Environments
---

### Post by benerickson1 on 2010-08-08
Hi. Is it possible to remove text from the Nautilus main toolbar? I would like to see the buttons only, with no words such as "Back" and "Forward". Thanks, this is kinda driving me nuts.

---

### Post by benerickson1 on 2010-08-08
I solved this by getting Nautilus Elementary.  Still wondering though, anyone know how you're "supposed" to do this? Trying to display icons only, no text, in the main toolbar.

---

### Post by stoian on 2011-08-07
Hey, perhaps you already found out the answer, but I'll post it anyway for other people who wish to customize their toolbars in Nautilus and other apps, too.

From [http://mitchtowner.net/?p=609]("http://mitchtowner.net/?p=609"):

In gnome/ubuntu using the menu, navigate to Applications > System Tools > Configuration Editor.

Once in there, locate this key:

```
/desktop/gnome/interface/toolbar_style
```

Change its value to one of these: "both", "both-horiz", "icons", or "text".

If you want only icons on toolbars, use "icons" (without quotes, of course).

---

