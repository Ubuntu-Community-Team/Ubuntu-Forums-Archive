---
title: "What config files store panel properties?"
date: 2012-07-03
forum: Desktop Environments
---

### Post by redss on 2012-07-03
Can anybody tell me what gnome configuration files in ubuntu (Lucid) store the shortcut properties in the top panel?  That information is not stored in the gconf repository.  (already checked the gconftool dump)

---

### Post by ajgreeny on 2012-07-03
Not sure, but look in ~/.config/dconf

---

### Post by cipherboy_loc on 2012-07-03
Check out ~/.gnome2?

---

### Post by kansasnoob on 2012-07-03
It would be very helpful if we knew exactly what you were trying to accomplish ;)

---

### Post by redss on 2012-07-03
Thanks for the replies. No luck here yet. OK here's my objective:   After booting a live CD of Lucid, I want to run a script that will change the command property of the firefox launcher icon in the panel. I cant find the default file that contains this information, although I've determined that manually changing the command property creates a ".desktop" file in ~/.gnome2/panel2.d/default/launchers/

So my question becomes where is this newly created desktop file referenced?

---

### Post by redss on 2012-07-03
But ultimately I'd just like to know where the default .desktop file is for the firefox icon in the panel (before a file is created under .gnome2/panel2.d/default/launchers)

---

### Post by cipherboy_loc on 2012-07-03
Check the /usr/share/applications directory. Should be a file called firefox.desktop.

---

### Post by redss on 2012-07-03
Ah, that works, thank you!

---

