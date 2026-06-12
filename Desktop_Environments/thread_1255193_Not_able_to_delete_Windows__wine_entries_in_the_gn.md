---
title: "Not able to delete Windows / wine entries in the gnome menu"
date: 2009-09-01
forum: Desktop Environments
---

### Post by cdysthe on 2009-09-01
Hi,

There are a couple of Windows / wine items in my Gnome menu I am not able to remove with the menu editor "alacarte". They are leftover from wine not unintalling correctly. When I highlight them and hit "Delete" nothing happens. It looks like all wine entries are added differently than other items in the /home/me/.config/menu folder, but I am not able to figure out how to delete the items manually from there. Is there another way to remove these items? I do not mind having to edit files manually, but I do not want to "experiment" and totally break my menu which otherwise works fine.

---

### Post by alienclone on 2009-09-01
if you right click on the menu button on the gnome panel and select edit menu you should be able to uncheck the items you dont want to show.

---

### Post by cdysthe on 2009-09-01
> **alienclone said:**
> if you right click on the menu button on the gnome panel and select edit menu you should be able to uncheck the items you dont want to show.


Thanks, but I was wondering how to remove them all together. Are you saying that's not possible?

---

### Post by alienclone on 2009-09-01
sorry i dont know if it is possible, i just assumed "out of sight, out of mind" would be sufficient.

---

### Post by cdysthe on 2009-09-01
> **alienclone said:**
> sorry i dont know if it is possible, i just assumed "out of sight, out of mind" would be sufficient.

I'm a "neat-freak" on my dekstop, so I would prefer to be able to remove it. Thanks again! :)

---

### Post by Swagman on 2009-09-01
That's actually something I would like to know as it bugs me as well.

---

### Post by kubug on 2009-12-28
delete the files in ~/.config/menus/applications-merged and in
~/.local/share/desktop-directories/

---

### Post by cdysthe on 2009-12-28
> **kubug said:**
> delete the files in ~/.config/menus/applications-merged and in
~/.local/share/desktop-directories/

That did the trick! Thanks a lot and Happy New Year :)

---

