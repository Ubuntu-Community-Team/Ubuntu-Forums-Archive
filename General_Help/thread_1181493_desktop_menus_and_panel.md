---
title: "desktop menus and panel"
date: 2009-06-08
forum: General Help
---

### Post by almagr on 2009-06-08
On my desktop no panels or menus are loading.  After reading some other posts.  i typed gnome-panel into terminal.  It brings this response.


** (gnome-panel:5436): DEBUG: Adding applet 0.
** (gnome-panel:5436): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:5436): DEBUG: Adding applet 1.
** (gnome-panel:5436): DEBUG: Adding applet 2.
** (gnome-panel:5436): DEBUG: Adding applet 3.
** (gnome-panel:5436): DEBUG: Adding applet 4.
** (gnome-panel:5436): DEBUG: Adding applet 5.
** (gnome-panel:5436): DEBUG: Adding applet 6.
** (gnome-panel:5436): DEBUG: Adding applet 7.
** (gnome-panel:5436): DEBUG: Adding applet 8.

(gnome-panel:5436): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:5436): DEBUG: Adding applet 9.
** (gnome-panel:5436): DEBUG: Adding applet 10.
** (gnome-panel:5436): DEBUG: Adding applet 11.
** (gnome-panel:5436): DEBUG: Adding applet 12.

The panels and menus bar appear as I set them, but when I go to close terminal, its says there are processes running.  Closing terminal then removes all menus and panels.

HELP PLEASE

---

### Post by Legace on 2009-06-08
Press ALT + F2, then type in gnome-panel, and press Run :)

---

### Post by almagr on 2009-06-08
as i said this brings back the menus and panels but they dissapear when I close terminal

---

### Post by Legace on 2009-06-08
> **almagr said:**
> as i said this brings back the menus and panels but they dissapear when I close terminal

Then go to System -> Preferences -> Startup Applications and add an entry for gnome-panel (reboot to see effect).

Also, you might want to try (in Terminal):
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by almagr on 2009-06-08
I tried  System -> Preferences -> Startup Applications and add an entry for gnome-panel (reboot to see effect).  
 The menus etc loaded fine.  Will i need to carry out the second of your ideas?   Cheers
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by Legace on 2009-06-08
> **almagr said:**
> I tried  System -> Preferences -> Startup Applications and add an entry for gnome-panel (reboot to see effect).  
 The menus etc loaded fine.  Will i need to carry out the second of your ideas?

No, you won't :)

---

