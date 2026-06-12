---
title: "&quot;Computer&quot; icon on desk top unwanted how to delete?"
date: 2010-03-29
forum: Desktop Environments
---

### Post by matter2012 on 2010-03-29
Ubuntu 9.10 i cannot delete this icon called computer off my desktop no matter what i do its really annoying it wont let me move to trash and if i drag it to the trash it says cannot move items to trash,do you want to delete them immediately? and i click delete and it does nothing any help would be appreciated. 
Thanks,
   Matter

---

### Post by coffeecat on 2010-03-29
Press Alt-F2, and type 'gconf-editor' and click 'run'. Now, apps > nautilus > desktop and untick 'computer_icon_visible'.

By the way, the Ubuntu default is not to have the Computer icon showing. You, or an app you installed, must have enabled it.

---

### Post by ajgreeny on 2010-03-29
Use **gconf-editor->apps->nautilus->desktop** and remove the selection to show computer icon; simple!

You can add and remove a few other icons that way as well.

---

### Post by matter2012 on 2010-03-29
THANK YOU it might have been me i like to play around with stuff and some times mess things up thanks again

---

### Post by mixim on 2011-10-22
WOuld just like to bump this in saying that, in GNOME 3 you can toggle individual desktop icons with gnome tweak tool or "advanced settings". It's located in the "Desktop" section.

---

### Post by sffvba[e0rt on 2011-10-22
Bump noted but not relevant to the thread in question (and thread closed due to necromancy).


404

---

