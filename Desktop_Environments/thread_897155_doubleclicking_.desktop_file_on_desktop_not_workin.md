---
title: "doubleclicking .desktop file on desktop not working"
date: 2008-08-21
forum: Desktop Environments
---

### Post by jeli on 2008-08-21
Instead, I get a "There is no application installed for this file type" message.  Should there be an application associated with the .desktop extension?
Thanks

---

### Post by Vadi on 2008-08-21
Can you please rename the .desktop to a .txt and attach it here?

---

### Post by pauper on 2008-08-21
Try opening that file in gedit via File-Open.

---

### Post by jeli on 2008-08-22
I attached a simple Launcher shortcut I created for gedit.  The problem seems greater than that.  Even doubleclicking on a text file in the File Browser gives me the same warning, "There is no application installed for this file type"

---

### Post by pauper on 2008-08-22
It works for me (saved as gedit.desktop): double-click or right-click--Open
brings up gedit.

---

### Post by jeli on 2008-08-22
Yes, but why isn't it working for me.  Something may be wrong with my nautilus.

---

### Post by pauper on 2008-08-22
Try creating any other launcher on Desktop via right-click--Create Launcher...

---

### Post by jeli on 2008-09-29
turns out it was related to mime types.  I noticed when I viewed the properties of all file in nautilus, they were set to text/plain.  I did a update-mime-database and that fixed everything

---

