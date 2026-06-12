---
title: "OAFIID:GNOME_MixerApplet trouble from .gtkrc-2.0"
date: 2009-06-21
forum: Desktop Environments
---

### Post by VOLKOV9 on 2009-06-21
I wanted my panels to have different color text than my window text, so I searched around these forums and found that I could make a file caled .gtkrc-2.0 and it could do exactly that.  However, upon rebooting, I no longer had the Human theme going on - everything that was normally that orange/tan had become blue, and everything looked slightly different.  This could be corrected by changing the theme to something else and back to Human.

Hours later, I rebooted again, and the same thing happend, except now, immediately after logging in, I got the error message:

```
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet"
```

and it asked me if I wanted to delete the applet.  I figured I was better off declining to do so.  Telling it to switch themes no longer elicits any response.

I've searched this forum and google and found people in similar predicaments.  Some are unresolved, some were resolved by reinstalling GDM, gnome-panel, and/or gnome-panel-data, and some were resolved by deleting files in the /tmp/.  No combination of these (or deleting the .gtkrc-2.0 file) has worked for me.

I would be very appreciative of any help.

---

### Post by VOLKOV9 on 2009-06-21
Sometimes when I boot up, all icons in nautilus (and desktop) are a piece of paper with a folded corner, and sometimes they are their proper icons.  I haven't rebooted enough times to be sure, but so far it seems to be every other time.  Weird.

---

### Post by VOLKOV9 on 2009-06-23
**bump**

---

