---
title: "software sources tab missing from main menu"
date: 2010-09-18
forum: Desktop Environments
---

### Post by macem29 on 2010-09-18
went to update the software sources and it's gone from System/Preferences/Main Menu/Administration

tried to add it back and I think I have the right file targeted (usr/bin/software-properties-gtk) but after
adding it I can't open it from the Main Menu without root, I used to be able to open this after passwording in,
any ideas to get it back properly in that main menu?

---

### Post by mc4man on 2010-09-18
The command for the menu item would be this
```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```

---

### Post by macem29 on 2010-09-18
thanks! I've been reading for awhile, don't know if I'd ever have found/figured that out, cheers mc4man

---

### Post by mc4man on 2010-09-18
I'm surprised it's not there ( in edit menus - assuming lucid

I'm using Maverick where it's no longer enabled by default in the menu but is visible in edit menus.

(by default in maverick software sources will be available in Ubuntu Software Center under the 'edit' tab

---

### Post by macem29 on 2010-09-18
sorry, yeah it's on a 10.04 NetBook Remix....your command worked, thanks again...and seeing as you brought it up, the option is available under the edit tab in Ubuntu Software Center, didn't know to look there

---

### Post by garvinrick4 on 2010-09-19
If anyone needs to get to it right off the bat to configure system it is in /etc/apt/sources.list
and right click and open with Software Sources. Not something that really needed to be said but just in case it helps anyone when it is not in System/Application/Software Sources.

---

### Post by garvinrick4 on 2010-09-19
> **mc4man said:**
> I'm surprised it's not there ( in edit menus - assuming lucid

I'm using Maverick where it's no longer enabled by default in the menu but is visible in edit menus.

(by default in maverick software sources will be available in Ubuntu Software Center under the 'edit' tab Never seen that in edit menu's just assumed that it would be a properties in that location.

---

