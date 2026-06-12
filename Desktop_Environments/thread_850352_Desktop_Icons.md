---
title: "Desktop Icons"
date: 2008-07-05
forum: Desktop Environments
---

### Post by nooblot on 2008-07-05
hi, 2 questions:

1) How to customize the display of Desktop icons ?
e.g. I don't want big fat file thumbnail like below.....Windows-style icon look suits me fine.

[img]http://img67.imageshack.us/img67/2100/screenshothl0.png[/img]

2) Default Desktop icons --- After fresh-install of 8.04, I get a BLANK Desktop, is this a "new" thing with Hardy ? 
How can I get back the default icons ?

thanks

---

### Post by ingvildr on 2008-07-05
1) Open the File Manager then go to Edit>Preferences>Preview and changes the options as desired.

2) Ubuntu has never had icons on the desktop by default, apart from other partitions/external drives etc.

---

### Post by sayakb on 2008-07-05
1. That is a video file. You should already have the preview for Videos enabled by default.

2. Press Alt+F2 and type in **gconf-editor. **Navigate to /apps/nautilus/desktop and **check** computer_icon_visible, home_icon_visible, trash_icon_visible etc.

---

