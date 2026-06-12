---
title: "Gnome crash after resizing panel"
date: 2006-12-28
forum: Desktop Environments
---

### Post by sicofante on 2006-12-28
Help!!!!

I was playing around with the panel's properties. I was increasing the size of the upper panel. When it reached something like 50, Gnome crashed and it will crash every time I log in now. I logged in to a terminal trying to change the panel's size back manually, but I can't find where Gnome saves these values.

Thanks in advance for any help.

---

### Post by Gen2ly on 2007-01-02
lol, got the same thing.  tried to have some fun, oops.  X11 crashes every time now i boot.

---

### Post by ComplexNumber on 2007-01-02
> **sicofante said:**
> Help!!!!

I was playing around with the panel's properties. I was increasing the size of the upper panel. When it reached something like 50, Gnome crashed and it will crash every time I log in now. I logged in to a terminal trying to change the panel's size back manually, but I can't find where Gnome saves these values.

Thanks in advance for any help.
it saves them in .gconf. fire up gconf-editor and type in "panel" into search. scroll down until you see /apps/panel/toplevels/top_panel_screen0, and you will see size as being 50. that is reflected in the xml files(because the settings are hold in xml format throughout gnome) in .gconf direectory.

---

### Post by Gen2ly on 2007-01-02
thanks for the info ComplexNumber.  I did failsafe-terminal in sessions and just rm -r .gconf.  I imagine i deleted other info but I just installed.  This bug crashed the whole X11, not just the panel... sheesh.

---

### Post by sicofante on 2007-01-03
Sorry I didn't come back earlier. I did solve this issue.

It wasn't possible to enter failsafe mode so I had to deal with a command line session. After much googling (in Windows...) and a lot of luck, I was able to find the file where the changed size was. It's this:

~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml

I edited that file and figured out where the size was, changed it back to 24 and Gnome worked again.

I guess I should file a bug about this behaviour.

---

