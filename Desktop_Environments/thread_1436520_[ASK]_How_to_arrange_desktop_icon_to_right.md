---
title: "[ASK] How to arrange desktop icon to right ?"
date: 2010-03-22
forum: Desktop Environments
---

### Post by m42h31 on 2010-03-22
Default Gnome desktop icon is arranged to left :
[IMG]http://img260.imageshack.us/img260/4343/leftq.png[/IMG]

How to automatically set desktop icons to right when mounting the hard drive or USB flash disk ? *(like MAC OSX do on their desktop)*

[IMG]http://img510.imageshack.us/img510/2913/rightu.png[/IMG]
i do this manually by dragging icon to right of desktop..

please advice me for best solution,
thanks..

---

### Post by quixote on 2010-03-23
Changing gnome defaults is always a royal pain.  I fight my way through gconf-editor when I'm trying to do that.  Start it by typing "gconf-editor" (without quotes) in a terminal (Applications > Accessories > Terminal).  (if it says it doesn't exist, it can be installed via synaptic.)

By the look of it, what you need is under apps > nautilus > desktop-metadata.  One of my entries, for instance, is bunch-of-gobbledygook@volume, and under that is an entry that says: ```
nautilus-icon-position   66,10 
``` I think that refers to the coordinates on the desktop where the icon is to appear.

What, exactly, you would have to enter, I don't know.  But at least that might give you some more precise search terms to try, such as "gconf-editor nautilus-icon-position" (enter them in the same search bar, but without quotes).

---

### Post by m42h31 on 2010-03-24
how about Right click on desktop then **Clean Up by Name** ?
icons go to left of desktop again.. i need they stay on right desktop..

thanks.. :)

---

