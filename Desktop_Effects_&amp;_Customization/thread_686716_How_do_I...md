---
title: "How do I.."
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by wahr on 2008-02-03
How do I make my window borders and pulldown menus transparent like this?
CCSM does a really good job of obscuring the opacity settings..   (thank god the guys aren't developing DRM : P)


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50830&d=1195586805[/IMG]

---

### Post by DaymItzJack on 2008-02-03
Go to your settings manager, click "General Options", go to "Opacity Options"

Hit +Add

for Opacity windows (put something like this): 
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog)
```

for window values, put 75, or whatever you want the transparency to be.

and it should work!

---

### Post by wahr on 2008-02-03
Much appreciated!

Any chance I could get a list of terms for all the major gui elements?

oh.. and one more thing.. that setup has the borders (grab areas with the minimize buttons) translucent but not the interior.. any ideas how to do that?

---

### Post by DaymItzJack on 2008-02-03
> **wahr said:**
> Much appreciated!

Any chance I could get a list of terms for all the major gui elements?

oh.. and one more thing.. that setup has the borders (grab areas with the minimize buttons) translucent but not the interior.. any ideas how to do that?

That's an emerald theme.

According to [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

> Or choose one: unknown, combo, desktop, dialog, dnd, dock, dropdownmenu, fullscreen, modaldialog, menu, normal, notification, popupmenu, splash, toolbar, tooltip, utility

---

