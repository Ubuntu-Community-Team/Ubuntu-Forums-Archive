---
title: "Delete all the panels"
date: 2009-11-25
forum: Desktop Environments
---

### Post by Nistenf on 2009-11-25
I installed AWN, so I deleted the bottom panel. I then added the system tray and everyrhing I need to the dock so I don't want the top panel, but it won't let me delete it. Is thera a way to do so? Also, if I want to create a new panel while having no one, how can I do?

---

### Post by Nistenf on 2009-11-25
I just found a way. I changed the entry in gconf-editor to "gnome-panel.null" It doesn't start now, but I can't use the alt+F2 shotcut. Disabling the panel this way is harmful? Does it disable anything else?

Thanks

---

### Post by nothingspecial on 2009-11-25
You are right Alt-F1 and Alt-F2 won`t work. Neither will the notifications.

If you set the autohide size in gconf-editor to 0 it will completely hide the panel. That might be a good alternative. 

Or you could just create a keyboard shortcut to launch a terminal instead of Alt-F2.

I disable the panels by removing gnome-panel from /usr/bin.

---

### Post by Nistenf on 2009-11-25
Setting autohide size to 0 does nothing. It's the same than in 1. But I guess I just won't use alt+F2 or will configure a new shortcut as you said. What kind of notifications don't work?

Thank you for your help

---

### Post by ninjapirate89 on 2009-11-25
I just set mine to 1 pixel, autohide, and set the unhide delay to a fairly large number.

---

