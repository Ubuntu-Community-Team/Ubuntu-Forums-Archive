---
title: "Lost track of tracker"
date: 2009-05-15
forum: Desktop Environments
---

### Post by su-37 on 2009-05-15
Hey, ive suffered from the bug where tracker says the index is xorrupted. After deciding i was going to wait for the fix i got rid of the tracker from the notification area. Now id like to knoe how to put it back regardless of the bug. Can anyone help? :D

---

### Post by adrianx on 2009-05-16
This is probably not the only way, but it worked for me. :)
```
gedit ~/.config/tracker/tracker-applet.cfg
```
Change AutoHideIcon=[COLOR=Navy]true[/COLOR] to AutoHideIcon=[COLOR=Navy]false
[COLOR=Black]Save and exit
Log out and back in
[/COLOR]
[/COLOR]

---

### Post by su-37 on 2009-05-16
Thanks for the tip. But unfortunately it already said auto-hide false. Any other ideas?

---

