---
title: "Menu Entry"
date: 2006-06-24
forum: Desktop Environments
---

### Post by dfego on 2006-06-24
I just installed gtodo on my system, and was expecting a menu entry to exist (under Office), but none does.  Thinking I could fix it up with Alacarte, I went in there, and the box was already checked for the icon.  I unchecked, rechecked, restarted, all sorts of things, but the icon just doesn't want to show up.  Does anyone have any idea what's going on?

---

### Post by ajgreeny on 2006-06-24
Not sure what you mean by "the box was already checked for the icon"  Do you mean there was an entry for the prog without an icon, or no menu entry for the prog at all?

---

### Post by aysiu on 2006-06-24
I think dfego means in the menu editor there *appears* to be an entry, but in the actual menu itself there isn't.

---

### Post by dfego on 2006-06-24
Yeah, there's an entry in Alacarte, and the box I'm referring to is the one that says that it should show up in the real menu.  However, whether the box is checked or not, the icon doesn't appear in the real menu (but it does show up in Alacarte).

---

### Post by aysiu on 2006-06-24
This probably won't help at all, but try this: Alt-F2 ```
killall gnome-panel
```

---

### Post by dfego on 2006-06-25
[QUOTE=aysiu]This probably won't help at all, but try this: Alt-F2 ```
killall gnome-panel
```[/QUOTE]

Thanks for the idea, but you were right, it didn't help. :p

---

### Post by aysiu on 2006-06-25
Have you tried unchecking the box and then just creating a new entry for it--same command, same icon?

---

### Post by dfego on 2006-06-25
[QUOTE=aysiu]Have you tried unchecking the box and then just creating a new entry for it--same command, same icon?[/QUOTE]

Hey, thanks, good idea, and I totally didn't think of it (and it works!)  I'm curious why the other way didn't work, but it's not such a big deal now.

---

