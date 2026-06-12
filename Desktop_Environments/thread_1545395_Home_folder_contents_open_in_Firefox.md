---
title: "Home folder contents open in Firefox"
date: 2010-08-03
forum: Desktop Environments
---

### Post by Frogs Hair on 2010-08-03
I used the places menu to open my documents and the folder opened in Firefox , I found that all personal folders would only open in FF. I thought it may be a Gnomenu problem and installed the default menu and the same thing happened.

The short cut from the AWN dock opens the file browser normally. I have done no configuration changes. I think I will do a fresh install unless someone has an idea what happened. the current installation of 10.04 has been great until today. I don't how long it has been this way because I use the dock all the time.

If you have any idea what caused this please let me know . Thanks !

---

### Post by Frogs Hair on 2010-08-04
Just finished reinstall and all is well .):P

---

### Post by mc4man on 2010-08-04
If it happens again - 
just r.click on any folder on your desktop, if you don't have one then create one, and go 'open with" -> 'other application' and pick 'folder handler'. That will set things straight.

What happened was somehow firefox was set as the  default folder handler - you'll notice that if r. clicking on a folder -> properties, that there is no 'open with' tab to change the default so how it happened is unclear.
(may be one of those random glitches.

There is also  a line in ~/.local/share/applications/mimeapps.list that can control this once it is created by opening a folder with anything but nautilus - 
inode/directory=
but nothing to concern yourself about atm.

---

### Post by Frogs Hair on 2010-08-04
> **mc4man said:**
> If it happens again - 
just r.click on any folder on your desktop, if you don't have one then create one, and go 'open with" -> 'other application' and pick 'folder handler'. That will set things straight.

What happened was somehow firefox was set as the  default folder handler - you'll notice that if r. clicking on a folder -> properties, that there is no 'open with' tab to change the default so how it happened is unclear.
(may be one of those random glitches.

There is also  a line in ~/.local/share/applications/mimeapps.list that can control this once it is created by opening a folder with anything but nautilus - 
inode/directory=
but nothing to concern yourself about atm.

Thanks , I had not used Firefox to open any programs and have no html. documents I attempted to change 
the open with settings , but it didn't work . When I right clicked  from the places menu it would open in Firefox.

---

