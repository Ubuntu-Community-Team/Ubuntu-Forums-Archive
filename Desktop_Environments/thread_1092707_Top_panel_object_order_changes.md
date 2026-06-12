---
title: "Top panel object order changes"
date: 2009-03-10
forum: Desktop Environments
---

### Post by Darvon on 2009-03-10
Hey!

I have that nasty problem with the top panel in gnome: if the panel is not expanded, the objects on the panel change their position after reboot.
It seems that it happens only in case the panel isn't expanded.

I've found a nice way to fix this with some commands ( [http://ubuntuforums.org/showthread.php?t=342775](http://ubuntuforums.org/showthread.php?t=342775) ), too bad that it doesn't work: I save the settings into a file, restart, but after loading the settings, the panel is just the same. The saved file for the settings could not change, so I don't know what else I could try...

---

### Post by m_duck on 2009-03-11
Hey,

I'm not positive it will work but if you arrange all the items as you want on the panel, then right click each of them and click "Lock to panel" or similar. That should ensure they don't move around after a reboot.

---

### Post by UbuntuNerd on 2009-03-11
> **m_duck said:**
> Hey,

I'm not positive it will work but if you arrange all the items as you want on the panel, then right click each of them and click "Lock to panel" or similar. That should ensure they don't move around after a reboot.

that's what you need to do lock all the icons in place then they won't move anymore

---

### Post by Darvon on 2009-03-11
Well, thanks for the answers, but that was the first thing I tried. Honestly, it would be just too easy :)
I not only locked the objects on the panel, I even locked the panel itself in the gconf-editor
The problem seems to be in loading the panel... somehow :-k

---

### Post by Ryuki_NdranC on 2009-05-21
> **Darvon said:**
> Well, thanks for the answers, but that was the first thing I tried. Honestly, it would be just too easy :)
I not only locked the objects on the panel, I even locked the panel itself in the gconf-editor
The problem seems to be in loading the panel... somehow :-k
I'm resurrecting this because i have the same problem in jaunty, each time i relog/reboot all the objects in the panel (locked or not) move around in the order i think they are loaded. I'm gonna keep searching for a fix, but any of you have found anything?

---

### Post by Ryuki_NdranC on 2009-05-21
lawl i think i just found a workaround. Easy enough just open the configuration editor and app>panel>global and activate the lockdown option. It's kinda troublesome because to be able to chage something from the panel agian, you need to keep using the config editor.

---

