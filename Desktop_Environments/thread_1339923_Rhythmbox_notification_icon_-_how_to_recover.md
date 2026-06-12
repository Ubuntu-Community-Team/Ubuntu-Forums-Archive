---
title: "Rhythmbox notification icon - how to recover?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by east2idaho on 2009-11-28
I accidentally nuked the notification icon for rhythmbox and cannot figure out how to add it back.  In gconf-editor, my current settings for 
apps|rhythmbox|plugins|status-icons are:
  active             (checked)
  mouse-wheel-mode   0
  notification-mode  2
  status-icon-mode   3
  window-visible     (unchecked)

What I want is the default notification icon behavior, where after I launch rhythmbox closing the application window minimizes it to an icon in the notification task bar.  Hovering over this icon displays the title of the currently playing song.

What I have is that after I launch rhythmbox closing the application window makes the application disappear with no icon visible.

Any suggestions?

---

### Post by wilee-nilee on 2009-11-28
The control of the notification icon is in the plugins.

---

### Post by east2idaho on 2009-11-28
Sorry, I should have shown my current settings for Rhythmbox's 
Edit|Plugins|StatusIcon|Configure... menu.

The settings I currently have for this are:
Notifications:  Always shown
Status icon:    Owns the main window
Mouse wheel:    Change volume

Any suggestions for changing something there?

I am thinking that I have a Gnome configuration issue here not a Rhythmbox application configuration issue.  With my current settings, Rhythmbox properly disappears instead of shutting down when I close its application window.  I just don't get a notification icon appearing in Gnome's notification bar.

---

### Post by east2idaho on 2009-11-28
I got it figured out.  What had disappeared was not the notification icon for rhythmbox, but the Gnome's whole notification panel.  I added this back with a right click|Add to Panel|Notification Area selection, and everything was as expected.

---

