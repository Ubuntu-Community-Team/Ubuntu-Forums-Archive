---
title: "How to drag app icon from menu bar to desktop"
date: 2012-05-22
forum: Desktop Environments
---

### Post by RogerDavis on 2012-05-22
How can I drag a menu bar from the bar at the side of the screen to the desktop without losing it in the launcher?  I can't do it with either mouse key, with or without any modifier key (ctl, alt, etc.)

---

### Post by adit on 2012-05-22
Do you mean dragging an icon from the unity launcher and create a shortcut on the Desktop?

---

### Post by RogerDavis on 2012-05-22
Yes, or any other easy (drag and drop) way to get it onto the desktop.

---

### Post by wilee-nilee on 2012-05-22
Make a launcher.
```
sudo apt-get install --no-install-recommends gnome-panel
```Then.

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```So your command is usually in the /usr/bin  so navigate there, the icon usually appears if you type the name of the app in the top line

---

### Post by MG&amp;TL on 2012-05-22
Good answer, just a small typo:

/user/bin -> /usr/bin 

;)

---

### Post by wilee-nilee on 2012-05-22
> **MG&TL said:**
> Good answer, just a small typo:

/user/bin -> /usr/bin 

;)

Doh, thanks :)

---

### Post by RogerDavis on 2012-05-22
OK, this confuses me.

Does the "sudo apt-get install", and "gnome-desktop-item-edit ~/Desktop/" reinstall the app?  

If so, I don't need to do that.  

What's going on is that I just upgraded to 12.04, and the Seamonkey icon is a blank page.  I don't see any way to change the icon, so I was just going to create a new ICON by making a copy of the one on the launcher, which is correct.

Thanks!

---

