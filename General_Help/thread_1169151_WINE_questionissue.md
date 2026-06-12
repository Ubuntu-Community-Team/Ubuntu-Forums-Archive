---
title: "WINE question/issue"
date: 2009-05-24
forum: General Help
---

### Post by kulturloseramerikaner on 2009-05-24
There are several programs that I've installed then later removed using WINE.  Every one of these uninstalled programs shows up in WINE's "Programs" folder still, but they're no longer in the fake "C" drive.  What do I need to do to get those programs off the list?

---

### Post by lovinglinux on 2009-05-24
Remove the applications launchers from these directories:

~/.local/share/applications/
~/.local/share/desktop-directories/

---

### Post by Kareeser on 2009-05-24
You can edit the menu items yourself with the command "alacarte"

---

### Post by lovinglinux on 2009-05-25
> **Kareeser said:**
> You can edit the menu items yourself with the command "alacarte"

But it doesn't delete Wine programs. That's why you need to delete the files manually.

---

### Post by kulturloseramerikaner on 2009-05-27
Thanks for the input; I'll give that a go tomorrow and post back.  I just realized it's 1 in the morning... :-o

---

### Post by kulturloseramerikaner on 2009-06-09
I had to leave town suddenly and haven't gotten to this until tonight.  I tried going into the /.local/share directory, but there were no applications or desktop-directories folders, only 'trash.'

---

